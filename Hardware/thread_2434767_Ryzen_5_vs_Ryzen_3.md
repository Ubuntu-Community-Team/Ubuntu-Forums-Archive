---
title: "Ryzen 5 vs Ryzen 3"
date: 2020-01-10
forum: Hardware
---

### Post by daniell59 on 2020-01-10
I am very slowly gathering my parts for my next computer build. I am a non gamer. I am trying to decide between Ryzen 5 3400G and Ryzen 3 3200G. My main concern is with Ubuntu compatibility. Would one be more compatible than the other? Also, Would I be better off getting a CPU without built in graphics and buying an inexpensive video card?

Thanks

---

### Post by CatKiller on 2020-01-10
They're as compatible as each other, since they're the same generation. In either case you'll want to be using software that's as new as possible, since the parts themselves are new. If you don't get round to doing the build till April, 20.04, otherwise 19.10 upgraded to 20.04 in April. As a non-gamer, and someone that's not doing GPGPU, integrated graphics will be fine.

---

### Post by TheFu on 2020-01-10
CatKiller nailed it. 100% agree.

OTOH, if you have an old GPU, you can get much more Ryzen CPU if you go with a pure CPU that doesn't have iGPU included.  Check out the passmarks and the prices and the $/watt.  Only you can decide. Get informed with as much data as possible for your local purchase possibilities.  I happen to live near-ish a nationwide computer store that likes to use GPU+Motherboard combinations as loss-leaders to get people into the store.

A year ago, I decided that using a non-iGPU Ryzen was better for my needs because it provided about 30% more processing power for the same price and I already had a GPU to reuse and I run 16.04 with no interest to use something newer for now.

YMMV.

---

### Post by daniell59 on 2020-01-10
> **TheFu said:**
> CatKiller nailed it. 100% agree.

OTOH, if you have an old GPU, you can get much more Ryzen CPU if you go with a pure CPU that doesn't have iGPU included.  Check out the passmarks and the prices and the $/watt.  Only you can decide. Get informed with as much data as possible for your local purchase possibilities.  I happen to live near-ish a nationwide computer store that likes to use GPU+Motherboard combinations as loss-leaders to get people into the store.

A year ago, I decided that using a non-iGPU Ryzen was better for my needs because it provided about 30% more processing power for the same price and I already had a GPU to reuse and I run 16.04 with no interest to use something newer for now.

YMMV.

Thanks, you gave me something to think about. Since I wont be gaming, can you recommend a GPU? I am planning on buying the MSI B450 Tomahawk motherboard. The only thing that i bought so far is the case.

---

### Post by Yellow Pasque on 2020-01-10
> Since I wont be gaming, can you recommend a GPU?

I'd recommend an Nvidia GT 1030 as long as you're not bothered by the proprietary driver. You can get a passively-cooled version if you want. I have a Ryzen 2400G with an Nvidia GTX950 on a B450 mobo. It's a good rig, but I'm probably going to upgrade to a Ryzen 3600(X) because the performance/Watt is a lot better with the 3600 and it comes with a much better heatsink. I wish AMD offered something similar to the GT 1030 in terms of price/performance/thermals, but alas...

---

### Post by daniell59 on 2020-01-10
The bottom line. Will I get better Linux compatibility with a separate video card?

---

### Post by TheFu on 2020-01-10
I cannot really recommend any GPUs. I had some old GPUs laying around. 

My "new" Ryzen system was really just 3 new things - CPU, RAM, Motherboard. I reused everything else.  I don't "do" 100% new systems.  I replace only the parts required to be replaced.  For example, I'm using the same case from 1999 in one system.  Nothing wrong with it, so why spend even $10 more?  I would have preferred to not by any new RAM too, but Ryzen is DDR4 and all my other systems are DDR3 or DDR2, so there wasn't any choice.  BTW, RAM is 50% less today than when I bought it 13 months ago.

The flaw in my upgrade methods is that I have 3 older "CPU+MB+RAM" systems here that can't be sold to non-tech people.

---

### Post by TheFu on 2020-01-10
> **daniell59 said:**
> The bottom line. Will I get better Linux compatibility with a separate video card?

It depends on the video card.  If you get a last-generation GPU, only install LTS, then yes. IMHO.  If you need the latest release and hottest, newest GPU, then no.

I have a fanless one of these:
```
$ lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'
08:00.0 VGA compatible controller: NVIDIA Corporation GP108 [**GeForce GT 1030**] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: eVga.com. Corp. Device 6336
        Flags: bus master, fast devsel, latency 0, IRQ 88
        Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at e000 [size=128]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
```
It isn't really cheap in my book at $65.   Be very careful with the 1030 models.  Some have DDR4 RAM and others have DDR5 which provides a huge performance increase.  [https://www.forbes.com/sites/jasonevangelho/2018/07/09/buyer-beware-nvidias-geforce-gt-1030-is-a-grossly-misleading-gpu/](https://www.forbes.com/sites/jasonevangelho/2018/07/09/buyer-beware-nvidias-geforce-gt-1030-is-a-grossly-misleading-gpu/)  and [https://www.gamersnexus.net/hwreviews/3330-gt-1030-ddr4-vs-gt-1030-gddr5-benchmark-worst-graphics-card-2018](https://www.gamersnexus.net/hwreviews/3330-gt-1030-ddr4-vs-gt-1030-gddr5-benchmark-worst-graphics-card-2018) have more details.

If I were looking today, I'd look more at AMD GPUs. They are better at supporting F/LOSS drivers. 

Nvidia isn't very nice towards F/LOSS according to Linus T.  Just google this "nvidia linus" to see what he thinks about them.  [https://www.phoronix.com/scan.php?page=news_item&px=MTEyMTc](https://www.phoronix.com/scan.php?page=news_item&px=MTEyMTc) has a summary.

---

### Post by daniell59 on 2020-01-10
> **TheFu said:**
> I cannot really recommend any GPUs. I had some old GPUs laying around. 

My "new" Ryzen system was really just 3 new things - CPU, RAM, Motherboard. I reused everything else.  I don't "do" 100% new systems.  I replace only the parts required to be replaced.  For example, I'm using the same case from 1999 in one system.  Nothing wrong with it, so why spend even $10 more?  I would have preferred to not by any new RAM too, but Ryzen is DDR4 and all my other systems are DDR3 or DDR2, so there wasn't any choice.  BTW, RAM is 50% less today than when I bought it 13 months ago.

The flaw in my upgrade methods is that I have 3 older "CPU+MB+RAM" systems here that can't be sold to non-tech people.

I can appreciate what you have said. I have a 10 + year  Lian Li case. I was going to use it, but got seduced by a great sale on Amazon. The advantage of the new case is bigger fans, USB 3.0 and it is on the top rather than on the bottom as is the case with the Lian Li case. In respect to the Lian Li case,  feel like I abandoned an old sick dog.

---

