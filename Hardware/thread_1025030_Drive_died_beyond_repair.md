---
title: "Drive died beyond repair?"
date: 2008-12-29
forum: Hardware
---

### Post by stefanst on 2008-12-29
Hi!

My data storage drive from my MythBuntu box died on me. To me it looks like it's catastrophic and beyond data recovery. But I HOPE that somebody here disagrees with that assessment...

My setup:
X86 AMD
MythBuntu 8.10 (64 bit)
The drive in question is a 500GiB SATA WD Caviar
Filesystem on that drive is XFS

Here is a dump from dmesg:

```

[    3.665885] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xb800 irq 20
[    3.665888] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xb808 irq 20
[    4.140028] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    9.148024] ata5.00: qc timeout (cmd 0xef)
[    9.148028] ata5.00: failed to IDENTIFY (SPINUP failed, err_mask=0x4)
[   14.508019] ata5: link is slow to respond, please be patient (ready=0)
[   15.056026] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   15.076278] ata5.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max UDMA/133
[   15.076281] ata5.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   15.093352] ata5.00: configured for UDMA/133
[   15.412022] ata6: SATA link down (SStatus 0 SControl 300)
[   16.072405] ata5: exception Emask 0x10 SAct 0x0 SErr 0x1910000 action 0xe frozen
[   16.072412] ata5: SError: { PHYRdyChg Dispar LinkSeq TrStaTrns }
[   16.072419] ata5: hard resetting link
[   22.220022] ata5: link is slow to respond, please be patient (ready=0)
[   23.160026] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.192897] ata5.00: configured for UDMA/133
[   23.192904] ata5: EH complete
[   23.217124] ata5.00: exception Emask 0x10 SAct 0x0 SErr 0x1910000 action 0xe frozen
[   23.217131] ata5: SError: { PHYRdyChg Dispar LinkSeq TrStaTrns }
[   23.217137] ata5.00: cmd 25/00:08:80:5f:38/00:00:3a:00:00/e0 tag 0 dma 4096 in
[   23.217140] ata5.00: status: { Busy }
[   23.217146] ata5: hard resetting link
[   29.364016] ata5: link is slow to respond, please be patient (ready=0)
[   29.968027] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   30.001115] ata5.00: configured for UDMA/133
[   30.001124] ata5: EH complete
[   60.044040] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   60.044092] ata5.00: cmd c8/00:38:28:00:00/00:00:00:00:00/e0 tag 0 dma 28672 in
[   60.044178] ata5.00: status: { DRDY }
[   60.044221] ata5: hard resetting link
[   65.404018] ata5: link is slow to respond, please be patient (ready=0)
[   70.052018] ata5: COMRESET failed (errno=-16)
[   70.052059] ata5: hard resetting link
[   75.412018] ata5: link is slow to respond, please be patient (ready=0)
[   80.060018] ata5: COMRESET failed (errno=-16)
[   80.060058] ata5: hard resetting link
[   85.420018] ata5: link is slow to respond, please be patient (ready=0)
[  115.064018] ata5: COMRESET failed (errno=-16)
[  115.064058] ata5: limiting SATA link speed to 1.5 Gbps
[  115.064060] ata5: hard resetting link
[  120.088018] ata5: COMRESET failed (errno=-16)
[  120.088058] ata5: reset failed, giving up
[  120.088097] ata5.00: disabled
[  120.088112] ata5: EH complete
```

I looked at it with "testdisk" and it can see the drive and it's size. It also detects the sectors, heads etc. OK, but I can't see a partition table or write a new partition table.

Any ideas?

Thanks!

ST

---

### Post by teaker1s on 2008-12-29
try knoppix live cd it can mount damaged file systems and you can burn files to cd/dvd

---

### Post by stefanst on 2008-12-29
Thanks!

Unfortunately this drive is beyond what the Knoppix boot-disc can fix. There is no superblock, no partition table- nothing. All read- or write-attempts only create errors. 

Looks like it's not the actual drive, but the electronics that are whack. Almost like the connection between the actual drive and the electronics is disconnected.

If there is a fix, it may involve having to take a solder-iron to my drive. 

Any other ideas?

---

### Post by cariboo on 2008-12-29
Put the external drive in the freezer for a couple of hours, I've used this method sucessfully sevral times to retrieve data from a defective hard drive. Once you have got you data off the drive, you should be able to get an RMA to get a replacement drive. In a lot of cases you may have to run the diagnostic software to get an error code. You can geet the diagnostic software from the hard drive manufacturers web site.

Jim

---

