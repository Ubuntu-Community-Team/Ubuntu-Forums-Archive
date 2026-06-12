---
title: "Why is disk I/O so poor?"
date: 2010-01-22
forum: Hardware
---

### Post by isecore on 2010-01-22
This has been posted before in various forums, and various bugreports have been filed, but why is the disk I/O in Ubuntu so amazingly poor?

I noticed this at first when I bought a new computer (the same one I'm using now) in March 2008. Disk IO was crap whenever something intense happened. CPU load shot through the roof. Whenever you do something disk-intense, basically the whole system just slows to a glacial speed. Applications stop responding, your mouse-cursor freezes in place. All kinds of strange things.

First everyone blamed AMD chipsets, but a lot of people have this problem regardless of hardware. AMD processors, Intel processors, AMD chipsets, Intel chipsets, different memory sizes, different harddrives, SATA/IDE doesn't matter. Lots of people are affected by this. The only thing in common is that whenever you do something disk-intense, doing anything else at the same time is impossible.

I figured this problem would work itself out. I mean open-source tends to fix itself, right? No, it hasn't happened yet, and I'm getting tired of it. This is an Ubuntu thing as well, it only happens with the Ubuntu-supplied kernel on Ubuntu as far as I know.

So what's the deal? Why is this happening? Why hasn't it been fixed yet?

For what it's worth, my machine is an AMD Phenom 9500 Quad-core, with 4 gigs of RAM on an AMD 790FX-chipsetted motherboard.

---

### Post by leclerc65 on 2010-01-22
I am thinking about going back to EXT2. To hell with journaling.

---

### Post by t4thfavor on 2010-01-22
Still faster than running the same machine with Vista/7. Im not really sure I have experienced the slowdown you speak of. 

It's possible that I don't notice it, but I use plenty of older sata/IDE machines, and have never been dissapointed with disk throughput.

what do you get when you run hdparm -tT /dev/sdX

Timing cached reads:   1586 MB in  2.00 seconds = 793.23 MB/sec
Timing buffered disk reads:  118 MB in  3.02 seconds =  39.13 MB/sec
CPU usage only spiked for about 1 second during the cached read test.

---

### Post by doas777 on 2010-01-22
> **leclerc65 said:**
> I am thinking about going back to EXT2. To hell with journaling.
I actually squeezed about 35 seconds out of my boot by upgrading my ext2 disks to ext4. I can't confirm, but I have heard that journaling is turned off by default, but you'll have to look it up to be sure. 

I have also heard that ext4 performance has been steadly dropping with each new kernel version for a little while now. no idea why, except that perhaps it is the code that fixes the instability/dataloss issues associated with early ext4 adoption. 

I will say this: an fschk on ext4 takes about  15 seconds on a TB drive. I like that.

---

### Post by paulisdead on 2010-01-22
> **doas777 said:**
> I have also heard that ext4 performance has been steadly dropping with each new kernel version for a little while now. no idea why, except that perhaps it is the code that fixes the instability/dataloss issues associated with early ext4 adoption. 

I will say this: an fschk on ext4 takes about  15 seconds on a TB drive. I like that.

[http://www.phoronix.com/scan.php?page=article&item=ext4_then_now&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_then_now&num=1)
There's the benchmarks I think you've heard about.  They do show a drop in performance with ext4 and the more recent kernels.

I haven't noticed any performance drop in what I do, though.  I haven't run any benchmarks, and am running / on a 10k RPM raptor hard drive, though.  The only thing I have noticed is 9.10 takes longer to bootup than 9.04.  I was running a 2.6.31 kernel when 9.04 was current, so I doubt it was the kernel that contributed to the longer boot time in my case.

The fsck time is completely worth it, especially if you've got some large partitions.  I went out of my way on my debian server to put the 9TB LVM volume onto ext4, just since there was no way I wanted to sit through file system checks on it with ext3.

---

### Post by never say never on 2010-01-22
Have you taken any troubleshooting steps to figure out what might be the cause?

Does your Motherboard have 'Raid' built in?  (Are you using it?)

What version of Ubuntu?

What kernel?

Do you regularly apply patches?

Are you running software raid?

Are the drives PATA or SATA?

If PATA are the drive(s) running with DMA 5? (If PIO mode do you have the correct cables)?

How is linux partitioned?

Can you duplicate the problem or is it random?

What is the output of fdisk -l, df -h, free

What is the output of top, vmstat, free when this is happening?

Have you checked the boot log?

A couple of things that come to mind are the disk is thrashing due to swap (which it really shouldn't be with 4 gigs of ram, unless you are running a huge database or AV editing).  

You don't have the correct drivers for your motherboard, I/O Chipset.  This is the most likely item.  The install did not have the correct drivers, so it chose 'default' drivers that work, but make the drives or system run in a degraded mode.

Looking at all of the above will help to narrow down the possibilities.

---

### Post by isecore on 2010-01-22
> **never say never said:**
> Have you taken any troubleshooting steps to figure out what might be the cause?

Does your Motherboard have 'Raid' built in?  (Are you using it?)

It does, and I don't use it. Drives are set to be single drives. I have no interest in the fake RAID-crap motherboards have.

> **never say never said:**
> What version of Ubuntu?

What kernel?

Do you regularly apply patches?

Ubuntu 9.10, all patched up as of 01/22. I apply patches as soon as they show up.

Uname -a says:

```
Linux superbeast 2.6.31-18-generic #55-Ubuntu SMP Fri Jan 8 14:54:52 UTC 2010 x86_64 GNU/Linux
```


> **never say never said:**
> Are you running software raid?

Are the drives PATA or SATA?

No software RAID. I do have my single drive in LVM because if I add more drives later on it's easier to add them to the structure. The drive is a SATA/300 Western Digital 1 terabyte 7200rpm with 16MB cache.

> **never say never said:**
> If PATA are the drive(s) running with DMA 5? (If PIO mode do you have the correct cables)?

N/A to my setup.

> **never say never said:**
> How is linux partitioned?

It's on an LVM2. Inside the LVM is both / and swap. I have no other partitions.

> **never say never said:**
> Can you duplicate the problem or is it random?

Easy. Every time I do something disk intense the load goes up and system becomes less responsive.

> **never say never said:**
> What is the output of fdisk -l, df -h, free

fdisk -L
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bbb32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121570   976510993+  8e  Linux LVM
/dev/sda2          121571      121601      249007+   5  Extended
/dev/sda5          121571      121601      248976   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dce62e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24322   195357696    7  HPFS/NTFS
```

df -h (although I don't see why it's relevant)

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/superbeast-root
                      906G  773G   87G  90% /
udev                  2.0G  392K  2.0G   1% /dev
none                  2.0G  4.7M  2.0G   1% /dev/shm
none                  2.0G  372K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda5             228M   62M  155M  29% /boot
```

free

```
             total       used       free     shared    buffers     cached
Mem:       4057600    3219736     837864          0      83316     715576
-/+ buffers/cache:    2420844    1636756
Swap:     11882488         96   11882392
```

> **never say never said:**
> What is the output of top, vmstat, free when this is happening?

They look normal. The load is according to them niced so low it doesn't appear in a chart of processes. Which leads me to believe it's init or some other very low pid causing it.

> **never say never said:**
> Have you checked the boot log?

Yes, but for what? I don't see anything out of the ordinary there.

> **never say never said:**
> A couple of things that come to mind are the disk is thrashing due to swap (which it really shouldn't be with 4 gigs of ram, unless you are running a huge database or AV editing).

It's not swap. I rarely have to rely on swap - only if I load up several VirtualBox machines at the same time and fire up Google Earth or something, and as soon as it starts swapping it's the same effect.

> **never say never said:**
> You don't have the correct drivers for your motherboard, I/O Chipset.  This is the most likely item.  The install did not have the correct drivers, so it chose 'default' drivers that work, but make the drives or system run in a degraded mode.

So which ones should I use and which ones should I not use? As I stated before I've seen people getting this symptom on a wide variety of hardware. This sounds like a very Windows-type question in my opinion.

---

### Post by never say never on 2010-01-24
Things look good for the most part, however there is at least one change I would make and another I would consider.

I would create a swap partition that is NOT part of the LVM, and not use a swap file in the LVM.  There are many reports of this type of problem when the swap is in an LVM as a partition or a file, especially in ubuntu.  If your LVM is encrypted you are most certainly taking a performance hit.  that hit can be quite severe depending on the encryption type / level chosen.  Don't use encryption on the entire disk unless it is actually needed.

As of the 2.6 kernel there is a [I]swappiness value that is set between 0-100 (60 is the default).  This determines how quickly the kernel will swap pages to disk.  You might try lowering the value of this setting.

Finally, drivers / settings chosen by the installer may not always be the best, there are simply too many variations in hardware for the installer to ALWAYS pick, or the kernel to always have, the correct drivers / settings for your hardware.  When you experience problems with performance it is always a good idea to look at drivers and device settings to make sure there is not a better option.  Normally this applies mostly to NICs and video cards for the most part, but it CAN apply to any device.  So when there is a performance issue these need to be looked at no matter what OS, at least this is true if we are talking about x86 hardware.[/I]

---

### Post by isecore on 2010-01-24
The LVM isn't encrypted and I don't really see what difference it would make anyways since I rarely (if ever) actually use the swapspace. Currently I'm using 0 (zero) swap of ~11 gigabytes available and I'm not exactly lacking open applications.

Swappiness is set to 10. It seems like a nice value. Could set it to zero although I don't really see why as it works just fine as it is.

As for the drivers... yeah... I'd love to go through the millions upon bajillions of available drivers and try them all out (especially when there's several for virtually the same thing) but I just don't have the time for it. Also, isn't it a bit overkill expecting every user to dedicate a huge amount of time figuring out which driver does the trick?

Also, again - I doubt it's a driver-issue. I've read about it affection numerous completely different systems, and the only common theme is that they all run Ubuntu with the Ubuntu-supplied kernel. Recompiling or using a mainline kernel makes the symptom disappear, but then of course incurs other various inconveniences.

> **never say never said:**
> Things look good for the most part, however there is at least one change I would make and another I would consider.

I would create a swap partition that is NOT part of the LVM, and not use a swap file in the LVM.  There are many reports of this type of problem when the swap is in an LVM as a partition or a file, especially in ubuntu.  If your LVM is encrypted you are most certainly taking a performance hit.  that hit can be quite severe depending on the encryption type / level chosen.  Don't use encryption on the entire disk unless it is actually needed.

As of the 2.6 kernel there is a [I]swappiness value that is set between 0-100 (60 is the default).  This determines how quickly the kernel will swap pages to disk.  You might try lowering the value of this setting.

Finally, drivers / settings chosen by the installer may not always be the best, there are simply too many variations in hardware for the installer to ALWAYS pick, or the kernel to always have, the correct drivers / settings for your hardware.  When you experience problems with performance it is always a good idea to look at drivers and device settings to make sure there is not a better option.  Normally this applies mostly to NICs and video cards for the most part, but it CAN apply to any device.  So when there is a performance issue these need to be looked at no matter what OS, at least this is true if we are talking about x86 hardware.[/I]

---

### Post by isecore on 2010-01-25
Oh, and here's the results of doing a hdparm -tT /dev/sda

```
/dev/sda:
 Timing cached reads:   2748 MB in  2.00 seconds = 1373.88 MB/sec
 Timing buffered disk reads:  264 MB in  3.01 seconds =  87.85 MB/sec
```

---

### Post by D3V11 on 2010-01-25
Hardware and/or driver issue. I'm running hardware that is half as up to date as yours and my system has never been smoother. Half the time I have 10 applications running on various sides of the 3d compiz cube with virtually no lag.

---

### Post by isecore on 2010-01-25
My system runs beautifully. But as soon as I do something that read/writes to disk it just slows to a crawl. Move a lot of files, unrar large files, write MKV's to disk... response from any other applications become glacial.

> **D3V11 said:**
> Hardware and/or driver issue. I'm running hardware that is half as up to date as yours and my system has never been smoother. Half the time I have 10 applications running on various sides of the 3d compiz cube with virtually no lag.

---

### Post by D3V11 on 2010-01-25
If it's a new computer it's probably not your hard disk. do a hard reset and see if it fixes the issue. if not then it's probably your processor and it needs the appropriate drivers. either that or you bought a lemon and i'd make those jokers you bought it from fix your pc.

---

### Post by never say never on 2010-01-25
> Recompiling or using a mainline kernel makes the symptom disappear, but then of course incurs other various inconveniences.
 

That says it all right there, like it or not you have one of three issues.

1. Driver / kernel build issue - Most Likely

2. Incorrect BIOS Settings or Bad BIOS version - (Make sure you have the latest BIOS for your MB) - Very Likely

3. Bad Hardware - least likely

Oh and for the record open source does not '*fix itself*' if you want it fixed you are going to have to be prepared to give a great deal of information to the developers. Even then they compile a kernel so that it runs on the most hardware, not so that it runs most efficiently on your hardware!  The beauty of Linux is that you can build custom kernels, taking out options you don't want / need and adding options for things you do want / need.

You seem to think someone owes it to you to fix this problem, but you have dismissed everyone's attempts to help you find a solution.  If you want it fixed you are going to have to get your hands dirty.  Finding the right drivers or correct kernel settings is not that difficult.  Neither is updating the systems BIOS.  If you can't be bothered, then that is another issue entirely.

I was able to find several articles pointing to stability problems and other issues with various linux kernels and the **AMD Phenom 9500 Quad-core AMD 790FX **combination.  That tells me that I am correct in my diagnosis of your problem.

---

