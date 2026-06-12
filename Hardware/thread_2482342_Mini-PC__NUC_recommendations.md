---
title: "Mini-PC / NUC recommendations?"
date: 2022-12-29
forum: Hardware
---

### Post by mark-chandler on 2022-12-29
Looking to replace my four-year-old Compulab fitlet2 with something newer/faster. Any recommendations for sub-$500 mini-PCs or NUCs that can run Ubuntu 22.x with a "vanilla" install?

---

### Post by TheFu on 2022-12-29
NUCs seem to cost $100+ more than the components inside would demand, have limited connectivity and nearly zero flexibility.   If you are going for "new", I'd look for ITX systems with a PicoPSU brick to avoid the jet-engine fan noise that most industrial computers of that type use.  ITX system don't have a "small" tax like NUCs do.

For a "boot" box size, Shuttle makes some good systems that aren't too overpriced, but still 50%+ smaller than a mid-tower. I ran a Core i7 Shuttle computer with a Pro-Nvidia CAD GPU for years. Best of all, the entire computer new was less than a mid-range GPU was last year, under $500.

If you are going for "new to you" systems, check the off-lease IBM/Lenovo/Dell options for their information worker/call center computers. These are usually about half a pizza box and maybe a little thicker, but there are some excellent bargains.  My local MicroCenter always has 50+ of these or there's eBay, which usually has 1000+ lots.  Just be certain to know the components and get 

a) a CPU with sufficient passmark benchmark scores (I'd say 8,000+ would be minimal).  A few weeks ago, I picked up a new Ryzen 5600G APU for $119. That has just under 20,000 passmarks for reference.  I believe that APU is $105 now.  Don't get ripped off.  My 2017 Core i5 laptop came with a 6800 passmark 8th gen CPU for $305.

b) Has a GPU that does what you need.

c) Has at least 1 intel NIC 

d) Has an NVMe 250GB+ SSD

e) Has at least 8GB of RAM. More is better, but 16GB is usually enough.

Only problems that I know about are the typical proprietary PSU connections and that if you plan to add a GPU, you'll have to avoid full-height and full length GPUs. Also, the onboard PSU might be 250W, which is fine for a desktop with an SSD, but not good if you hang lots of USB devices or a hefty GPU is used.  And there are typically only 2 RAM slots, so either 16G or 32G would be the max RAM which is fine for almost everyone running a Linux desktop, but you haven't really spelled out the intended workloads.

Small has problems and costs are premium.  If you want flexibility for upgrades and addons, stick with a microATX, unless you need more than 3 PCIe slots. Then a full ATX is needed.  I suspect those extra cards aren't in your plans.

The only mini-PC that I have is an APU2 with 4GB that runs my router.  The AMD-64 Cores aren't the fastest, but thanks to very well supported intel NICs, it can move some data. It uses 12W, supports 2 USB3 ports, 1 SATA, 1 SDHC and is completely silent.  Alas, it doesn't have any GPU, so if you plan to run a desktop, you'll need to setup remote access into the system (or use a virtual machine) to connect to the desktop.

I expect all my efforts to convince you to avoid the NUC will fail.  Sigh.  Watch out for really old, slow, computers being sold.  100%, always, every time, check the passmark score for each CPU.  A core i5 from 2013 is slower than a Core i3 from 2015.  Basically, every 2 yrs the lower model of CPU overtakes the next level up for performance. I wouldn't consider any Intel CPU that isn't 8th gen or later.  

