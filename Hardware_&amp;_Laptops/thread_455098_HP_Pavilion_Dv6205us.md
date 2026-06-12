---
title: "HP Pavilion Dv6205us"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by dyingscience on 2007-05-26
My laptop specs are as follows:

SATA 80GB Hard Drive.
Intel Pentium Dual-Core Inside T2060 @ 1.6GHz
1.0GB DDR2 PC6300 Ram
x24 DVD-R/RW DL ROM-Drive
Intel Xtreme Graphics 64MB 
Current OS: Windows Vista Ultimate
Laptops Intended OS:  Windows Vista Home Basic

If you need anymore after reading the rest please inform me so.
  
I can not do the following:

1. Install Ubuntu due to having a SATA HD
2. Can not run the LiveCD because my laptop will not give me the option to run live disc even though the CD is in my DVD-ROM Drive at the time of start-up.

---

### Post by shagpile on 2007-05-26
Hmmmm, interesting.

I have a DV1665EU , not the same model but more or less is internally identical.

I have edubuntu running on mine. Had ubuntu and kubuntu running on it perfectly in the past as well.
(Both 6.10 and feisty)

Have you gone into the bios setup and selected CD as the first boot device?

---

### Post by Kobalt on 2007-05-26
Check out your BIOS settings (the boot order) to be able to boot on a CD/DVD.
I also own a HP dv6000 laptop and Ubuntu is runing just fine. Sata HD are now quite well handled in Ubuntu.

---

### Post by dyingscience on 2007-05-26
I have successfully installed Feisty and am loving it.

But I do have one issue:

I can not use wireless.

---

### Post by Kobalt on 2007-05-27
You can get it working this way : [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

---

### Post by dyingscience on 2007-05-27
I do not have that model wireless card. In Device Manager under Ubuntu Feisty it says i have the following Wireless Card I will boot up Vista in a moment and see if the two match: But here is what Linux says I have:

Dell Wireless 1390 WLAN Mini-PCI Card

Question: How do I have a Dell part in a Hewlett-Packard?

---

### Post by syberdave on 2007-05-28
I think that's what the wireless card returns to the kernel.

From lspci:
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

This wireless card support is broken in Fiesty? I tried the beta and reported the bug in some hardware support survey program. Lame. Anyway, it's because the kernel's bcm43xx drivers don't work with these cards for some reason. It pretends to work, but no data gets through. It's weird.

So yeah, you need to use ndiswrapper.

---

### Post by rbanffy on 2007-06-08
I am very happy, delighted in fact, to inform you all that the bcm43xx thingie that came with this notebook works fine under the 2.6.22-6 kernel currently shipping in Gutsy.

While upgrading to gutsy is quite suicidal right now, I was able to just install the kernel package by putting the gutsy main repository in the sources.list, doing the proper apt-get update, apt-cache search and apt-get install (no apt-get upgrade because I am not insane and I need to get work done in this laptop).

Good luck, folks

---