### Post by alecjw on 2008-12-29
I used to have loads of problems with my SATA drive and found that the problem was simply that the cable wasnt completely connected. It seemed to unplug itself a lot. Have you tried unplugging the data cable and putting it back in?

---

### Post by stefanst on 2008-12-29
Will try the freezer over night- never heard of that one before. I would have been more skeptic, if you would have suggested the oven ;-)

Tried to re-seat the cable and used different cables. No change...

ST

---

### Post by alecjw on 2008-12-29
I had a dead hard drive once. I put it in the freezer overnight, took it out and put it straight back into the computer (well, xbox) and it was fixed.
Not for long though, but it might be long enough to rescue your data.

---

### Post by Cracauer on 2008-12-29
To me that looks like a screwup somewhere in the USB layers, not with the drive itself.

Rip the thing out of the external case and run it directly connected to the computer.

Don't do the freezer thing with the full USB enclosure, if you do it, just the naked drive. I'm serious.

Anyway, it's possible that real drive errors are there and only appear USB-related due to the error messages reported. Then you are screwed :)

---

### Post by stefanst on 2008-12-29
Hi Cracuaer,

it's an internal drive. It's in the freezer now- wrapped in anti-static bag and a ziploc bag.

I am very curios, if this works. I googled the freezer fix and it seems that it is mainly for drives that fail mechanically. "unfortunately" my drive seems mechanically sound. Plates spin up fine, no weird noises...

ST

---

### Post by teaker1s on 2008-12-30
Depending on how vital you feel the data is, the other possibility, which isn't by any means certain.

most hard drive control boards will have model and version and even software version on them. It may be possible to buy a drive off ebay with same board. 

make sure all information on controller board matches

I did this with an hitachi/ibm Deathstar (Deskstar) that are unreliable to say the least.

---

### Post by stefanst on 2008-12-31
AMAZING!

the "freeze-the-drive" method actually got me somewhere!
I was able to boot up and see the drive and browse it. However, by the time the drive was mounted and I had navigated to the right directory, my time was over and it was too late to actually copy data.
So now the drive is back in the freezer.

It appears that I will need to extend the cooling beyond the initial 5 minutes in order to be able to copy my data.

I am planning to keep the drive in it's Ziploc baggy and submerge that in some salty ice-water (just like you would use for making ice cream). Does that sound like a doable idea?

Thanks so far!

ST

---

### Post by lexen on 2009-01-03
Hey guys, I put my broken hard drive in the freezer over night and my question is:  Do I let it "thaw" or do I start it up right out of the freezer?


Thanks,
Lexen

---

### Post by Cracauer on 2009-01-03
> **lexen said:**
> Hey guys, I put my broken hard drive in the freezer over night and my question is:  Do I let it "thaw" or do I start it up right out of the freezer?


Hard to say. You need to be aware of condensation, which can build up water on the circuit board and short it out if you start it right out of the freezer. You should probably leave it in the ziplock bag. Don't breathe near it.

I think it's safer to first let it warm up somewhat and use it and only get more radical when that doesn't work. On the other hand you might not have too many tries with the temperature cycle.

You can also leave it in a ziplock and put it on ice in another ziplock to have more time to read data.

Whatever you do, you should report what works and what doesn't for the next guy.

---

### Post by stefanst on 2009-01-03
It works!

Just putting it in the freezer and then hooking it up only gave me maybe 3 minutes to work with - that includes boot-up. So I built a somewhat minimal XUBUNTU system for fast boot. 

Then I take the drive out of the freezer and leave it in the Ziploc bag (1 gallon). IMPORTANT: Make sure the bag is absolutely new and watertight.
I immediately put the drive inside the bag in a tall container containing shredded ice, water and salt (stir before use). This solution gets actually colder than 32 degrees, because the salt lowers the melting point of the water.

The cables stick out the top of the bag. 

This whole setup sits next to the computer. Fire up and I get about ten minutes of use out of it each time. There is plenty of condensation on the board and once I had a leaky bag and even got some water inside. But it did not hurt the drive (so far).

At this point in time I got roughly 50GB off the drive. (200 to go!)

So all-in-all I would call my first attempts at "cryo-computing" a success.

---

### Post by NorthernSuze on 2009-04-02
Ah, this is the the "pop it in the freezer" post I was looking for!

Thank you so much for the suggestion.  My /home sata drive went flaky the same day I read this post. A good percentage of the data I was pulling off it was corrupted. Amazingly I was able to recover the entire drive after putting it out the front door <grin> and running the cables back to my computer. 

I did have back-ups for everything excepting that mornings work, but it was an interesting exercise to recover the everything on the drive intact.

-14C weather in what for most of the world is balmy spring has its perks!:lolflag: Thank you!
Suzanne

---

