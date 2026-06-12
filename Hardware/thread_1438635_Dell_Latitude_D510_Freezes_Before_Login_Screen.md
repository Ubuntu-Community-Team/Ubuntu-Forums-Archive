---
title: "Dell Latitude D510 Freezes Before Login Screen"
date: 2010-03-25
forum: Hardware
---

### Post by rudge1980 on 2010-03-25
About 3 months ago I put Ubuntu 9.10 on my old Dell Latitude D510 laptop, in the last couple of days got a weird problem.
My computer starts and loads but when the Ubuntu screen appears just before the login screen, the one where the bar moves across, my computer sometimes freezes.
I had no other problems and it happens maybe twice in every 9 boots.
I checked the forum and googled it but couldn't find my exact problem, I apologize if I've missed it.
I'm hoping somebody's got an answer.
Thanks.

---

### Post by LucianoMS on 2010-04-10
I´m having the same problem. 

I installed Ubuntu 4 months ago and sometimes I experienced the same problem. But since yesterday it appears every start up.

I tried some suggestions, but without sucess. These are

acpi=off and rootdelay=90 on the grub config
remake the swap

Luciano

---

### Post by moetunes on 2010-04-10
Sounds like it may be a X issue - if you can boot into the desktop you can read /var/log/Xorg.1.log - that will be the log from the boot before - or if you can't get into the gui you can read it from the cli with > cat /var/log/Xorg.0.log | less

---

### Post by LucianoMS on 2010-04-11
The file Xorg.0.log is empty (0kb). Is there any other log file that I could check?

The system boots normally in the recovery mode. 

In the normal mode it crashes in the screen that there is "Ubuntu" and a bar that moves from on side to other. When the system crashes the "numlock" and "capslock" still function for one minute, after that they also crashe.

---

