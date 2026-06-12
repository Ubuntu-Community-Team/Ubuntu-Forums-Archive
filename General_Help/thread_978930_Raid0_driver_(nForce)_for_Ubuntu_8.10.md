---
title: "Raid0 driver (nForce) for Ubuntu 8.10"
date: 2008-11-11
forum: General Help
---

### Post by UranUtan on 2008-11-11
Hi,

I would like to install Ubuntu 8.10. This time as real, I have done enough home work playing with Ubuntu in a Virtual Machine.
I am novice in Linux and I don't know how to deal with Raid0.

Mother board: Gigabyte GA-73VM-S2 Socket 775
Chipset: nVidia nForce 610i Chipset + GeForce 7050
Hard Drives: 2x 500 GB SATA

The setup currently works OK with Vista Business x64 using the entire 1 TB disk storage.


Question 1: Does Ubuntu 8.10 comes with Raid0 driver? Do you recommend to use Raid0?

Question 2: Do you recommend Dual Boot with both systems? How can I free some GB for the Ubuntu partion?

Thanks in advance for any help.

---

### Post by cariboo on 2008-11-11
Have a look here:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I used this to set up the on board raid on my server.

Jim

---

### Post by eldragon on 2008-11-11
> **UranUtan said:**
> Hi,

I would like to install Ubuntu 8.10. This time as real, I have done enough home work playing with Ubuntu in a Virtual Machine.
I am novice in Linux and I don't know how to deal with Raid0.

Mother board: Gigabyte GA-73VM-S2 Socket 775
Chipset: nVidia nForce 610i Chipset + GeForce 7050
Hard Drives: 2x 500 GB SATA

The setup currently works OK with Vista Business x64 using the entire 1 TB disk storage.


Question 1: Does Ubuntu 8.10 comes with Raid0 driver? Do you recommend to use Raid0?

Question 2: Do you recommend Dual Boot with both systems? How can I free some GB for the Ubuntu partion?

Thanks in advance for any help.

you've got some tricks to do to get the raid0 working.

its been a long time since i last did this, since raid-0 offers almost no performace gain against a single drive.

you need to have dmraid installed before starting the installer for the partitioner to recognize your raided partitions. i dont remember clearly, but last time i did this (it was dapper drake, so, about 2 years), during install, when setting up grub (the bootloader), it will fail (for this same reason).


all this might have changed since 6.06 so, search the forums for dmraid which are the softraid drivers for linux, there ought to be lots of info on the subject.

i found this on the wiki: [https://wiki.ubuntu.com/DmraidSupport](https://wiki.ubuntu.com/DmraidSupport)

so it appears to work out of the box in intrepid. good for you. i would read a bit more on the subject to know what can go wrong.

---

### Post by UranUtan on 2008-11-11
Is it really true that Raid0 brings almost no performance gain?

I have heard this quite a few times. I can witness that on my current machine (Vista x64, Raid 0, 2 SATA drives) the write speed is really fast. However, this is  compared with my 6 years old computer with a single ATA drive. I didn;t run the same Vista on a single STA drive so I cannot really confirm if Raid0 is really faster.

I have read this article: Chipset Serial ATA and RAID performance compared. Whose arrays are faster? [http://techreport.com/articles.x/9124/1](http://techreport.com/articles.x/9124/1)

And it showed that Raid0 has sometimes has some performance than a single drive but for half of the benchmarks, Raid0 is faster than a single drive.

So then is RAID0 really worth to bother with? Anyone of you having experience with Raid0 can give some inputs?

Thanks.

---

### Post by fjgaude on 2008-11-12
Well, in my testing using **hdparm** I can say that raid0 is fast. Two drives make the sequential read about twice as fast as one drive alone; three drives, three times faster; four drives, four times faster. All using **mdadm** software raid under Ubuntu.

You can't boot from raid0, but can from raid1... not recommended.

---

### Post by UranUtan on 2008-11-12
> **fjgaude said:**
> Well, in my testing using **hdparm** I can say that raid0 is fast. Two drives make the sequential read about twice as fast as one drive alone; three drives, three times faster; four drives, four times faster. All using **mdadm** software raid under Ubuntu.

You can't boot from raid0, but can from raid1... not recommended.

I wonder if RAID 0 will scale linearly. There must be a limit somewhere when the combine I/O bandwidth of the drives max out the one of the SATA interface.

I am a total Linux novice, can you please hint what  are**hdparm** and **mdadm**? Are they benchmark tool or admin tool?

---

### Post by fjgaude on 2008-11-12
Well, each SATA drive has 300MB/sec... the raid0 or raid5 array tops out as the CPU, memory, and PCI-E or -X bus top out... I've seen thru-puts as high as 450MB/sec, seq read. Scaling is linear but flattens at the limits of one or more bottle-necks are reached.

There's been lots of testing over the years... a google of such likely will bring much data forward.

Here's one of my test runs:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v; 4x raid5 Seagates, each having 70MB/sec seq read:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

---

### Post by eldragon on 2008-11-12
well, my statement is only based on my personal experinece.

when raid-0 was the hype, if course i bought a brand new nforce4 chipset with two 80gb sata 7200 rpm drives. did a zero raid on them, and installed winxp.

since the computer was new, i did test bootimes having installed on same drives, raided or not. a fresh install with nothing else. i did time software installing, encoding and whatnot. 

there was no real performance gain. might be related to the software based nature of the raid system, but it did seem like the bottleneck was somewhere else.

right now, i got the same computer, with a small 40gb drive as a root partition, and the same 2x80gb raided drives as my /home and swap partitions. i thought having swap on a raid-0 would be beneficial. we will never know, since its hardly ever used :D.

you will have a better experience with lots of ram and preload installed and its daemon running.

my advice:
keep the raid-0 as a big home, and buy a blind fast small 10k RPM drive with lots of cache for the boot and / partition.

---

