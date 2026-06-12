---
title: "File system problem"
date: 2012-10-23
forum: Hardware
---

### Post by gqterre on 2012-10-23
Hi everyone, I'm new in this forum, but not new to ubuntu.

The other day, I had a problem with my laptop, and even if I found on the web some guys with a problem very similar to mine, it presentes in a form that I have not found any other case, that's why I turn to you.

I describe the situation. I have a laptop HP Pavilion dv6 where I have installed ubuntu 12.04 and windows 7. The other day I was working unplugged when I had to plug in the power supply. When I plugged into the electrical outlet there was a spark. At the moment I didn't care ... and I'm not sure this is really the cause of my problem, but the fact is that from this moment on, the PC has started to go wrong: the PC started working very slowly with frequent little crashes.

I then decided to reboot and while rebooting appeared

```
error: unknown file system
press a key to continue
```and then a screen that told me that he could not find the hard drive.

After some attempts, suddenly the PC has resumed work;  when I start ubuntu, still appears the message "unknown file system", but ubuntu actually starts correctly. However, it's very slow.

In the web I found other problems unknow file system, however, in all cases ubuntu could not start, but to mine does...

I am really worried that some internal component might have been damaged.

I post here the output of some command that might be useful:

fdisk:

```
Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   814061717   406826059    7  HPFS/NTFS/exFAT
/dev/sda3       814063614   976768064    81352225+   f  W95 Esteso (LBA)
/dev/sda5       892394752   976543154    42074201+   7  HPFS/NTFS/exFAT
/dev/sda6       976543218   976768064      112423+   b  W95 FAT32
/dev/sda7       884541440   892393471     3926016   82  Linux swap / Solaris
/dev/sda8       814063616   876687359    31311872   83  Linux
/dev/sda9       876689408   884539391     3924992   82  Linux swap / Solaris
```cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=adb8ef8c-f1d6-4037-9535-3d6c7a42b8e2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=4cb7958e-ae5b-4296-86e4-25eaf6146d16 none            swap    sw              0       0

```blkid

```
/dev/sda1: LABEL="SYSTEM" UUID="C2A638A2A638993D" TYPE="ntfs" 
/dev/sda2: UUID="5E726F20726EFC61" TYPE="ntfs" 
/dev/sda5: LABEL="RECOVERY" UUID="9C9453979453732E" TYPE="ntfs" 
/dev/sda6: LABEL="HP_TOOLS" UUID="5246-4C55" TYPE="vfat" 
/dev/sda7: UUID="850ddf9b-c677-441b-b717-f5dbb2e2dd6e" TYPE="swap" 
/dev/sda8: UUID="adb8ef8c-f1d6-4037-9535-3d6c7a42b8e2" TYPE="ext4" 
/dev/sda9: UUID="4cb7958e-ae5b-4296-86e4-25eaf6146d16" TYPE="swap"

```Please, note that in this moment I do need the pc, and I cannot afford some configuration problems with program I'm using so if some of the solutions that you suggest might involve this kind of problem, please say it.

Thanks a lot

---

