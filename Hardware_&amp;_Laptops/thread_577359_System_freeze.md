---
title: "System freeze"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by ushills on 2007-10-16
Hi

I have experienced a few stability issues over the past few days with my Ubuntu system.

Occassionally the whole system locks and freezes.

I have tried to run memtest from the Live CD, however, it alwways stops after 24 seconds when testing pattern 80808080 (or something like that)

If I disable the USB controller the test will run pasts 24 seconds and the memory checks out fine.

Any ideas what in my system might be causing problems.

---

### Post by balthamaisteri on 2007-10-16
My asus laptop freezes if i don't have cd on my drive, it is driving me crazy.

I really hope that this will be fixed on 7.10, or atleast 8.04

---

### Post by ushills on 2007-10-16
Funny mine is an Asus motherboard as well.

All was fine until earlier this week, more testing tonight!

---

### Post by PmDematagoda on 2007-10-16
This problem could be attributed due to corrupted RAM or due to the memory modules being too dirty. Clean them out a bit by removing them, clean the gold contacts using a clean, dry and soft cloth, do not damage the gold contacts.

Clean the slots as well by blowing some dry, clean air gently in such a way that any dust will be removed.

Replace the memory modules and see if the freezes reduce.

---

### Post by ushills on 2007-10-16
> **PmDematagoda said:**
> This problem could be attributed due to corrupted RAM or due to the memory modules being too dirty. Clean them out a bit by removing them, clean the gold contacts using a clean, dry and soft cloth, do not damage the gold contacts.

Clean the slots as well by blowing some dry, clean air gently in such a way that any dust will be removed.

Replace the memory modules and see if the freezes reduce.


Thanks, I will give this a try.  I only hope that the problem doesn't lie with the CPU or Motherboard.  I cannot afford to replace those yet!

I do seem to have a problem with motherboards hence why I brought ASUS last time.  So far in about 7 years this will be my third motherboard, don't know why but freezes usually start first!

---

### Post by PmDematagoda on 2007-10-16
I've had the same problems with my Intel PC, I solved it by cleaning the memory modules out, but even that didn't work after that same problem happened a second time, so that time I changed their places,  put memory modules in different slots, now it seems to work with no problems, seems to be the problem with the RAM slots.

---

### Post by ushills on 2007-10-17
Don't ask me what happened but I solved the problem.

After booting I logged into the desktop and waited.  The wi-fi network strenght meter dropped to red and a few seconds later the system froze.

As I had set up my wifi manually due to the RT61 driver not accepting WPA by default, I reset the connection an changed the setting for ra1, and removed references to eth0 and eth1 in the interfaces file.  I also added eth0 and eth1 to the blacklist.

I had done all of this before but for some update must have changed the settings.

---