[https://www.ebay.com/itm/293526962748](https://www.ebay.com/itm/293526962748) is a Core i3 - 3rd gen for $99.

[https://www.ebay.com/p/7051078914?iid=185708914608](https://www.ebay.com/p/7051078914?iid=185708914608) is at auction for $325. Below $350 and it is a steal. Dell OptiPlex 3090 (Intel Core i5-10500T, 8 GB RAM, 256 GB SSD) Micro BTX PC Desktop - Black (TG95F)  That's 10,200 passmarks.

I'm seeing 3rd gen Core i5s and 7th gen Core i5s for the same prices.  Be careful out there.  The 7th generation should be over 2x faster, which is what you want if you can't find a newer generation.  The current gen is 12, btw.  They are good on performance and using less power, which means the entire system will be cooler, so fans don't need to be loud.  Everything needs to fix just right for a quiet, cool, fast, system.  Folding components onto each other isn't good for cooling. That's wear NUCs tend to fail.

I like Dell systems for compatibility.  Lenovo has a good history in that regard too.  

Seems a little strange to see a 3090 for that price.  3090 is an old IBM mainframe model number. [https://en.wikipedia.org/wiki/IBM_3090](https://en.wikipedia.org/wiki/IBM_3090) Not related to this thread at all, just funny to people like me.

---

### Post by mark-chandler on 2022-12-30
Thanks for the extremely detailed reply. I'm now looking at reconditioned/refurbed Lenovo and Dell SFF boxes. WiFi and Bluetooth are must-haves. My main use cases are streaming audio and video (Spotify, BBC, ITV, etc). Current setup is Celeron CPU J3455 @ 1.50GHz × 4 (8GB RAM/128GB SSD).

---

### Post by TheFu on 2022-12-30
[https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+J3455+%40+1.50GHz](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+J3455+%40+1.50GHz) shows a passmark of 2200. Meh.
If you want video playback, you'll need a sufficient GPU with good drivers that Linux likes which can handle mpeg2, h.264 and h.265 decoding in hardware.  Nearly any video player/computer made in the last 10 yrs will do the first 2, but h.265/vp9 video is more work and I don't know which GPU level is needed.

I use raspberry pis v3 & v2 running OSMC for 1080p playback at home, streamed from a Jellyfin media server. 1080p mpeg2 is a struggle for both, but h.264 is easily handles.  If you want 4K video playback, a Pi v4 is needed and probably a 3-4 yr old intel CPU can do it. I wouldn't be on anything older.  Our roku3 pukes if the stream provided is h.265/vp9 in hidef resolutions.  At US-DVD resolutions, most CPUs, even $150 ARM cell phones and 2017 $50 amazon tablets work with h.265 encoded media.

In short, the video encoding matters along with the resolution.

Audio isn't any issue for most systems, unless you are really, really, picky about the audio playback.  I have old, old, audio systems (mono through 5.1 THX) and can always get one of the audio tracks to play.  DTS, DD, PCM, vorbis, AAC all work.  DD+ can cause problems, which is what most streaming services switched to over 3+ yrs ago, perhaps 4-5.  I just remember when they did I had to change the roku to output stereo, not DD+ to my old audio system. No more 5.1 through my old Roku.  Perhaps a newer version would handle it. IDK.  Anyway, audio playback is seldom an issue for most people.

If you want a good GPU, good audio, good decoding that is Linux friendly, I'd look at one of the Ryzen models ending with a "G".  I have 2 Ryzen 5600G systems and the built-in GPU is faster and better supported, than an nvidia 1030 DDR5 discrete GPU that was running $130 last year.  Consider that a Ryzen 5600G without any sales is $125 these days and doesn't need a separate GPU for excellent performance (non-gaming/non-video editing).  I'm a Ryzen fan. I was running Intel CPUs since 2005-ish, but Ryzen 2xxx and later won my business.

---

### Post by mark-chandler on 2023-01-09
Apologies for the tardy reply. I picked up an off-lease Lenovo ThinkCentre M93p (i7, 16GB RAM, 512GB SSD) and installed 22.04.1 LTS over Windows 10. Zero issues with the installation and setup. Not the fastest box around, but works well for streaming music and video.

---

### Post by TheFu on 2023-01-09
> **mark-chandler said:**
> Apologies for the tardy reply. I picked up an off-lease Lenovo ThinkCentre M93p (i7, 16GB RAM, 512GB SSD) and installed 22.04.1 LTS over Windows 10. Zero issues with the installation and setup. Not the fastest box around, but works well for streaming music and video.

Nice.

I'm seeing a bunch of Core i5-4xxx models for $30-$150.  6700 passmarks [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i7-4770S+%40+3.10GHz&id=1884](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i7-4770S+%40+3.10GHz&id=1884) Nice.   I might need to upgrade my opnSense router. ;)
I like to have the router less than 30W and fanless with 4+ ethernet ports.

---

