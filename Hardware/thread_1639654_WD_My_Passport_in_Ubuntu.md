---
title: "WD My Passport in Ubuntu"
date: 2010-12-06
forum: Hardware
---

### Post by random.nerd.evan on 2010-12-06
There is a couple similar issues in the forum but mine seems to be different. 
I helped a co-worker out by using Ubuntu to pull pictures and music off an iPhone problem is the drive they gave me to copy them to will not mount.
It is a Western Digital My Passport drive.

The keys that were asked for in the other posts were the fstab file.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9a042f38-7c34-468f-a31e-a88fe3d72e37 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e6517101-026e-4917-a1fc-bb90d5f9d687 none            swap    sw              0       0

```
and the df command output.

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            230582428   3707460 215161996   2% /
none                   1799488       240   1799248   1% /dev
none                   1805080      1592   1803488   1% /dev/shm
none                   1805080        88   1804992   1% /var/run
none                   1805080         0   1805080   0% /var/lock
```

Any help greatly appreciated by me and my coworker.

Thank you all in advance.

---

### Post by Fafler on 2010-12-07
```
tail -f /var/log/messages
```

Connect the drive and post the output.

---

### Post by random.nerd.evan on 2010-12-07
Here you go, looks like it is picking something up.
Thank you in advance.

```
randomnerdevan@randomnerdevan-laptop:~$ tail -f /var/log/messages
Dec  7 18:42:19 randomnerdevan-laptop kernel: [ 6832.224621] video LNXVIDEO:00: Restoring backlight state
Dec  7 18:42:20 randomnerdevan-laptop kernel: [ 6832.750932] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  7 18:42:22 randomnerdevan-laptop kernel: [ 6834.392784] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Dec  7 18:42:22 randomnerdevan-laptop kernel: [ 6834.683407] sr 2:0:0:0: [sr0] CDB: Test Unit Ready: 00 00 00 00 00 00
Dec  7 18:42:23 randomnerdevan-laptop kernel: [ 6835.653958] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Dec  7 18:42:56 randomnerdevan-laptop kernel: [ 6867.876750] lo: Disabled Privacy Extensions
Dec  7 18:50:13 randomnerdevan-laptop kernel: [ 7304.996087] usb 2-2: new full speed USB device using ohci_hcd and address 6
Dec  7 18:50:13 randomnerdevan-laptop kernel: [ 7305.624107] usb 2-2: new full speed USB device using ohci_hcd and address 7
Dec  7 18:50:14 randomnerdevan-laptop kernel: [ 7306.252082] usb 2-2: new full speed USB device using ohci_hcd and address 8
Dec  7 18:50:15 randomnerdevan-laptop kernel: [ 7306.797086] usb 2-2: new full speed USB device using ohci_hcd and address 9

```

---

### Post by Fafler on 2010-12-08
It might be hard to make this work. It isn't identified by the kernel and doesn't use the standard USB storage driver. Googleing a bit, it seems likely to be the build in encryption/backup software acting up. I'm not sure what to do about it, but personally i would either return it to the store or move the drive to another USB enclosure.

---

