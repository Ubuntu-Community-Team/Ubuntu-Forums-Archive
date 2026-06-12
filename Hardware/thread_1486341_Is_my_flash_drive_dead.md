---
title: "Is my flash drive dead?"
date: 2010-05-17
forum: Hardware
---

### Post by DigitalRanger on 2010-05-17
I have a Corsair Voyager 64Gb flash drive which I used for backing up my /home partition. However, after reformatting it to Ext3, and copying so many files over to it, and I'd get a broken pipe error. Subsequently, it would only mount intermittently.

Ubuntu (Lucid) was having trouble mounting the drive, sometime reporting a bad superblock. Here's some of my system logs from when it was trying to mount:

```
Debug: (The '28' value keeps incrementing by one and loops to 0 after 127)
May 17 01:41:24 XtremeCT kernel: [15648.144805] usb-storage: device found at 28
May 17 01:41:24 XtremeCT kernel: [15648.144808] usb-storage: waiting for device to settle before scanning
May 17 01:41:29 XtremeCT kernel: [15653.144204] usb-storage: device scan complete
May 17 01:41:29 XtremeCT kernel: [15653.161308] sd 153:0:0:0: [sdb] Mode Sense: 00 00 00 00

Kern.log:
May 17 01:42:49 XtremeCT kernel: [15733.134222]  sdb:
May 17 01:42:49 XtremeCT kernel: [15733.272140] sd 163:0:0:0: [sdb] Assuming drive cache: write through
May 17 01:42:49 XtremeCT kernel: [15733.272152] sd 163:0:0:0: [sdb] Attached SCSI removable disk
May 17 01:42:51 XtremeCT kernel: [15735.715350] usb 1-1: USB disconnect, address 38
May 17 01:42:52 XtremeCT kernel: [15735.972059] usb 1-1: new high speed USB device using ehci_hcd and address 39
May 17 01:42:52 XtremeCT kernel: [15736.106266] usb 1-1: configuration #1 chosen from 1 choice
May 17 01:42:52 XtremeCT kernel: [15736.109498] scsi164 : SCSI emulation for USB Mass Storage devices
May 17 01:42:52 XtremeCT kernel: [15736.126229] usb-storage: device found at 29
May 17 01:42:52 XtremeCT kernel: [15736.126236] usb-storage: waiting for device to settle before scanning
May 17 01:42:57 XtremeCT kernel: [15741.124278] usb-storage: device scan complete
May 17 01:42:57 XtremeCT kernel: [15741.125147] scsi 164:0:0:0: Direct-Access     Corsair  Flash Voyager    0.00 PQ: 0 ANSI: 2
May 17 01:42:57 XtremeCT kernel: [15741.132206] sd 164:0:0:0: Attached scsi generic sg2 type 0
May 17 01:42:57 XtremeCT kernel: [15741.133473] sd 164:0:0:0: [sdb] 126353408 512-byte logical blocks: (64.6 GB/60.2 GiB)
May 17 01:42:57 XtremeCT kernel: [15741.134095] sd 164:0:0:0: [sdb] Write Protect is off
May 17 01:42:57 XtremeCT kernel: [15741.134103] sd 164:0:0:0: [sdb] Mode Sense: 00 00 00 00
May 17 01:42:57 XtremeCT kernel: [15741.134110] sd 164:0:0:0: [sdb] Assuming drive cache: write through
May 17 01:42:57 XtremeCT kernel: [15741.145461] sd 164:0:0:0: [sdb] Assuming drive cache: write through

messages:
May 17 01:44:57 XtremeCT kernel: [15861.012292]  sdb:
May 17 01:44:57 XtremeCT kernel: [15861.150532] sd 179:0:0:0: [sdb] Attached SCSI removable disk
May 17 01:44:59 XtremeCT kernel: [15863.714896] usb 1-1: USB disconnect, address 54
May 17 01:45:00 XtremeCT kernel: [15863.972105] usb 1-1: new high speed USB device using ehci_hcd and address 55
May 17 01:45:00 XtremeCT kernel: [15864.107032] usb 1-1: configuration #1 chosen from 1 choice
May 17 01:45:00 XtremeCT kernel: [15864.122338] scsi180 : SCSI emulation for USB Mass Storage devices
May 17 01:45:05 XtremeCT kernel: [15869.125541] scsi 180:0:0:0: Direct-Access     Corsair  Flash Voyager    0.00 PQ: 0 ANSI: 2
May 17 01:45:05 XtremeCT kernel: [15869.130112] sd 180:0:0:0: Attached scsi generic sg2 type 0
May 17 01:45:05 XtremeCT kernel: [15869.133879] sd 180:0:0:0: [sdb] 126353408 512-byte logical blocks: (64.6 GB/60.2 GiB)
May 17 01:45:05 XtremeCT kernel: [15869.134490] sd 180:0:0:0: [sdb] Write Protect is off

syslog:
May 17 01:45:45 XtremeCT kernel: [15909.160297]  sdb:
May 17 01:45:45 XtremeCT kernel: [15909.297400] sd 185:0:0:0: [sdb] Assuming drive cache: write through
May 17 01:45:45 XtremeCT kernel: [15909.297406] sd 185:0:0:0: [sdb] Attached SCSI removable disk
May 17 01:45:47 XtremeCT kernel: [15911.714516] usb 1-1: USB disconnect, address 60
May 17 01:45:48 XtremeCT kernel: [15911.988032] usb 1-1: new high speed USB device using ehci_hcd and address 61
May 17 01:45:48 XtremeCT kernel: [15912.124370] usb 1-1: configuration #1 chosen from 1 choice
May 17 01:45:48 XtremeCT kernel: [15912.137993] scsi186 : SCSI emulation for USB Mass Storage devices
May 17 01:45:48 XtremeCT kernel: [15912.139595] usb-storage: device found at 61
May 17 01:45:48 XtremeCT kernel: [15912.139597] usb-storage: waiting for device to settle before scanning
May 17 01:45:53 XtremeCT kernel: [15917.136768] usb-storage: device scan complete
May 17 01:45:53 XtremeCT kernel: [15917.137603] scsi 186:0:0:0: Direct-Access     Corsair  Flash Voyager    0.00 PQ: 0 ANSI: 2
May 17 01:45:53 XtremeCT kernel: [15917.148768] sd 186:0:0:0: Attached scsi generic sg2 type 0
May 17 01:45:53 XtremeCT kernel: [15917.154711] sd 186:0:0:0: [sdb] 126353408 512-byte logical blocks: (64.6 GB/60.2 GiB)
May 17 01:45:53 XtremeCT kernel: [15917.155430] sd 186:0:0:0: [sdb] Write Protect is off
May 17 01:45:53 XtremeCT kernel: [15917.155439] sd 186:0:0:0: [sdb] Mode Sense: 00 00 00 00
May 17 01:45:53 XtremeCT kernel: [15917.155445] sd 186:0:0:0: [sdb] Assuming drive cache: write through
May 17 01:45:53 XtremeCT kernel: [15917.159924] sd 186:0:0:0: [sdb] Assuming drive cache: write through
```

