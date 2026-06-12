---
title: "WD external drive not being detected after boot"
date: 2014-03-21
forum: Hardware
---

### Post by l0uismustdie on 2014-03-21
Hello. I recently upgrading from Ubuntu 12.04 (where this was all working fine) to Ubuntu 12.10 (where this seems to have stopped working). The issue is that I have a WD drive plugged in via USB and this is no longer detected when the machine reboots. I **can** however manually unplug the drive and plug it back it and it will mount and be recognized. Previously I had the drive automatically mounted from /etc/fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=12199d54-83a1-44b5-8d8b-dfdde45ecefe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=24897433-0ffc-46e2-ad62-753301d4a93f none            swap    sw              0       0
UUID=f8483e27-5517-47e7-860d-a9952b050b24 /media/cavalry  auto      defaults,nofail 0    

```

But since the drive isn't being recognized during the boot process this fails. After rebooting if I check [FONT=courier new]lsusb[/FONT] I get:
```

Bus 002 Device 002: ID 05ac:8502 Apple, Inc. Built-in iSight
Bus 003 Device 007: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 007 Device 003: ID 05ac:021a Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

In addition it can't be seen in [FONT=courier new]fdisk -l[/FONT] either:
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4095        2047+  ee  GPT
/dev/sda2   *        4096   221896703   110946304   83  Linux
/dev/sda3       221896704   234440703     6272000   82  Linux swap / Solaris

```

I have tried modifying my /etc/modules to include [FONT=courier new]usb_storage[/FONT]:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
usb_storage

```

but this hasn't worked. I've also tried checking the dmesg log:
```

[  911.115075] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:10:40:f3:96:7f:38:08:00 SRC=192.168.8.91 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=19450 PROTO=UDP SPT=56352 DPT=8612 LEN=24 
[  916.300184] hub 1-0:1.0: unable to enumerate USB device on port 2
[  916.700096] usb 1-2: new high-speed USB device number 9 using ehci-pci
[  917.397937] usb 1-2: New USB device found, idVendor=1058, idProduct=1130
[  917.397950] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  917.397958] usb 1-2: Product: My Book 1130
[  917.397965] usb 1-2: Manufacturer: Western Digital
[  917.397972] usb 1-2: SerialNumber: 5743415A4134353232383630
[  917.398672] scsi4 : usb-storage 1-2:1.0
[  918.397087] scsi 4:0:0:0: Direct-Access     WD       My Book 1130     1012 PQ: 0 ANSI: 6
[  918.400607] scsi 4:0:0:1: Enclosure         WD       SES Device       1012 PQ: 0 ANSI: 6
[  918.401819] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  918.402057] scsi 4:0:0:1: Attached scsi generic sg3 type 13
[  918.405343] sd 4:0:0:0: [sdb] 2930210816 512-byte logical blocks: (1.50 TB/1.36 TiB)
[  918.406905] sd 4:0:0:0: [sdb] Write Protect is off
[  918.406910] sd 4:0:0:0: [sdb] Mode Sense: 47 00 10 08
[  918.407600] sd 4:0:0:0: [sdb] No Caching mode page present
[  918.407604] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  918.409685] sd 4:0:0:0: [sdb] No Caching mode page present
[  918.409691] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  919.026693]  sdb: sdb2
[  919.033285] sd 4:0:0:0: [sdb] No Caching mode page present
[  919.033292] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  919.033298] sd 4:0:0:0: [sdb] Attached SCSI disk
[  919.039036] ses 4:0:0:1: Attached Enclosure device
[  919.507295] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)

```

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
Could you have a flaky usb cable that sometimes works and sometimes doesn't? I had one like that. Gave me hell until I figured it out.

---

### Post by l0uismustdie on 2014-03-21
I suppose anything is possible but this seems unlikely to me. It has been working with Ubuntu 12.04 for months with no problem. The only difference being the upgrade to 12.10. In addition it seems like a flaky cable would sometimes not work after manually unplugging and plugging in.

---

### Post by l0uismustdie on 2014-03-22
Note: In addition I just tried using a different USB port and this made no difference.

---

### Post by Dreamer Fithp Apprentice on 2014-03-22
That was good thinking. Always good to eliminate the eliminate the easy things even when the probability is low. A pity it didn't work. I'm out of easy ideas. If you don't find something else to try you might want to upgrade again, either to Saucy or the new LTS coming out next month. For what it's worth, under Saucy with an Openbox-only DE with thunar, I have no problems with booting from an external WD usb drive and the other partitions on the same drive mount automatically as I instructed in fstab. I also had no problems with pretty much the same hardware setup under 12.04 with no problem running Lubuntu. But I'm not sure I ever installed 12.10 at all. If I did, I didn't use it very long. Good luck.

---

### Post by mikewhatever on 2014-03-22
Can you remove the 'nofail' option from the fstab line. Hopefully it will produce some clues in the logs. Also, isn't there a '0' missing from that line?

---

