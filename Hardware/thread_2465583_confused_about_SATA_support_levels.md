---
title: "confused about SATA support levels"
date: 2021-08-05
forum: Hardware
---

### Post by JamButty on 2021-08-05
Putting in a second HDD into my desktop and I get what seems conflicting information about which SATA level my mobo supports (I, II or III - 1.5 Gbps/3 Gbps/6 Gbps).
[HTML]$ dmesg | grep SATA
[    0.541970] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x11 impl SATA mode
[    0.553100] ata1: SATA max UDMA/133 abar m2048@0xf7e1a000 port 0xf7e1a100 irq 32
[    0.553106] ata5: SATA max UDMA/133 abar m2048@0xf7e1a000 port 0xf7e1a300 irq 32
[    0.868090] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.868132] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[/HTML]
Do the "UDMA" listings refer to ODD slots and "link up" listings to the HDD slots? It seems odd that a mobo would have various levels of support for different SATA slots (one is 6, one is 1.5?).

I read that it should be printed directly on the mobo next to each SATA slot, but that is unclear to me also (see attached photo)

---

### Post by mIk3_08 on 2021-08-06
> **JamButty said:**
> Putting in a second HDD into my desktop and I get what seems conflicting information about which SATA level my mobo supports

I haven't seen any conflict here. If you wanted to see more information about
your new attached hdd/ssd you can also go and run your GUI Disks Application on your Ubuntu.

UDMA is a "protocol transfers data" in burst mode so don't be more confuse on this
your system knows what is newly attached in your system hardware.
In fact, your UDMA has different results; it has ports
```

0xf7e1a100 
0xf7e1a300  

```

If your disk is running properly and you can copy any data from your disk 1 to disk2 and 
vice versa and can run an applications then their is nothing to worry about it. 
You better confused and worrier if your newly attached hardware is not detected by your System.

---

### Post by TheFu on 2021-08-06
IDK, but there is a difference between what the theoretical throughput could be and reality.
Until we get into NVMe SSDs, any the SATA theory really doesn't matter. The storage can't get anywhere near the theoretical throughput.

It is extremely common for SATA controllers to be level I, II, or III. Faster controllers cost more.  Cheaper controllers are pennies in bulk.

That's just the controllers.  Then we have to worry about the storage devices.  No matter what the controller, storage can't push/accept data faster than it can based on read/write and onboard cache performance.

The first step for figuring all of these things is to gather information. Look up the specs for the controller ports and the storage devices.  That means reading the manuals that came with the controller/motherboard or going online for the specifications.  For marketing purposes, they claim whatever the maximum, theoretical performance states, not real-world values.  

For us, real-world is what matters and that vastly changes based on the workload.  The solution is to run some tests for each storage device while connected to each controller port that is different.  For disk performance, there are tools like bonnie++ and fio.
Run read workloads with tiny read that jump around and large contiguous reads.
Run write workloads with tiny writes that jump around and large contiguous writes.
See how vastly different each of those are?

It is good to run those tests exactly the same with a reboot between each run to keep them fair. 

As for ways to tell the type of port by looking at them - some motherboards will use different colors.  white, blue, red.  But the ports will be numbered, like yours are and you can look up in the motherboard manual which port has which speeds.

When doing all of this, watch the units provided.  MB/s and Mbps are VERY different. Do not confuse those.  With storage, both are common.  In general, testing tools will show Mbps and controllers are rated in Mbps.  But disk drives and some GUI tools will show MBps.  I honestly think that is to confuse normal people.

