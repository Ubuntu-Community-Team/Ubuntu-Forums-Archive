---
title: "Ubuntu 9.04 -&gt; 9.10 Problems"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by lefty175 on 2009-11-02
Okay, I know that I'm duplicating some previous posts/problems here, but I have not found a solution to mine during my research. When I boot Ubuntu using any of the following: my old kernel, the new kernel, or either in recovery mode, I get to a point where the system says: "Begin: Waiting for root file system . . ." it then eventually says "Alert! /dev/disk/by-uuid/xxxxxxxxxxxxxxxxxxxxxxx does not exist. Dropping to shell!" Where I get dropped to the busy box. Now, I've tried playing around with where grub points, but to no avail. I'm dual booting XP/Ubuntu and have a total of three HDs installed in my machine. Now this is where my problem diverges from some others that I've seen. I cannot reach a command prompt except the busy box, except through the Live CD.

When I boot into the live CD I run fdisk -l and get this: 
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS
/dev/sda2           30402       60801   244188000    5  Extended
/dev/sda5           30402       30402        8001   82  Linux swap / Solaris
/dev/sda6           30403       60801   244179936   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xade5bec7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
/dev/sdb2           30402       60801   244188000    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d790d78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            1021       60800   480182850    f  W95 Ext'd (LBA)
/dev/sdc5            1021       60800   480182818+   7  HPFS/NTFS
```I, however, cannot mount any of the drives, except /dev/sdc5. Opening gparted I get these flags: 

/dev/sda1 & /dev/sdb2:

```
The device /dev/sda1 doesn't exist

ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(2): Failed to check '/dev/sd##' mount state: No such file or directory
Probably /etc/mtab is missing. It's too risky to continue. You might try an another Linux distro.

Unable to read the contents of this file system!
Because of this some operation may be unavailable.
```/dev/sda6 & /dev/sdb1:

```
e2label: No such file or directory while trying to topen /dev/sd##
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.41.9 (22-Aug-2009)
dumpe2fs: No such file or directory while trying to open /dev/sd##

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
```Now, one very strange thing about this is that when I load Super Grub, It gives me a different partition structure when I look at the partitions there:

/dev/sdb1 hd1,0 NTFS
/dev/sdb5 hd1,4 SWAP
/dev/sdb6 hd1,5 ext2fs Ubuntu 9.10

/dev/sda5 hd0,4 NTFS

/dev/sdc1 hd2,0 ext2fs
/dev/sdc2 hd2,1 NTFS

I can go back and get more information from that if need be. Please let me know what other information would be helpful. Oh, I can boot into my Windows partition just fine.

Thank you in advance.

---

### Post by zarathustra on 2009-11-02
I have a similar problem. Upgraded to 9.10 through the update manager, rebooted and it could not find my first SATA hard drive. Tried a clean install using the alternate CD install, recognises the drive on install, boots up into grub that crashes as above. I've booted into it about twice over about 3 different attempts at installation, no idea what could be wrong. It seems everything works but only when it wants to?

---

### Post by lefty175 on 2009-11-02
I should also mention that when I boot with the Live CD the two drives that I cannot access are both my SATA drives. The third drive, an IDE drive, can be accessed just fine. When I boot into Windows I can access the NTFS partitions on my SATA drives. I have tried playing around with the GRUB loader by replacing the first line uuid xxxxxxxxxxxx with root (hdx,x) and truncating the second line to root=/dev/sdxx or root=UUID=/dev/sdxx, but either receive an Error 22 or Error 15 (cannot find and cannot mount respectively), if I remember correctly.

---

### Post by zarathustra on 2009-11-02
Just tried a fix I read for Karmic where you change the path GRUB uses for the root device to an absolute path but this did not work.

---

### Post by lefty175 on 2009-11-02
So, some new information. When I boot with the 9.04 Live CD all my drives appear just fine and I do not have any issues seeing and mounting the other partitions that I cannot under 9.10.

---

### Post by lefty175 on 2009-11-03
I believe that I have solved this. This issue appears to be rooted in 9.10's inclination to look at all SATA drives as a RAID array, thus resulting in the system looking in the wrong location for the OS. I was able to successfully boot into Ubuntu 9.10 by editing the grub menu where it reads something like:

```
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=e1e6bfc7-725d-4456-99cf-2a7141b6ecb9 ro quiet splash
```

I added "nodmraid" to the end of that line so that it read:

```
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=e1e6bfc7-725d-4456-99cf-2a7141b6ecb9 ro quiet splash nodmraid
``` 

And booted. After booting I removed all the dmraid components from the synaptic package manager and can now boot into 9.10 without any issues. While I feel like this is a temporary fix, I am still interested in any other solutions people come up with that might not involve disabling raid. I hope this helps some people though.

---

### Post by zarathustra on 2009-11-03
Have tried editing GRUB when it boots up and adding nodmraid but this didn't seem to affect it. In the end I had to install Linux Mint for the meantime because I really needed the machine working, but I will keep a lookout for fixes.

---

