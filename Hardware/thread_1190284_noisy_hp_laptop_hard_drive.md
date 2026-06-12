---
title: "noisy hp laptop hard drive"
date: 2009-06-17
forum: Hardware
---

### Post by wormhole on 2009-06-17
Hi. This is an old problem, but until now I didn't have the time to look into it. I looked around for a bit but couldn't find relative info in other threads/sites.

  I have an HP laptop model nx7300 with a SATA hard drive (FUJITSU MHW2120BH) and Kubuntu 8.04 running on kernel 2.6.24-24. Memory is 1 GB and 512 MB swap.
  My problem is that every time a (larger) program loads or unloads (this includes boot and shutdown) or there is a lot of processing going on (like apt installs), the harddrive is very noisy (kind of like the grinding sound old drives used to make). This applies to both NTFS and ext3 partitions. Under Windows XP SP2, the drive is completely silent (well, almost - you can make out a slight working sound, but it's very faint).
  The drive seems to be in good condition (I checked SMART info). I'm more worried about (early) wearing. Sometime ago I looked around a bit and found something about how the Linux kernel does more writing (commiting) than the Windows kernel.

Things I've tried to no avail:
-  I suspected excessive swapping so I tried reducing swappiness to 10 in hope that it would hinder thrashing but there is no obvious change.
-  I tried changing the APM setting with hdparm to 254 (also note that the drive does not support acousting management)

  So, I'm curious if this a kernel issue (design if you will) or a configuration issue and if I should be worried. I could provide a sound recording if necessary, but it's very low quality (phone recording).
  Thanks in advance !

---

### Post by wormhole on 2009-06-20
follow-up with more info:

The commit interval for my ext3 partition is 5 sec (though not sure if this is relevant).
I launched Kubuntu 9.04 from an USB stick and began accessing my partitions. Strangely, only when accessing the ext3 and its adjacent NTFS partition (sda3) does the noise occur.
Now, according to GParted, the physical partitions seem to be contiguous.
Could this be an ext3 issue ? Can't figure this out.

I've attached a screenshot of GParted's view of my hard disk.

---

### Post by wormhole on 2009-06-26
second follow-up:

I have upgraded and the problem persists in Kubuntu 9.04 64bit, kernel 2.6.28-13-generic

---

### Post by philcamlin on 2009-06-26
its not ubuntu its your hard drive or you need to upgrade your ram because your swap is full

check system monitor:popcorn:

---

### Post by wormhole on 2009-06-26
This happens from boot time, and ram is usually only 60-80% full, while swap usually 10-20% full.
I don't think it's the harddrive because this doesn't happen under Windows, so doesn't look like a hardware defect (like i said SMART is ok)

---

### Post by philcamlin on 2009-06-26
20% swap will make your hdd noisy and is it ide or sata?

---

### Post by wormhole on 2009-06-26
SATA hard drive (FUJITSU MHW2120BH) - same thing if run in native SATA or PATA mode
I understand about the swap, but it's weird that the noise starts from kernel load (the kernel image is stored on the ext3 partition)

---

### Post by wormhole on 2009-07-25
Third and (presumably) last follow-up. 
After more observation, I've determined that the crunching sound occurs when accessing my sda3 and sda6 + swap partitions from Kubuntu and the sda3 (NTFS) from Windows (see screenshot above), although in Windows it is less loud (probably due to distance - see below and filesystem driver). I guess I didn't notice since the Windows install drive is sda1, which does not experience the noise and I mainly use sda3 for storage (less frequent access).
My only conclusion is that this is due to the drive's architecture, as these partitions would be nearer to the center of the platter (being 'last linearly'), and from what I gather from Wiki, this would impact access (to some extent) as there is less data density in this region. Strange that it's noisy though. I just hope it's not a serious defect. The fact that I've had no hardware problems in two years time and SMART metrics seems ok is reassuring.
I suppose I have my answer, just don't like it very much :P

---

### Post by mikewhatever on 2009-07-25
You can actually set the acoustic management value wtih hdparm. I'd try something like this just to see if there is a difference: 
**sudo hdparm -M 200 /dev/sda**.

Edit: Oops, just noticed your hdd doesn't support acoustic management.

The acoustic management value can range from 254 (fastest/noisiest) to 128 (slowest/quietest).

There is also a better way to reduce disk activity, then playing with swappiness.
[http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

---

