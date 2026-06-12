---
title: "External HDD (WD 3TB drive) mounted fine under 9.04 not under 10.10"
date: 2011-09-28
forum: Hardware
---

### Post by dibbler77 on 2011-09-28
Laptop was running Ubuntu 9.x (.04 i think) I successfully used a Western Digital (WD) My Book Essential 3TB HDD without problems for long time. Upgraded to Ubuntu 10.04 and then 10.10 this weekend and external HDD doesn't work. I have all logs from before when it was working and now from when it isn't.

Look at the before and after info below, note the "is beyond EOD, enabling native capacity" and "is beyond EOD, truncated". How do I get the drive's partitions to be recognized by the kernel so I can mount them, with the end goal of getting access to my data again.

===

Before when it worked the logs show kernel is:
Linux version 2.6.31-23-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #75-Ubuntu SMP Fri Mar 18 18:08:39 UTC 2011 (Ubuntu 2.6.31-23.75-generic)

Before when it worked the logs show the connection as:
```
Sep 14 17:25:18 ryan-laptop kernel: [17559.625948] usb 1-1.2: new high speed USB device using ehci_hcd and address 8
Sep 14 17:25:18 ryan-laptop kernel: [17559.718512] usb 1-1.2: configuration #1 chosen from 1 choice
Sep 14 17:25:18 ryan-laptop kernel: [17559.719488] scsi7 : SCSI emulation for USB Mass Storage devices
Sep 14 17:25:18 ryan-laptop kernel: [17559.719651] usb-storage: device found at 8
Sep 14 17:25:18 ryan-laptop kernel: [17559.719655] usb-storage: waiting for device to settle before scanning
Sep 14 17:25:23 ryan-laptop kernel: [17564.703548] usb-storage: device scan complete
Sep 14 17:25:23 ryan-laptop kernel: [17564.704065] scsi 7:0:0:0: Direct-Access     WD       My Book 1140     1003 PQ: 0 ANSI: 6
Sep 14 17:25:23 ryan-laptop kernel: [17564.704421] scsi 7:0:0:1: Enclosure         WD       SES Device       1003 PQ: 0 ANSI: 6
Sep 14 17:25:23 ryan-laptop kernel: [17564.704884] sd 7:0:0:0: Attached scsi generic sg2 type 0
Sep 14 17:25:23 ryan-laptop kernel: [17564.704935] ses 7:0:0:1: Attached Enclosure device
Sep 14 17:25:23 ryan-laptop kernel: [17564.704981] ses 7:0:0:1: Attached scsi generic sg3 type 13
Sep 14 17:25:24 ryan-laptop kernel: [17564.988387] usb 1-1.1: new low speed USB device using ehci_hcd and address 9
Sep 14 17:25:24 ryan-laptop kernel: [17565.085377] usb 1-1.1: configuration #1 chosen from 1 choice
Sep 14 17:25:24 ryan-laptop kernel: [17565.088588] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input11
Sep 14 17:25:24 ryan-laptop kernel: [17565.088736] generic-usb 0003:045E:0040.0002: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.0-1.1/input0
Sep 14 17:25:35 ryan-laptop kernel: [17575.948119] sd 7:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Sep 14 17:25:35 ryan-laptop kernel: [17575.949616] sd 7:0:0:0: [sdb] Write Protect is off
Sep 14 17:25:35 ryan-laptop kernel: [17575.949621] sd 7:0:0:0: [sdb] Mode Sense: 47 00 10 08
Sep 14 17:25:35 ryan-laptop kernel: [17575.949625] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep 14 17:25:35 ryan-laptop kernel: [17575.951611] sd 7:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Sep 14 17:25:35 ryan-laptop kernel: [17575.952482] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep 14 17:25:35 ryan-laptop kernel: [17575.952489]  sdb: sdb1 sdb2 sdb3
Sep 14 17:25:35 ryan-laptop kernel: [17575.960213] sd 7:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Sep 14 17:25:35 ryan-laptop kernel: [17575.960952] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep 14 17:25:35 ryan-laptop kernel: [17575.960960] sd 7:0:0:0: [sdb] Attached SCSI disk
Sep 14 17:25:38 ryan-laptop kernel: [17578.822701] EXT4-fs (sdb2): barriers enabled
Sep 14 17:25:38 ryan-laptop kernel: [17578.833010] kjournald2 starting: pid 11001, dev sdb2:8, commit interval 5 seconds
Sep 14 17:25:38 ryan-laptop kernel: [17578.890275] EXT4-fs (sdb2): internal journal on sdb2:8
Sep 14 17:25:38 ryan-laptop kernel: [17578.890283] EXT4-fs (sdb2): delayed allocation enabled
Sep 14 17:25:38 ryan-laptop kernel: [17578.890322] EXT4-fs: file extents enabled
Sep 14 17:25:38 ryan-laptop kernel: [17578.901941] EXT4-fs (sdb3): barriers enabled
Sep 14 17:25:38 ryan-laptop kernel: [17578.924540] kjournald2 starting: pid 11006, dev sdb3:8, commit interval 5 seconds
Sep 14 17:25:38 ryan-laptop kernel: [17578.925135] EXT4-fs (sdb3): internal journal on sdb3:8
Sep 14 17:25:38 ryan-laptop kernel: [17578.925139] EXT4-fs (sdb3): delayed allocation enabled
Sep 14 17:25:38 ryan-laptop kernel: [17578.925142] EXT4-fs: file extents enabled
Sep 14 17:25:38 ryan-laptop kernel: [17579.017685] EXT4-fs: mballoc enabled
Sep 14 17:25:38 ryan-laptop kernel: [17579.017701] EXT4-fs (sdb3): mounted filesystem with ordered data mode
Sep 14 17:25:38 ryan-laptop kernel: [17579.046244] EXT4-fs: mballoc enabled
Sep 14 17:25:38 ryan-laptop kernel: [17579.046267] EXT4-fs (sdb2): mounted filesystem with ordered data mode
```