[https://en.wikipedia.org/wiki/UDMA](https://en.wikipedia.org/wiki/UDMA) lists different modes of UDMA. These are not SATA - they are typically PATA (or IDE), which will all be slower.  No amount of trickery will make a PATA device anywhere near a SATA-I throughput.  Those older storage devices just aren't that fast.

In my mind, this is an issue that doesn't make any real difference unless you are trying to decide if an NVMe storage device using a converter will be useful.  Because computers are built with similar level components, having a really fast NVMe storage connected to a 10 yr old laptop won't be worth the cost.  Get a quality SATA SSD device in the 500 MB/s read/write range and be happy that you saved 30% off the cost.

6Gbps is around 750 Mbps - those are theoretical. Nobody actually gets that throughput.

---

### Post by JamButty on 2021-08-06
Thanks for the input. Official sources had no info on SATA support levels. Found lots of people willing to sell me that mobo, but not tell me those specs. Two days of digging through forums turned up many people with the same questions, but no direct answers, but clearly the consensus is that mechanical HDDs will never go beyond SATA2 support levels, theoretical or real-world, so the question is moot as to performance. Ostensibly, the HDD I ordered is capable of SATA3 levels of read/writes, but most forum opinions leaned toward saying no non-SSD can really take advantage of SATA3 support level. 
I did finally find one person claiming that mobo's HDD slots should both be SATA3 and its ODD slots should be SATA2. That source raised another issue by claiming that the cable needs to match the slot support level or BIOS might not recognize it. The cable that is coming with the HDD will be SATA2 (theoretically not compatible with the open HDD slot) so I will get to test that claim I guess. Worst case scenario is I might need to buy another cable. Not a problem.

---

### Post by TheFu on 2021-08-06
SATA 1 didn't know that SATA2/3 were coming. so no support level would have been labeled or put into the MB manual.  All motherboards have manuals online. If you haven't found it, then ask for help with that.  I've never NOT found the manual.

125 MB/s (1024 Mbps) is about the top end of consumer spinning HDDs. Usually real world is slower - closer to 90MBps (720 Mbps) which is half of what SATA1 can theoretically handle.  Some enterprise spinning SAS disks were faster and very loud.  I've some of those too. In a home office, they weren't worth it so I sold them off with a system.  

Cheap quality SATA SSDs are faster and SATA3 could be needed.  But almost nobody in the real world would really notice unless they were editing 4K/8K video.  Then I can see people wanting multiple striped NVMe SSDs but only if their GPU does the transcoding.

When I'm transcoding, I specifically avoid hitting the SSD in my systems - I don't want to drive the write counts up. I stick with WD-Black 5 yr warranty or Gold enterprise HDDs for that type of workload.  If it wasn't my money and time == money in a business, then I'd get multple striped NVMe storage devices.  20+ yrs ago, I got my development team SCSI cards and HDDs because I proved to management that we'd get at least 2 more link cycles per day from each developer over using IDE disks.  It was an easy show and they bought it. This was at a place that wasn't extravagant, but did spend money where it would clearly pay off.

BTW, SATA1, SATA2, and SATA3 cables are all compatible. They will work.  I honestly didn't google for whether there was any impact to performance. Sometimes cables make a huge difference and other times they mean ZERO.  Sorta like how there aren't any "HiDef TV antennas." Antennas from 1972 are just as good at the latest version if the channels are on the frequencies the antenna picks up.  USB cables definitely matter and HDMI cables matter when going beyond 3-6 ft.

After we get passed the drive controller, the motherboard bus architecture and limitations can easily end our efforts at performance.  I added a PCIe USB3 card to a computer from 2010.  It couldn't come anywhere near USB3 speeds or even fast speeds for the HDDs connected that way.  Why?  Because in 2010, the cheapo system bus architecture was the limitation.  There were 2 buses - 1 for the GPU slot and the other for everything else - all USB, all other peripherals. If the bus can only do 1500 Mbps and I have devices connected that support 5Gbps, each, plus 2 GigE NICs ... there really isn't much to be done to get everything working at the same time over that single bus.  We can't get a softball into a straw.

---

### Post by JamButty on 2021-08-07
Once it arrives and I get it working, I can test against the primary HDD to see if there is any significant speed difference. I ordered the exact same model that it came with as primary HDD in 2015 (Seagate ST2000DM001 2TB 64MB Cache SATA 6.0Gb/s). I am not doing anything that requires high performance, but I do have about 2TB of data slowly getting massaged/updated that I want two copies of for security. I am an old fart and don't trust cloud backups. This is just my home desktop and, given the bottlenecks you describe, it does not seem to matter whether the slots are I, II or III.

---

### Post by TheFu on 2021-08-07
> **JamButty said:**
> Once it arrives and I get it working, I can test against the primary HDD to see if there is any significant speed difference. I ordered the exact same model that it came with as primary HDD in 2015 (Seagate ST2000DM001 2TB 64MB Cache SATA 6.0Gb/s). I am not doing anything that requires high performance, but I do have about 2TB of data slowly getting massaged/updated that I want two copies of for security. I am an old fart and don't trust cloud backups. This is just my home desktop and, given the bottlenecks you describe, it does not seem to matter whether the slots are I, II or III.

You probably don't want to hear this, but that model, ST2000DM001, has the worst failure rate.  I owned 2 and both died just after the 1 yr warranty was up.  **Cancel the order if you can.**  Go read the old backblaze drive reliability reports on that model ... and all Seagates.  There's little need to buy the exact same model. Almost any other 2TB 3.5inch HDD would be better.

I'm all for backups. Read my posts here on them.  I'm not a fan of cloudy solutions either.

---

### Post by cryptearth on 2021-08-07
Although this topic is marked solved I had a read - and may want to throw in my two cents:

@TheFu
Well, although I'm aware that there's no real science behind it, but for me it's the exact opposite: I'm using seagates for years now, and have quite a variety of different models. Only two ST3000DM001 failed so far, both after over 3 years of pretty much 24/7 of active usage - the 2TB ones are still all fine.
In contrast: For me it's WD disks failing within only a couple of months - consistency. I never had any WD for a full year without failures - while my seagates are my daily drivers without hickups for years.
Also: As all my disks are S-ATA 6Gbit/s ones - I can assure you they are in fact capable of get over even the theoretical limit of sata2: According to wikipedia sata1 is about 150MByte/s theoretical max, sata2 is about 300MByte/s and sata3 is about 600MByte/s. As the drives have rather large caches I can get over 350MByte/s out of them until the cache fills up during writes or drains on reads. Sustained over long time runs they hold up to about 200MByte/s - 200MByte/s.
So, I can not support your statements, neither the one about seagate vs other brands nor the one that about 125MByte/s is somewhat of a top-tier limit - as my disks do proof otherwise.
But ... as I only ever had about 10 disks or so my sample-size is just too small to get any "real world" conclusion out of it - and could be "within margin of error" when compared to a datacenter with couple of 10.000s of disks.

@OP
Well, what you posted firstly only says, that what's connected to ata1 runs with full sata3 link while what's connected to ata5 only runs at sata1 link. Although modern boards have mulitple controllers for different purposes they usually all match the same specs. So, if you have at laest one controller with full sata3 speeds - it's fair to assume that all s-ata ports are capable of that same sata3 link spec. Using different controllers would just increase the production cost: Using two different components is always more expensive than re-use the same component twice. So it's most likely either just a firmware setting in bios/uefi - or the connected device (most likely an optical drive) just has a sata1 interface.

In very rare cases it could be possible that there're in fact two different kinds of controllers on the board - a sata3 one specifically only for the ports marked as "HDD" - and a slower sata1 one for those ports labled "ODD". BUT: That doesn'T make much sense and would rather be found on a board designed for a very specific purpose which such a configuration requested specifically. S-ATA was designed as a device-independet connection - no matter if it's used for HDDs or ODDs or what ever might be connected by it - hence they all meant to be interchangeable. The actual link is automatically set to the highest both devices, the controller and the device, support. So if the device supports only sata1 the link will be sata1. If both, controller and device, support at least sata2 the link will be sata2. And if both support sata3 the link will be sata3.

As for the cables: That's marketing BS snakeoil. The only real difference between cables from the sata1 standard and from later sata2/3 standards is the added locking clip on the connector. It's proven by many experiments that "old sata1" cables are as equally good as "fancy new sata3" ones. As long as a sata cable is properly shielded and is kept short it's as good as any other - no matter if the connector has the locking clip or what's written on it. You can spent 30 bucks on one single cable - or you can get a bag of 10 for just 5 bucks - turns out: They're the same - and some even produced in the same factory.

---

### Post by TheFu on 2021-08-08
[https://www.backblaze.com/blog/hard-drive-reliability-q4-2015/](https://www.backblaze.com/blog/hard-drive-reliability-q4-2015/)    28% failure rate - ouch.
They moved to 12+TB disks, so they don't have any 2TB since around 2016.  The models are there in 2013-2016 and the reliability is 10x worse.  10x!!!
They used thousands of each model. Some models were bought to almost 30,000 units.  Seems a valid statistical sample from my Stats 101 class.

Going to a different system, both with Intel GigE NICs, The HDD getting the data is a WD Black that is 11 yrs old. 
```
sent 1,491,279,858 bytes  received 54 bytes  [COLOR="#00FF00"]110,465,178.67 bytes/sec[/COLOR]
```
That's about 108MB/sec. 

Using NFSv4, to the same machine with Intel NICs, The storage is RAID1.
```
sent 1,491,279,858 bytes  received 54 bytes  [COLOR="#00FF00"]80,609,724.97 bytes/sec[/COLOR]
```

I don't really copy files on the same system to different disks. For testing:

Copying from the RAID1 onto the WD-Black inside the same Core I5 system:
```
sent 3,492,135,173 bytes  received 149 bytes  [COLOR="#00FF00"]104,242,845.43 bytes/sec[/COLOR]
```

Copying from a Deskstar (Consumer HDD) onto an SSD inside the Ryzen 5 system:
```
sent 3,006,553,108 bytes  received 54 bytes  [COLOR="#00FF00"]122,716,455.59 bytes/sec[/COLOR]
```

Perhaps my systems are just slow?

---

### Post by Yellow Pasque on 2021-08-08
@OP: What motherboard do you have?

---

### Post by JamButty on 2021-08-08
I have a 088DT1 88DT1.  Most of my searches for its specs/manual just led back to very generic ones describing the Dell 3847 model it is in, not the mobo. Some sellers of the mobo list a few specs, but not SATA support levels.

The ata1, ata5 comments clarified my initial confusion about the "dmesg | grep SATA" command, which I thought would be listing info port by port.

Drive will arrive in a couple of days. My guess at this point is I will plug the SATA3 compliant mechanical HDD into port HDD2 with the ostensibly SATA2 cable and get pretty much the same performance as I get from the primary drive, which would be fine. This would only continue as an issue for me if the performance is markedly less.

---

### Post by Yellow Pasque on 2021-08-10
> It seems odd that a mobo would have various levels of support for different SATA slots (one is 6, one is 1.5?).

No, it's not odd. The Intel H81 chipset supports two SATA 6Gbps and two SATA 3Gbps ports. [https://www.intel.com/content/www/us/en/products/sku/75016/intel-h81-chipset/specifications.html#specs-1-0-5](https://www.intel.com/content/www/us/en/products/sku/75016/intel-h81-chipset/specifications.html#specs-1-0-5)
So it's extremely likely the ports labeled HDD are the 6's and the ports labeled ODD are the 3's.

However, if you have an optical drive connected, it will only link up at 1.5Gbps, because that is the maximum the drive is capable of (it is more than sufficient for optical drives, so manufacturers don't bother with higher SATA specs):
```
ata5: SATA link up 1.5 Gbps
```

If you plug a hard disk into the ODD slot, it should run at 3Gbps.

---

### Post by JamButty on 2021-08-10
Thanks, @Yellow Pasque.  Between misunderstanding the DMESG command, the differing support levels, cable marketing gimmicks, misinformation from youtube videos, controllers vs. connecting slots, AHCI vs. UDMA, ACPI vs. native drivers, bottlenecks etc. it was a very muddy picture for an old n00b like me, but it is mostly clear now.

---

### Post by Yellow Pasque on 2021-08-10
No problem. dmesg output can be very confusing. If you have any further questions, don't hesitate to ask.

---

