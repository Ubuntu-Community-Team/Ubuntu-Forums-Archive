---
title: "fakeraid woes"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by gimmic on 2007-11-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/156189](https://bugs.launchpad.net/ubuntu/+bug/156189) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I recently moved my primary system over to Ubuntu 7.10 from XP. Aside from some video issues, the install went without issues. I realized my array was not mounted and started looking into that last night. I've got about ~850GB of data so changing the array to another format is not going to be an easy task(although I will do it if I have to)

I decided to start a new thread since this seems to be a genuine Ubuntu bug after some more research. I can mount the array, but get input/output errors when trying to access it. I followed threads over to the NTFS-3G forum where a developer said it appeared to be a problem within ubuntu(here: [http://forum.ntfs-3g.org/viewtopic.php?t=668](http://forum.ntfs-3g.org/viewtopic.php?t=668) ), and the user there posted a bug to launchpad here: [https://bugs.launchpad.net/ubuntu/+bug/156189](https://bugs.launchpad.net/ubuntu/+bug/156189) 

**In the bug post, someone mentioned it was an issue fixed upstream for heron, but I'm wondering if there's some way I can get the fix now?**

I am continuing documentation from this thread: [http://ubuntuforums.org/showthread.php?t=610857](http://ubuntuforums.org/showthread.php?t=610857)

I've got an NTFS raid0 using nvraid(soft/fakeraid) where I've kept all my media / etc.

```

gimmic@waveboxen:/dev/mapper$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bfd0bfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0db7928d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bd75a56

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976768033+   7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

```

```

gimmic@waveboxen:/dev/mapper$ ls -l
total 0
brw-rw---- 1 root disk 254,  4 2007-11-15 10:56 1ATA_WDC_WD4000KD-00NAB0_WD-WMAMY1306447
brw-rw---- 1 root disk 254,  5 2007-11-15 10:56 1ATA_WDC_WD4000KD-00NAB0_WD-WMAMY1306447p1
brw-rw---- 1 root disk 254,  3 2007-11-15 10:56 1ATA_WDC_WD5000KS-00MNB0_WD-WCANU1350580
brw-rw---- 1 root disk 254,  2 2007-11-15 10:56 1ATA_WDC_WD5000KS-00MNB0_WD-WCANU1354387
crw-rw---- 1 root root  10, 63 2007-11-15 10:56 control
brw-rw---- 1 root disk 254,  0 2007-11-15 10:56 nvidia_fgchbaig
brw-rw---- 1 root disk 254,  1 2007-11-15 10:56 nvidia_fgchbaig1
brw-rw---- 1 root disk 254,  6 2007-11-15 10:56 nvidia_fgchbaig1p2

```

```

gimmic@waveboxen:/dev/mapper$ sudo mount -t ntfs-3g /dev/mapper/nvidia_fgchbaig1 /media/raid
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/mapper/nvidia_fgchbaig1 (RAID0)

```

At first I was able to mount, but getting I/O errors when trying to access it. Now After running kpartx -a, I can't get them to mount properly. I wouldnt make a new post over the issue except that I'd really like to avoid trying to juggle 850~GB while nuking my array partition information.
Thanks for any input.

---

