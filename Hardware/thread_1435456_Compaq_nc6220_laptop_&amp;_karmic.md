---
title: "Compaq nc6220 laptop &amp; karmic"
date: 2010-03-21
forum: Hardware
---

### Post by MrCheese on 2010-03-21
I just upgraded my HP Compaq nc6220 from Jaunty to Karmic. Jaunty was sweet, no issues at all. Under Karmic, I have the Intel cpu hog bug plus restart just hangs the machine after dropping out of Xorg.I've seen a lot of gripes about the Intel Xorg bug but no solutions - can this be sorted or do I go back to Jaunty?

BTW long-time Linux user, Ubuntu since 6.04.

Confused of Calverton

---

### Post by MrCheese on 2010-03-24
I fixed my problem - append "reboot=b" to the kernel options in the grub defaults, reboots now behave properly.

---

