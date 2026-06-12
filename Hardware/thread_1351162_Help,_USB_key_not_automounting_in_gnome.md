---
title: "Help, USB key not automounting in gnome"
date: 2009-12-10
forum: Hardware
---

### Post by reuben on 2009-12-10
From /var/log/messages, when I plug the drive in:

[INDENT]Dec 10 10:02:34 fridge kernel: [351247.415112] scsi 11:0:0:0: Direct-Access     ST       16GB             0000 PQ: 0 ANSI: 0 CCS
Dec 10 10:02:34 fridge kernel: [351247.415542] sd 11:0:0:0: Attached scsi generic sg10 type 0
Dec 10 10:02:34 fridge kernel: [351247.422466] sd 11:0:0:0: [sdk] 31326208 512-byte logical blocks: (16.0 GB/14.9 GiB)
Dec 10 10:02:34 fridge kernel: [351247.423710] sd 11:0:0:0: [sdk] Write Protect is off
Dec 10 10:02:34 fridge kernel: [351247.427713]  sdk: sdk1
Dec 10 10:02:34 fridge kernel: [351247.432715] sd 11:0:0:0: [sdk] Attached SCSI removable disk
[/INDENT]

From /var/log/messages, when I successfully mount it manually using pmount (it shows up on the desktop after pmount, and I'm able to read/write to it):

[INDENT]
Dec 10 10:03:53 fridge kernel: [351326.925689] UDF-fs: No anchor found
Dec 10 10:03:53 fridge kernel: [351326.925692] UDF-fs: Rescanning with blocksize 2048
Dec 10 10:03:53 fridge kernel: [351326.937939] UDF-fs: No anchor found
Dec 10 10:03:53 fridge kernel: [351326.937941] UDF-fs: No partition found (1)
Dec 10 10:03:53 fridge kernel: [351326.950317] UDF-fs: No anchor found
Dec 10 10:03:53 fridge kernel: [351326.950321] UDF-fs: Rescanning with blocksize 2048
Dec 10 10:03:53 fridge kernel: [351326.962566] UDF-fs: No anchor found
Dec 10 10:03:53 fridge kernel: [351326.962568] UDF-fs: No partition found (1)
Dec 10 10:03:54 fridge kernel: [351327.031066] ISOFS: Unable to identify CD-ROM format.
Dec 10 10:03:54 fridge kernel: [351327.065315] ISOFS: Unable to identify CD-ROM format.
[/INDENT]

The nautilus preferences in gconf-editor _are_ in fact set to automount usb devices. And, this disk used to automount in Gnome. It also successfully automounts on my netbook (running XFCE) and my laptop (Gnome, ubuntu 9.10).

Help?

---

### Post by reuben on 2009-12-12
Bump!

---

