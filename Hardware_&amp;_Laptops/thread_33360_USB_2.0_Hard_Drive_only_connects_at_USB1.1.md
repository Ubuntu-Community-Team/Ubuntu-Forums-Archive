---
title: "USB 2.0 Hard Drive only connects at USB1.1"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by movery on 2005-05-10
I have a very strange problem.  When connecting my ipod mini via USB on my laptop it connects as USB2.0 and works like I would expect - fast.  When I connect an old IDE hard drive using an IDE->USB adaptor it works like I would expect - fast.

When I connect my (host powered) argosys 80GB 2.5" notebook HD (USB2.0 compliant) it only connects at USB1.1 and is painfully slow.  When connecting this to my friends debian box though it works as fast as can be!  The strange thing is dmesg shows that it is detected as a high speed device but it is almost as if doesn't get picked up by my USB 2.0 controller

[I]May 10 20:00:41 localhost usb.agent[10508]:      usb-storage: already loaded
May 10 20:00:46 localhost kernel:   Vendor: HTS54808  Model: 0M9AT00           Rev: MG4O
May 10 20:00:46 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
May 10 20:00:46 localhost kernel: SCSI device sda: 156301489 512-byte hdwr sectors (80026 MB)
May 10 20:00:46 localhost kernel: sda: assuming drive cache: write through
May 10 20:00:46 localhost kernel: SCSI device sda: 156301489 512-byte hdwr sectors (80026 MB)
May 10 20:00:46 localhost kernel: sda: assuming drive cache: write through
May 10 20:00:46 localhost kernel:  /dev/scsi/host1/bus0/target0/lun0: p1 p2
May 10 20:00:46 localhost kernel: Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
May 10 20:00:46 localhost kernel: usb-storage: device scan complete
May 10 20:00:47 localhost scsi.agent[10558]:      sd_mod: loaded sucessfully
May 10 20:00:47 localhost udev[10569]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda' becomes '%k'
May 10 20:00:47 localhost udev[10569]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda' becomes '%k'
May 10 20:00:47 localhost udev[10569]: creating device node '/dev/sda'
May 10 20:00:47 localhost udev[10614]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda1' becomes '%k'
May 10 20:00:47 localhost udev[10614]: creating device node '/dev/sda1'
May 10 20:00:47 localhost udev[10617]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda2' becomes '%k'
May 10 20:00:47 localhost udev[10617]: creating device node '/dev/sda2'
May 10 20:00:48 localhost kernel: ReiserFS: sda1: found reiserfs format "3.6" with standard journal
May 10 20:00:55 localhost kernel: ReiserFS: sda1: using ordered data mode
May 10 20:00:55 localhost kernel: ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
May 10 20:00:55 localhost kernel: ReiserFS: sda1: checking transaction log (sda1)
May 10 20:00:55 localhost kernel: ReiserFS: sda1: Using r5 hash to sort names[/I]

All help here **VERY** much appreciated as this is really pi**ing me off.  I bought it to mass backup all my important data and copying 10GB of data at the moment takes well over 5 hours!

---

