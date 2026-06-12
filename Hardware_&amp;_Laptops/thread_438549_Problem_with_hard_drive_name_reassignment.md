---
title: "Problem with hard drive name reassignment"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by Rhadamanthos on 2007-05-09
I have quite a few hard drives, and under Feisty, I have been having a problem with them randomly changing identifiers.

For example, I have /dev/sdb mounted as ~/foo and /dev/sdc mounted as ~/bar. These are in /etc/fstab.

So, I log in one day, and the files normally in foo are in bar, and vice versa.  I fire up gparted, and the drive that was formerly /dev/sdb is now /dev/sdc and vice versa. I didn't think this was supposed to be able to happen, any ideas why it might be, or how to stop it?

System setup:
AMD Athlon64 3200+
Ubuntu Feisty Fawn 64-bit
Abit KV8-Pro motherboard with onboard IDE (4 ch) and SATA (2 ch)

HD setup:

IDE controller (Mobo):
DVD reader
CD burner
400GB Seagate (/dev/hdc)
80Gb Maxtor (/dev/hdd)

Promise Card (PCI, IDE):
400 GB Seagate (/dev/sda)
80 GB Maxtor (/dev/sdb)

SATA controller (Mobo):
500 GB Western Digital (/dev/sdc)

/dev/sda, /dev/sdc, and /dev/sdb are the ones that randomly change letterings. I haven't had any problems with the /hdX drives.

---

