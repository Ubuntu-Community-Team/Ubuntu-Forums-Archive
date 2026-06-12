---
title: "processor fan not running"
date: 2010-04-27
forum: Hardware
---

### Post by bushidofang on 2010-04-27
Hey guys. A total newbie to Linux/Ubuntu here. 

I'm having a problem with my Ubuntu. Recently i installed and am running Ubuntu 9.10 on my BenQ S57 laptop.

My system is:
CPU : Intel Core 2 Duo P8700
System Ram: 4GB RAM
Graphics Card: ATi Mobility Radeon HD4650

My problem is that, my fan would not work or spin at all. I found this out when i was fiddling around Ubuntu and started up Mozilla. While i was surfing around, the laptop switched off by itself. Then, i touched the vent and it was uber hot. I booted into Windows and the fan works just fine as normal. 

Any help? Thanks. :)

Kenny

---

### Post by b862449 on 2010-11-29
From: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508674/comments/28](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508674/comments/28)


this fix is working for my BenQ S57,  thanks Ricardo.



In case it disappeared:



Hi!
 I'm the owner of a brazilian rebranded Benq S57. We have the same  problem around, but as far as I could check, it's a problem in the bios.  I'm not sure BenQ has a new bios for that (in Brazil nobody tried the  BenQ Bios, since the first guy ever to try it used the wrong program and  lost his motherboard... ok, that was probably the program's fault, not  the bios, but can you convince someone else to test in such a situation?  ;) ).
 Anyway, I could solve my problems appending the option during boot  time (after you edit your grub configuration, for some reason I'm not  aware, you must first **turn off** your system and then start it again  will probably go fine. A simple restart *does not* work, ok?):
 acpi.power_nocheck=1
 This can be done by
 sudo gedit /etc/default/grub
 And then edit the line:
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 into:
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi.power_nocheck=1"
 After that, just update your grub:
 sudo update-grub2
 (or is it just update-grub?) and turn off your system. The next power on, your cooler will be working fine, I guess.
 Sincerely,
 Ricardo

---