The following day, the laptop would not recognize that the drive was connected at all, so I couldn't even reformat it. So I took the following steps:


* Burned a Ubuntu 9.10 live cd to try it there (to test for a bug in Lucid) - no luck.

* Verified that flash drive was picked up on POST screen though.

* Burned a GParted LiveCD, and flash drive was detected and I was able to reformat it.

* Booted back into Lucid, plugged in drive and it was repeatedly mounted & unmounted.

* Went back to GParted Live CD, performed a file system repair, and from then, even 
GParted was only intermittently detecting that the drive was plugged in, but I could no longer do anything with it, like writing a new partition table, because it was only intermittently connected.

* Also tried connecting via cable and direct to port and 'waggling' slightly to make sure there wasn't a loose connection anywhere.

I now find that the drive it constant connected and disconnected from the laptop. This isn't a mounting problem, it's at the device level.

For instance, if I go into a terminal and keep repeating the command "clear; fdisk -l" I'll sometimes get a list of partitions for just my internal hard drive, and sometimes for both my internal hard drive and the flash drive in question.

This means that I cannot even get to rewrite the partition table or reformat.

Any suggestions? Is it dead?

Thanks for reading!

---

### Post by DigitalRanger on 2010-05-19
Polite bump :)

---

### Post by AlexZaim on 2010-05-19
Hm, i don't know. Have you tried other os, like Windows?

---

### Post by DigitalRanger on 2010-05-19
> **AlexZaim said:**
> Hm, i don't know. Have you tried other os, like Windows?

Unfortunately, I don't have access to another computer.

---

