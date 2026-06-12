---
title: "Urgent problem with GRUB"
date: 2008-11-11
forum: General Help
---

### Post by ichiban-2k7 on 2008-11-11
I used to have ubuntu 8.04 on my computer, dual boot with xp. I had both partitions formatted due to a fatal error, and reset my BIOS. Now, everytime I try to boot into the vista installation disk, I only get "Please Wait, GRUB loading. Error 21".

I have no idea how this is possible; both harddrives have been formatted and BIOS reset, and I am unable to use my computer. Please halp.

---

### Post by IceBadger on 2008-11-12
Resetting your BIOS may have changed the boot priorities to change.  Make sure that your BIOS is set to boot from your CD/DVD drive before your HDD.

Depending on how your partitions were setup and how you reformatted your drive(s), your boot sectors may still be intact, resulting in grub loading with the "unknown boot error".

---

### Post by dfgilbert on 2008-11-12
I think you need to reset your MBR.

Or go into setup - usually f2 when your bootstrap is loading.

And set it to boot from the CD drive first.


Edit:  snaps, IceBadger posted similar as I was typing.

---

### Post by ichiban-2k7 on 2008-11-13
Thanks for the responses,

I have no idea how to set my computer to boot up into the cd/dvd drive first, All I know is that my cd/dvd drive is set as secondary master, with my first harddrive as primary master, and I have no idea how to change it in my BIOS, which is a 2003 version, which may be too old. Is changing it to booting of CD/DVD drive still possible?

Thanks

---

### Post by caljohnsmith on 2008-11-13
> **ichiban-2k7 said:**
> Thanks for the responses,

I have no idea how to set my computer to boot up into the cd/dvd drive first, All I know is that my cd/dvd drive is set as secondary master, with my first harddrive as primary master, and I have no idea how to change it in my BIOS, which is a 2003 version, which may be too old. Is changing it to booting of CD/DVD drive still possible?

Thanks
The fact that you have your HDD as primary master is of course the reason why it boots first on start up and gives you that Grub error; the only way to correct that is to go into your BIOS and change the boot order. Some BIOSes have a key you can press on start up to temporarily change your boot order, sometimes F10, F12, etc. You should be able to press some function key (F2, F10, F12, etc) on start up to enter your BIOS (or possibly some other key depending on your BIOS), and then you should hopefully be able to change the boot order. If you don't know which function key it is, try pressing as many of them as you can on start up, and that may get you into your BIOS. Or if you know your motherboard model and manufacturer, you could always visit their website and most likely find out which key it takes to enter your BIOS. Good luck and let us know how it goes. :)

---

