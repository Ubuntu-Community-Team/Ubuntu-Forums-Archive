---
title: "Strange Laptop boot problem... have to remove battery to restart"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by Ascetik on 2006-08-14
I am having this problem with ubuntu but actually i have had it with almost every linux distro that i have tried to dual boot on my laptop. I have to remove the battery and power to start the machine only after i have booted into the linux partition. It shuts down fine but when i restart i don't even get the bios screen and memory check screen. At this point i will remove all power sources and then restart and it goes straight into grub and everything is perfect. What i cannot understand is what is hanging around in memory that will not even let the bios start. I have tried differnt boot options like acpi=on and off. I have no idea what to do. I have looked on forums forever and never found an answer. I do not have this problem when i boot into windows. Any Ideas.

Thanks in advance.

---

### Post by kaens on 2006-08-14
What are the specs on your laptop, as well as make and model?

---

### Post by Ascetik on 2006-08-14
its a Toshiba p25-s670. P4 HT 3.2Ghz nvidia go5700. I am dual booting windows multimedia center and ubuntu.

---

### Post by kaens on 2006-08-14
So I did some looking around, and it looks like there's a lot of people having problems with Toshiba p25 series laptops and having to remove batteries/plug to reboot cleanly, and that it is linked to acpi, and possibly to BIOS (If you have a pheonix bios, the toshiba-extras part of acpi won't work).

Have you tried doing acpi=off apm=on? One person said that that worked for them, but that they had some issues detecting battery life.

Also, I read that Toshiba released a bunch of laptops with desktop processers in them . . . which seems somewhat ridiculous. I would think that heat would become an issue really fast.

---

### Post by Ascetik on 2006-08-15
yes, i have tried:
acpi=on
acpi=off
apm=on
apm=off
acpi=on apm=off
acpi=off apm=off
acpi=off apm=on
acpi=on apm=on

I have exhausted all of those options. It is strange a while back i was trying out several different distos and they all acted the same except for one distro of Debian. They all used grub but this one distro worked. Not sure why. I might try creating another partition and see what options it was using after it was installed.

---

### Post by eqspec on 2007-04-29
The only linux distro that I have been able to install and not have this problem was Debian Sarge, which uses the 2.4 kernel. 2.6 kernel will cause this problem because of acpi  and power management features in 2.6. Also like previously mentioned, Phoenix bios. Try Sarge, it's not that bad and it runs great on this laptop. For now I have decided to put up with the problem and hope that a fix shows up or I'll get a new laptop. I'm running Feisty.

---

### Post by CountdeMonet on 2008-03-09
I also have the same exact problem, it's driving me nuts!   It occurs both during dual boot and off a live CD.  The only distro I've used that works reboots properly is White hat Knoppix.  Does anyone know where I can get a bios that would fix this problem?  Toshiba only offers the phoenix bios.

---

