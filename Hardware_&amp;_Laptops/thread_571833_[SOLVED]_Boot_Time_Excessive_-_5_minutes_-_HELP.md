---
title: "[SOLVED] Boot Time Excessive - 5 minutes - HELP"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by steveneddy on 2007-10-09
I think I am having a software problem, but I am not ruling out hardware. Hardware is System76 Serval Performance laptop, core 2 Duo at 2 Ghz and 2 Gig RAM. Wireless, USB mouse, power adapter plugged in the whole time. 

My boot time seems to be excessive. I recently installed Ubuntu 64 bit and I came from Ubuntu 32 bit. I have enjoyed years of 30 second or less boot times, and this has me wondering what could be the problem.

The boot time is approaching 5 minutes which starts at Grub not auto starting. No matter what I try, I can't get Grub to start by itself anymore.

The boot process stalls at the loading hardware drivers. This is getting longer and longer. 

Another stall at the acpi modules. 

Something about the can't get the time change, clock tick off.

This whole time, by the time the hardware drivers section comes up and stalls, the cooling fan speed goes to full on. 

Also, the system won't boot at all if there is no internet connection to the machine at all. You have to plug in a live ethernet cable or have a wireless connection to connect to.

This is really frustrating. After the machine is booted up and I'm logged on, the laptop runs great.

EDIT:

Just rebooted again and the hwclock is taking up 100% cpu time right after login. This may be a clue to solving this puzzle.

EDIT #2:

Just ran **hwclock** in terminal and it still says that it is 7:15 am today but the display says it is the true time. Weird. ( i before e, except after c and spelling weird ) maybe my Firefox dictionary is wrong, too. I'll check that. Leave no stone unturned, they say.

---

### Post by steveneddy on 2007-10-09
I found the problem by installing 

bootchart

and looking at the files in /var/log/bootchart

I noticed two places where the hwclock was taking up all of the CPU cycles and researched from there.

Turned out all i had to do was change the clock in my BIOS and everything is good.

:popcorn:

---

