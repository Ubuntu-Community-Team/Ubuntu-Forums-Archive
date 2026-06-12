---
title: "USB stopped working on upgrade"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by zewrestler on 2008-04-02
Hello,

I've upgraded from Fawn to Gibson yesterday. The system crashed part way through the upgrade, I was able to go into recover mode and have dpkg fix any problems... So I thought. I tried to use my USB drive today. Upon mounting it, I got a popup window that said  "cannot mount volume: unable to mount volume". When I clicked on details, I got the following message: "mount wrong fs: type bad option, bad superblock on /dev/sb1/,  missing code page or helper program, or other error. In some cases useful info is found in syslog -try dmesg|tail or so.

I've run "tail -f /var/logs/message" when I plug in my flash drive.  The following is the output I get:
Apr  2 17:29:47 localhost kernel: [  329.676000] usb 5-3: new high speed USB device using ehci_hcd and address 6
Apr  2 17:29:47 localhost kernel: [  329.892000] usb 5-3: configuration #1 chosen from 1 choice
Apr  2 17:29:47 localhost kernel: [  329.900000] scsi6 : SCSI emulation for USB Mass Storage devices
Apr  2 17:29:52 localhost kernel: [  334.908000] scsi 6:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
Apr  2 17:29:52 localhost kernel: [  334.920000] SCSI device sdb: 1001472 512-byte hdwr sectors (513 MB)
Apr  2 17:29:52 localhost kernel: [  334.920000] sdb: Write Protect is off
Apr  2 17:29:52 localhost kernel: [  334.928000] SCSI device sdb: 1001472 512-byte hdwr sectors (513 MB)
Apr  2 17:29:52 localhost kernel: [  334.928000] sdb: Write Protect is off
Apr  2 17:29:52 localhost kernel: [  334.928000]  sdb: sdb1
Apr  2 17:29:52 localhost kernel: [  334.928000] sd 6:0:0:0: Attached scsi removable disk sdb
Apr  2 17:29:52 localhost kernel: [  334.928000] sd 6:0:0:0: Attached scsi generic sg2 type 0


when I remove the drive, it says: 
Apr  2 17:40:58 localhost kernel: [ 1000.512000] usb 5-3: USB disconnect, address 6


Any suggestions what to do to fix this?  this has happened on multiple flashdrives that worked before upgrading.

---

### Post by zewrestler on 2008-04-03
I took my system to a Lug group tonight, and I have some updates.  They were not able to fix my problem.  But we discovered that we can still mount if we do the mounting through the CLI. It appears that the automounting feature of Ubutnu has someone corrupted.  We looked, and believed that it is autofs as the default ubuntu has, so we reinstalled it.  even after the reinstall, the system still wouldn't work correctly and not automatically mount the drive. Does this help narrow down the problem?

---

