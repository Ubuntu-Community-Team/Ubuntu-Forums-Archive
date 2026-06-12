---
title: "Fan ALWAYS on, but not in windows 7"
date: 2010-04-25
forum: Hardware
---

### Post by Zalastax on 2010-04-25
I recently installed Ubuntu 9.10 and I had soem wireless network problems that now is solved. But all the time that Ubuntu is on I hear the fans being on all time.
In windows 7 the fans turn of when I come to the login screen( might be some process that turns on at that point) and it won't go on again unless I do REALLY heavy stuff for a long time.
I have read lots of threads on how to solve this but it won't work, the lm-sensors only shows temperature and when I modify what the threads say I should nothing changes.
The sensor also always show exactly the same temperature so it might even be corrupt.

I would like to get help with how I could set the fans to only go on when they are like 60°C and after that be on untill they are like 50°C, some sort of software would be really nice.

My computer is a Compaq cq5144sc and the chip is Asus f800

---

### Post by P4man on 2010-04-25
It could be two different issues; either the cpu is cool and fan control is not working properly, or there is a problem with cpu clock scaling and the cpu is indeed hot enough to warrant that fast fan speed (and overriding it might be a bad idea, if it can even be done).

Perhaps something easy to check: right click on the top panel, add to panel, select CPU frequency scaling monitor. Can you see the cpu clockspeed go up and down depending on what you do?

---

### Post by Zalastax on 2010-04-25
Yes I can, and the fan can't always be so hot that the fans need to be running

---

### Post by P4man on 2010-04-25
ok next thing to do is probably checking bios. If you go in to the bios, do you have settings to control the fan speed? I would also advice checking if there is a new bios available for your machine, and if so, upgrade the bios to hopefully fix acpi issues

---

### Post by demosthene1 on 2010-04-25
grub menu.lst for fan fix:

acpi_osi="Linux"

kernal line in menu.lst looks something like this:

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cb256055-368d-4cdf-992b-908c1eb92482 ro acpi_osi="Linux" quiet splash

---

### Post by dino99 on 2010-04-25
have you run sensors-detect and applied the settings ?

---

### Post by Zalastax on 2010-04-25
I done nothing but now my fans go as they should, just like in windows 7, I will change this thread to solved

---

