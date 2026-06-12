---
title: "Asus P5B Deluxe - Core 2 Duo 6300 - Live CD Won't Boot"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by andrewpmk on 2006-08-17
My i386 Ubuntu 6.06 Live CD will not boot on my computer. It hangs on the graphical boot display after reading "Mounting root partition".

My hardware configuration:
[LIST]
[*]Asus P5B Deluxe motherboard
[LIST]
[*]Intel 965G chipset
[/LIST]
[*]Intel Core 2 Duo E6300 processor (Allendale)
[*]1066MHz FSB bus
[*]1 GB DDR2 533MHz memory
[*]160 GB SATA hard drive
[*]ATI Radeon X1600 Pro / 256 MB GDDR2
[*]LG SuperDrive GSA-H10N/Bk - DVD-ReWriter / 16x DVD±R, 10x DL / OEM / Black
[*]No floppy drive
[/LIST]

My computer was assembled by a local computer maker, Kingston Computer Planet. Windows works fine, but the Ubuntu Live CD will not boot. Is there any workaround that will allow me to boot the Live CD?

---

### Post by drewster4590 on 2006-09-16
I am having the same issue. I have similar specs compared to andrewpmk.
[LIST]
[*]Asus P5WD2 Premium motherboard
[*]Intel 955X chipset
[*]Intel D 805 processor
[*]1 GB DDR2 memory
[*]400 GB SATA hard drive (partitioned into several parts)
[*]ATI Radeon AIW 2006 / 256 MB GDDR2
[*]NEC DVD+-RW Drive / Black
[*]No floppy drive
[/LIST]
I am somewhat surprised this topic went four weeks and had no reply.

---

### Post by jakemikey on 2006-09-16
If you do a search for "P5B" in the forums you'll find mountains of threads and posts covering this problem.  The P965 chipset lacks an integrated IDE controller (99% of optical drives out there are IDE), so P965 motherboards must rely on the JMicron controller which apparently isn't supported in kernels prior to 2.6.18, which includes Dapper.  A fix is expected in the daily builds of Edgy starting on Monday 9/18. If you can get a IDE->USB enclosure for your CD drive that'll be the easiest short term fix.

---

### Post by sheenaramone on 2006-09-17
I tried a usb dvd drive yesterday on my Asus P5B and was able to boot 6.06 but there was no internet connection. There must be an issue with the lan on this board, too.  So I'm stuck with Windows on this  computer.

---

### Post by RomeoSierra on 2006-09-28
> **sheenaramone said:**
> I tried a usb dvd drive yesterday on my Asus P5B and was able to boot 6.06 but there was no internet connection. There must be an issue with the lan on this board, too.  So I'm stuck with Windows on this  computer.

There are linux drivers on the ASUS CD (which is supplied with P5B board) for Marwell's chipset (ethernet controller).

---

