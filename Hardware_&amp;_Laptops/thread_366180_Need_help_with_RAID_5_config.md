---
title: "Need help with RAID 5 config"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by caffienda on 2007-02-20
RAID 5 on Ubuntu Linux: Setup Ques on Promise TX2 card
I am setting up a File Server, and I'm thinking I would like to use the 5 160 GB drives that I have in a RAID 5 array.

I'm planning on running Ubuntu 6.10 Server (unless someone can tell me a better distro). Here is the hardware I'm planning:

MSI 865PE II MOBO (supports 4 IDE, 2 SATA)
P4 2.6Ghz
Sapphire 9200 AGP card
Promise Ultra 133 TX2 (supports 4 IDE drives)
Rosewill 4-channel SATAII (Promise based)

5 160GB WD IDE Drives
5 500GB WD SATA Drives
1 36GB Raptor (OS drive)
1 Samsung 8x DVD+-R/RW

I will have the DVD drive and a 160Gb, each on it's own channel off the MOBO. The other 4 160's will be on the Promise card.
Will this work for RAID 5 with Linux software running the RAID config?

The 5 500's are not in a RAID config.

I'm open to any comments here too! Thakns!
Edit/Delete Message

---

### Post by caffienda on 2007-02-20
What would  be the ideal FS to run on this system?

---

### Post by tommi-fi on 2007-08-28
Hey,

I have similar setup at my home. I have two Promise ATA cards, Intel mobo 2Gb RAM, 4x250Gb for files and 2x320Gb for system. And DVD Drive.

I can't get my setup to work. I installed KUbuntu 7.04 on my Raid1 mirror of 2x320Gb. But when I try to connect any drives to those Promise cards, system wont boot. It locks up after loading drives.

Have you installed or just gave up?

---

