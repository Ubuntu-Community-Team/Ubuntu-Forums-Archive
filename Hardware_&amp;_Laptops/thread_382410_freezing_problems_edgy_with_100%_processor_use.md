---
title: "freezing problems edgy with 100% processor use"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by jllangston on 2007-03-12
I have the i386 version of 6.10 on my AMD64 laptop. Quite frequently the machine freezes when the processor use is at 100%. It happens so often that when I look up at system monitor and see the system processor use at 100% and the fan is whirring at the  high rate, the machine freezes in roughly 7 sec.

Some things it has frozen on before:


When i attach my palm, sometimes gpilot causes it (roughly 30%). I can stop this before too long if I am quick about killing the program.

After I first installed 6.10, the machine went through the upgrade process and when it hit the capella part, the fan whirred up high and a couple of seconds later stuck.  Got a kernel panic and had to boot up into lower version kernel and do dpkg --configure -i to try installing upgrades again.

When running Automatix2 for the first time, it froze and again I got a kernel panic.



I have run the memtest to see if that was the problem. Ran it all night, no errors. I checked dmesg for obvious errors (i am new at this...)


I have several questions regarding this: Why does this thing freeze up so much? Is there a way of rebooting gracefully without turning the thing off and on? And lastly, if I can't reboot gracefully, it seems that just turning the computer off and on again is kinda harsh. Can I do anything to make things happier when I turn on (filesystem stuff, or ???) ?


This is a very frustrating problem. I am kinda new to Linux/Ubuntu. I would appreciate any and all takers!

---

### Post by apjone on 2007-03-13
Not sure, try having a terminal with 'top' or  a nice version of top 'apt-get install htop' open and see if you can spot what is running. You could try ctrl+alt+back space (restarts the window manager or maybe X) to instead of rebooting as this will just kill your current session and put   you back to the login screen

---

