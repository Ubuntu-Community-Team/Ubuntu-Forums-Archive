---
title: "my hdd is not detected by windows vista, or by ubuntu"
date: 2008-12-28
forum: Hardware
---

### Post by lionfox on 2008-12-28
I recently bought a used laptop. It has a 40GB compaq hdd, it is a satellite pro 6100
P4m 2ghz
512mb ram
wireless
etc...

The problem is that the hdd is not able to be detected by either vista, or ubuntu. I also have an XP disk that says I386/ biosinfo.sys is missing when I try to install XP.

I think that the HDD is corrupt, as I have removed and reinstalled the drive twice now, and made sure it was well connected.

The ubuntu Live CD works like a charm, and the only problem is it not being able to read the drive, so that I can install it on my system.

I don't think it is bios, or anything of that sort. The drive looks clean, but seeing as I got it in houston, it may be a hurricane Ike Hard drive. I could really care less if I have to get a new drive, because I got he laptop for 200, which is a sweet deal. I saw it was only 60 bucks for a 120 GB drive.

You guys think it's the drive? Or am I being overly hopeful?:guitar:

---

### Post by swudee on 2008-12-28
Is the new drive SATA or PATA?
If it is a SATA drive, you may need to move a link on the drive to reduce the transfer rate from the drive, as it may not be supported by the laptop at the higher speed. The earlier SATA chipsets don't know about the later modes so the drive has to be altered with a jumper lead to accommodate them.
Something to look into.

---

### Post by lionfox on 2008-12-28
IDE Slim

---

### Post by nick09 on 2008-12-28
Well here is a HDD for 80 bucks and its a 2.5" EIDE from what I know.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136159](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136159)

Who says you can't beef up a old laptop?;)

---

### Post by lionfox on 2009-01-03
thanks

---

### Post by logos34 on 2009-01-03
on the live cd run this in terminal:

sudo fdisk -l

anything?

---

