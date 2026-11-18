# Cheap GPU Server: What One RTX 4090 Costs Per Month, What Eight Cost, and How to Avoid Paying Twice in Month One (Full Plan Table)

A single RTX 4090 server at LightLayer lists at **$365 per month**: one 24 GB card, 16 vCPU, 32 GB of RAM, 250 GB of SSD, billed monthly. The eight-card version of the same line lists at **$2,920 per month** with 64 vCPU, 128 GB of RAM and 1,000 GB of SSD, which works out to exactly $365 per card.

That is the lowest monthly price for a 24 GB card in this comparison, and about a third of what a single 96 GB professional card costs per month elsewhere. Whether it is cheap for your job depends on two things the plan table won't tell you: how much VRAM the work actually touches, and what the first invoice looks like once setup fees and term discounts are applied. Both are below.

> **Short answer for most readers:** take the 1× RTX 4090 plan at $365/month. It covers rendering, streaming, emulator farms and inference of models that fit in 24 GB, and it is the only tier here where picking wrong costs you one month instead of a year. The 8-card box at $2,920/month only makes sense when you already know one card is the bottleneck.
>
> 👉 [Check the 1× RTX 4090 plan and the current monthly price](https://account.lightlayer.net/?affid=74)

## LightLayer's GPU plans, side by side

| Plan | GPU / VRAM | CPU · RAM · Storage | Price | Billing | Order |
| --- | --- | --- | --- | --- | --- |
| VGPU-1*RTX4090 | 1× RTX 4090, 24 GB | 16 vCPU · 32 GB · 250 GB SSD | **$365/mo** | Monthly | [Order the single-card plan](https://account.lightlayer.net/?affid=74) |
| VGPU-8*RTX4090 | 8× RTX 4090, 192 GB total | 64 vCPU · 128 GB · 1,000 GB SSD | **$2,920/mo** | Monthly | [Order the 8-card plan](https://account.lightlayer.net/?affid=74) |

Three things about this table matter more than the numbers in it.

The eight-card box carries no volume discount. $2,920 divided by eight is $365, the same as buying one. Scaling up buys capacity, not a better rate per card, so the decision is purely "how many cards does the job need", never "the bigger box is cheaper per unit".

Both configurations are listed with monthly billing. There is no hourly meter to watch, which is the whole point of a flat-price GPU server, and also the reason you should not rent eight cards for a two-week experiment.

Stock on GPU configurations moves. At the time of writing both were listed as available; a week later one of them may not be, and multi-GPU builds beyond the eight-card box are quoted per order rather than published.

## The rest of the catalogue starts at $4/month

Worth knowing before you spend $365, because a fair number of people searching for a cheap GPU server are running something a CPU handles fine.

| Plan | CPU · RAM · Storage | Bandwidth | Price | Billing |
| --- | --- | --- | --- | --- |
| Startup | 1 core · 1 GB · 50 GB SSD | 100 Mbps unlimited | $4.00/mo | Monthly |
| Pay As You Go | 2+ cores · 2 GB+ · scalable | 200 Mbps+ | from $5.60/mo | Monthly |
| Business | 32 cores · 32 GB · scalable | 200 Mbps unlimited | $53.60/mo | Monthly |

Annual pricing on the entry configuration runs $24.99/year in Manila and Taiwan (about $2.08/month), $29.99/year in Los Angeles on the Global route, $39.99/year on Standard and $49.99/year on Premium, which uses the CN2/CMIN2 China-facing routes. The Premium routes cost more because the transit does; if your users are not in Asia-Pacific, the cheaper route is the correct one.

The gap between $4 and $365 is 91×. If your workload is a web app, a scraper, a build server or a database, the GPU line is not for you at any discount.

## What $365, $1,199 and $3,250 actually buy

Three price points show up repeatedly when you compare GPU servers by the month, and they buy three different machines.

**$365, LightLayer, 1× RTX 4090.** A consumer card with 24 GB and 16,384 CUDA cores, paired with a 16 vCPU server. This is the tier for people whose work fits on one GPU: 30-plus Android emulator instances, 4K game and animation rendering (a 4090 scores around 11,662 in Blender), dual NVENC encoders for streaming and recording at once, and inference of models small enough to sit in 24 GB.

**$1,199 (€999 / £969), Contabo, 1× RTX PRO 6000.** A professional Blackwell card with 96 GB of GDDR7, 24,064 CUDA cores, 120 TFLOPS FP32 and roughly 1.8 TB/s of memory bandwidth, attached to 18 vCPU, 96 GB of RAM and 900 GB of NVMe. Available in Europe and US Central, Ubuntu 24.04 with CUDA by default. The 96 GB is the reason to buy it: it holds a 70-billion-parameter model on a single card, and FP4 support lets you serve longer contexts at lower precision without splitting the model across machines. Contabo describes the launch as a limited run and states plainly that this is not hardware for large-scale multi-node training.

**$3,250 plus a $3,250 setup fee, IONOS, IP4-60.** The same RTX PRO 6000, in Server Edition form, inside a dual Xeon 6517P machine with 256 GB of DDR5 and 3.2 TB of NVMe. You are paying for the platform around the card as much as the card.

Per gigabyte of VRAM, the ranking is not what the sticker prices suggest:

| Machine | Monthly | VRAM | Cost per GB of VRAM |
| --- | --- | --- | --- |
| LightLayer 1× RTX 4090 | $365 | 24 GB | **$15.21** |
| Contabo RTX PRO 6000 | $1,199 | 96 GB | **$12.49** |
| IONOS IP4-60 | $3,250 | 96 GB | $33.85 |
| IONOS AP2-10 (A10) | $975 | 24 GB | $40.63 |
| IONOS AP1-10 (T4) | $767 | 16 GB | $47.94 |

VRAM per dollar is a crude metric, since a 4090 and a T4 are not interchangeable for any real workload, but it answers the "cheap" question honestly. The 4090 wins on entry price. The 96 GB Contabo card wins on capacity per dollar, by a wide margin over the other 96 GB option. IONOS's cheaper tiers are the most expensive VRAM in the table, and their value sits in the 128 GB of ECC memory and RAID 1 storage wrapped around an older card.

## The first-month bill is where cheap gets decided

IONOS charges a setup fee equal to one month's rent on every GPU tier. Not a token activation charge, the full monthly price again:

| Machine | Monthly | Setup | First invoice | 12-month total |
| --- | --- | --- | --- | --- |
| LightLayer 1× RTX 4090 | $365 | none shown | **$365** | **$4,380** |
| LightLayer 8× RTX 4090 | $2,920 | none shown | **$2,920** | **$35,040** |
| Contabo RTX PRO 6000, 12-month term | €849.15 effective | none stated | €849.15 | €10,189.80 |
| IONOS AP1-10 (T4) | $767 | $767 | $1,534 | $9,971 |
| IONOS AP2-10 (A10) | $975 | $975 | $1,950 | $12,675 |
| IONOS IP3-10 (Flex 170) | $1,027 | $1,027 | $2,054 | $13,351 |
| IONOS IP4-60 (RTX PRO 6000) | $3,250 | $3,250 | $6,500 | $42,250 |

The setup fee adds about 8% to a year of service, which is survivable. The problem is the first invoice arriving at double the number you budgeted for, on a machine you may only keep for a quarter. Two 96 GB cards that look like a $2,050 gap per month are a $5,300 gap in month one.

Contabo's term discounts work the other way. 15% off on a 12-month commitment brings €999 to €849.15 per month, or €10,189.80 for the year. Twenty percent off on 24 months takes it to €799.20 per month and €19,180.80 across two years, at the cost of locking in a card generation that will look old before the contract ends.

LightLayer's GPU listings show monthly billing with no setup fee in the listing. The annual discounts in the catalogue apply to VPS plans, not to the GPU line.

CloudClusters sits in the same consumer-card category as the 4090 box but publishes prices only on request, so it cannot be slotted into this table. Select models there carry a one-day free trial, subject to approval and stock. If you want to test a card before committing a month, that trial is the only low-risk option among the providers compared here.

👉 [Compare the 1× and 8× RTX 4090 plans and their monthly rates](https://account.lightlayer.net/?affid=74)

## Limits that never appear in the price

**Contabo's 96 GB card is a limited run, in two regions.** Europe and US Central only, with expansion tied to demand. If your latency budget points at Asia or South America, this is the wrong machine regardless of price.

**Contabo also rules out the workload most people assume they need.** Their own wording is that large-scale, multi-node training is a different class of infrastructure, and that H100 or A100 systems with NVLink are the right tool. A single 96 GB card does inference, fine-tuning and LoRA well; it does not become a training cluster.

**CloudClusters ships Windows Server 2022 Standard Evaluation, and it expires.** 180 days after deployment the system stops running. A genuine licence has to be bought at least ten days before that date. Budget for it, or run Linux.

**Cherry Servers quotes delivery in hours, not minutes.** Up to 24 hours generally, 24 to 72 hours depending on region, with hourly, monthly and yearly billing and 100 TB of free traffic per month. Fine for a planned deployment, wrong for an emergency.

**OVHcloud prices move with term length and location**, which the product page states without publishing a table. Get a quote for the exact region before comparing it to anything here.

For LightLayer, confirm two things during checkout rather than assuming: which locations carry the GPU configuration you picked, and the delivery window for that specific build. Multi-GPU orders above eight cards go through a quote.

## Which card fits which job

**Rendering, streaming, emulator farms, game servers.** One RTX 4090 at $365/month is the right buy. These workloads scale with encoder count and CUDA cores, not with VRAM past 24 GB, and consumer cards handle them at a fraction of enterprise pricing.

**Inference of a model that fits in 24 GB.** Same answer. One card, monthly, cancel when the project ends.

**A 70B model on a single card, or long-context serving.** 24 GB will not hold it at any usable precision. You need the 96 GB class, and the Contabo machine at $1,199 is the cheapest verified way to get there, with the IONOS IP4-60 at $3,250 as the option when you also want dual Xeon CPUs, 256 GB of RAM and RAID storage in the same box.

**Multi-node training.** None of the machines in this article. You want H100 or A100 nodes with NVLink, and the pricing conversation starts somewhere else entirely.

**Not actually a GPU job.** The $4 Startup VPS, or the $5.60 Pay As You Go plan if you need to dial cores up and down.

Two checks before you pay: the monthly price versus the annual price on the exact configuration you selected, and whether a setup fee applies on the first invoice. A $365 machine and a $767 machine can both be the cheap option; a $767 machine with a $767 setup fee on a three-month project is not.

👉 [Start with the single RTX 4090 plan at $365/month](https://account.lightlayer.net/?affid=74)