===

Now when it is broken the kernel is:
Linux version 2.6.35-30-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #59-Ubuntu SMP Tue Aug 30 15:58:00 UTC 201
1 (Ubuntu 2.6.35-30.59-generic 2.6.35.13)

Now when it is broken the logs show:
```
Sep 28 10:44:53 ryan-laptop kernel: [ 2215.879794] usb 1-1.1: USB disconnect, address 3
Sep 28 10:45:02 ryan-laptop kernel: [ 2225.294547] usb 1-1.1: new high speed USB device using ehci_hcd and address 7
Sep 28 10:45:03 ryan-laptop kernel: [ 2225.419727] Initializing USB Mass Storage driver...
Sep 28 10:45:03 ryan-laptop kernel: [ 2225.419901] scsi6 : usb-storage 1-1.1:1.0
Sep 28 10:45:03 ryan-laptop kernel: [ 2225.420047] usbcore: registered new interface driver usb-storage
Sep 28 10:45:03 ryan-laptop kernel: [ 2225.420052] USB Mass Storage support registered.
Sep 28 10:45:04 ryan-laptop kernel: [ 2226.420262] scsi 6:0:0:0: Direct-Access     WD       My Book 1140     1003 PQ: 0 ANSI: 6
Sep 28 10:45:04 ryan-laptop kernel: [ 2226.421007] scsi 6:0:0:1: Enclosure         WD       SES Device       1003 PQ: 0 ANSI: 6
Sep 28 10:45:04 ryan-laptop kernel: [ 2226.422206] sd 6:0:0:0: Attached scsi generic sg2 type 0
Sep 28 10:45:04 ryan-laptop kernel: [ 2226.422789] scsi 6:0:0:1: Attached scsi generic sg3 type 13
Sep 28 10:45:04 ryan-laptop kernel: [ 2226.423166] sd 6:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Sep 28 10:45:04 ryan-laptop kernel: [ 2226.423912] sd 6:0:0:0: [sdb] Write Protect is off
Sep 28 10:45:04 ryan-laptop kernel: [ 2226.423920] sd 6:0:0:0: [sdb] Mode Sense: 47 00 10 08
Sep 28 10:45:04 ryan-laptop kernel: [ 2226.423925] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 28 10:45:04 ryan-laptop kernel: [ 2226.425169] sd 6:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Sep 28 10:45:04 ryan-laptop kernel: [ 2226.425903] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 28 10:45:20 ryan-laptop kernel: [ 2226.425913]  sdb: sdb1 sdb2 sdb3
Sep 28 10:45:20 ryan-laptop kernel: [ 2242.794842] sdb: p2 start 5860466688 is beyond EOD, enabling native capacity
Sep 28 10:45:20 ryan-laptop kernel: [ 2242.795921] sd 6:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Sep 28 10:45:20 ryan-laptop kernel: [ 2242.796774] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 28 10:45:20 ryan-laptop kernel: [ 2242.796782]  sdb: sdb1 sdb2 sdb3
Sep 28 10:45:20 ryan-laptop kernel: [ 2242.797346] sdb: p2 start 5860466688 is beyond EOD, truncated
Sep 28 10:45:20 ryan-laptop kernel: [ 2242.797351] sdb: p3 start 22244466688 is beyond EOD, truncated
Sep 28 10:45:20 ryan-laptop kernel: [ 2242.798128] sd 6:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Sep 28 10:45:20 ryan-laptop kernel: [ 2242.798928] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 28 10:45:20 ryan-laptop kernel: [ 2242.798933] sd 6:0:0:0: [sdb] Attached SCSI disk
Sep 28 10:45:20 ryan-laptop kernel: [ 2242.842924] ses 6:0:0:1: Attached Enclosure device
```

