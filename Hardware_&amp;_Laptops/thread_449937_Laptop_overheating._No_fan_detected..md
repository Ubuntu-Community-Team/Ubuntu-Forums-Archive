---
title: "Laptop overheating. No fan detected."
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by wdev on 2007-05-20
Hi!

I have a strange laptop it's NTT Corrino 321 - polish product ;) I can't find any info about it and I have really serious problem. My laptop (brand new) is overheating. On Windows XP everything was ok - fan was turning on/off when needed. Ubuntu doesn't even detect my fan (nothing in proc/acpi/fans) and my laptop is overheating - normal temperature showed by acpi -V is about 65 degrees and sometimes it turns off because of temp. Anyone has an idea what to do?

My system is ubuntu 7.04, and short specs of my laptop are:
CPU: Celeron M 360
Mainboard chipset: SIS 661GX + 963L
Graphics: SIS 661GX Mirage Graphics (AGP)

---

### Post by eilu on 2007-05-20
Not a solution per se but a quick fix, as my notebook has no fans at all (just a lot of heatsinks), what I do is grab an electric fan and point it so the air runs parallel to the heatsink holes; it helps move heat away faster. At least you can use the laptop until someone comes by with a correct solution.

---

### Post by henriquemaia on 2008-03-20
> **wdev said:**
> Hi!

I have a strange laptop it's NTT Corrino 321 - polish product ;) I can't find any info about it and I have really serious problem. My laptop (brand new) is overheating. On Windows XP everything was ok - fan was turning on/off when needed. Ubuntu doesn't even detect my fan (nothing in proc/acpi/fans) and my laptop is overheating - normal temperature showed by acpi -V is about 65 degrees and sometimes it turns off because of temp. Anyone has an idea what to do?

My system is ubuntu 7.04, and short specs of my laptop are:
CPU: Celeron M 360
Mainboard chipset: SIS 661GX + 963L
Graphics: SIS 661GX Mirage Graphics (AGP)

This probably doesn’t happen often, but I installing Ubuntu on a friend’s laptop and I have the same issue. Any ideas on how to solve this?

---

### Post by tgalati4 on 2008-03-20
Can you set performance to "On Demand" in the Power Management control panel?  This will reduce the processor speed to save power, but also reduces heat.  You should have that set in both AC and Battery modes.

You have SiS chipset; in the past, SiS was not releasing specifications for their chipsets, so writing drivers for SiS machines was difficult.  I don't know if that situation has changed.  It's possible that you don't have a proper motherboard driver to detect the fan, and therefore it won't turn on.  Perhaps you can force a fan module using modprobe, but someone with a similar chipset will have to weigh in.

---

### Post by sdennie on 2008-03-20
Some laptop vendors (Toshiba in particular) do a very poor (or short sighted) BIOS implementation and so fundamental things like fans may not work on linux.  It's possible that booting with acpi_osi=!Linux could fix the problem or that creating a custom DSDT could fix it.  You should be able to google for either of those things and find information.

---

### Post by henriquemaia on 2008-03-21
Thanks for your replies. I’ll try to have a look at this following your suggestions.

---