===

cfdisk sections list shows:
```
Partition Table for /dev/sdb

               First       Last
 # Type       Sector      Sector   Offset    Length   Filesystem Type (ID) Flag
-- ------- ----------- ----------- ------ ----------- -------------------- ----
   Pri/Log           0         255      0#        256 Free Space           None
 1 Primary         256   732558335      0   732558080 HPFS/NTFS (07)       None
 2 Primary   732558336  2780558335      0  2048000000 Linux (83)           None
 3 Primary  2780558336  5860466687      0  3079908352 Linux (83)           None
```


fdisks -l currently shows (I don't know what it used to show):

```
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 3000.6 GB, 3000558944256 bytes
1 heads, 1 sectors/track, 732558336 cylinders, total 732558336 sectors
Units = cylinders of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000246c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             257   732558336  2930232320    7  HPFS/NTFS
/dev/sdb2       732558337  2780558336  3897032704   83  Linux
/dev/sdb3      2780558337  1565499392  3729698816   83  Linux

```

---

### Post by maul9999 on 2011-09-28
It is limits of your motherboard's BIOS or it might limited in 10.10.  You will want two partitions on your 3 TB external hard drive to keep your data safe.

---

### Post by dibbler77 on 2011-09-28
I suspect it's not a BIOS issue as it worked perfectly moments before the upgrade from the 9.x series. As shown in the above cfdisk output, the original setup did have 2 ext partitions.... neither works now but both did before.

---

### Post by diasf on 2011-09-28
Can you access it  on another pc?
Hell of a coincidence, but still possible, that you got a hard drive problem near the time you upgraded. At least to be sure it isn't the drive itself.

---

### Post by maul9999 on 2011-09-28
Hmm....I agree with diasf.  It might your hard drive problem.  I had WD hard drive and have problem with it.  It is always freeze on me.  If it do work on other computer, test it using SMART from Ubuntu, as well using hard drive benchmark.  Just use CD Live.   In case if you have to buy another hard drive, i would recommend you a SeaGate.  It is most stable hard drive i every have, I have 3 of them (you could say i'm crazy lol).  They never fail me.

---

### Post by dibbler77 on 2011-09-28
This afternoon I created a virtual box with a clean install of ubuntu 9.04 on it (from the iso archives) shared the USB directly with the VB image after it booted. 9.04 still mounts the HDD's two ext partitions perfectly. So the HDD itself if 100% fine. And the partition layout/setup is fine under 9.04. It still works 100% w/in the Virtual Machine running 9.04. It's something between 9.04 and 10.10.

To Clarify: I installed (via apt) Virtual Box (VB) on the computer  running 10.10 (this is the same that will not read/mount the EXTERNAL drive --  this computer has an INTERNAL drive that works fine). After I installed  VB on it I download a new clean 9.04 ISO image. I configured a VB  instance and booted it. Using the ISO, I installed 9.04 onto the VB instance. I  then configured the VB to access the USB hardware directly. I booted the 9.04 VB instance (the VB software itself is running on 10.10). Amazingly, the 9.04 install  in the VB could then *successfully* access the EXTERNAL hdd.

This strongly implies it is not a hardware issue with the computer itself nor the external drive itself.

---

### Post by maul9999 on 2011-09-28
> **dibbler77 said:**
> This afternoon I created a virtual box with a clean install of ubuntu 9.04 on it (from the iso archives) shared the USB directly with the VB image after it booted. 9.04 still mounts the HDDs perfectly. So the HDD itself if 100% fine. And it still works 100% w/in the Virtual Machine running 9.04. It's something between 9.04 and 10.10.

Wait. are you tried to install Ubuntu 10.10 using VirtualBox into your hard drive external?

---

### Post by dibbler77 on 2011-09-30
No, not at all. My problems have nothing to do with VirtualBox or install onto an external drive. As I documented above, my problem is that 10.10 will not access my external HDD in which the previous 9.04 had no problem doing. I clarified my previous post.

---

### Post by diasf on 2011-09-30
Yes, I agree that your problem is not the drive.
This is very weird indeed. I have 2x2Tb WD elements, here's what i get when i hook one of them:

```

Linux dalaran 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 i686 i386 GNU/Linux
---
kernel: [  177.665594] Initializing USB Mass Storage driver...
kernel: [  177.666028] scsi2 : usb-storage 1-1:1.0
kernel: [  177.666179] usbcore: registered new interface driver usb-storage
kernel: [  177.666182] USB Mass Storage support registered.
kernel: [  178.672894] scsi 2:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
kernel: [  178.673551] sd 2:0:0:0: Attached scsi generic sg2 type 0
kernel: [  178.676402] sd 2:0:0:0: [sdb] 3907024896 512-byte logical blocks: (2.00 TB/1.81 TiB)
kernel: [  178.677373] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
kernel: [  178.677377] sd 2:0:0:0: [sdb] Assuming drive cache: write through
kernel: [  178.678993] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
kernel: [  178.678997] sd 2:0:0:0: [sdb] Assuming drive cache: write through
kernel: [  178.692626]  sdb: sdb1
kernel: [  178.697249] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
kernel: [  178.697254] sd 2:0:0:0: [sdb] Assuming drive cache: write through
kernel: [  178.697259] sd 2:0:0:0: [sdb] Attached SCSI disk
```

I know is a different drive, this does not prove anything (might be irrelevant), but it's there. It's identical to yours. It works here. That's the weird part. (I even have more logical blocks than you, even with a smaller disk, because each block of yours is 4 of mine).


I know what the problem is. The system thinks your sector has 512 bytes, but your sectors actually have 4k. From your dmesg:

```

[ 2226.425169] sd 6:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[ 2242.794842] sdb: p2 start 5860466688 is beyond EOD, enabling native capacity

```

732558336 x 4kb = 2.72TB
5860466688 x 512b = 2.72TB.

That's even clearer on the fdisk -l :
```
Note: sector size is 4096 (not 512)
```

Ok, problem identified. But as to the solution.... apparently, ppl assumed 512bytes as block size, and since your drive is big, it has 4k block. Check this out:

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by dibbler77 on 2011-10-03
Interesting find. Any ideas on why it would (and still does) work under 9.04 but not 10.10 even with the 4k vs 512 section size? Did something happen in the 10.10 that changed support for 4k sector size?

---

### Post by maul9999 on 2011-10-03
> **dibbler77 said:**
> Interesting find. Any ideas on why it would (and still does) work under 9.04 but not 10.10 even with the 4k vs 512 section size? Did something happen in the 10.10 that changed support for 4k sector size?

Hmm.... Most time. when i format my hard drive, i usually to choose Allocate size, aka section size.  I choose 4 MB on 10.10, but honest i had never seem problem like that.  So you should be able to find it on disk unity.

PS my old WD is SATA II type hard drive, which is why it work pretty good.  I think Ubuntu isn't ready for SATA III and USB 3.0.  Maybe 11.10 will be ready for it.

---

