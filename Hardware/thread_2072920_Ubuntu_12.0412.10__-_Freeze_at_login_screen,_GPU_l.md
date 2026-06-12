---
title: "Ubuntu 12.04/12.10  - Freeze at login screen, GPU lockup"
date: 2012-10-18
forum: Hardware
---

### Post by Selvinus on 2012-10-18
Hi guys!

Tried to run both these versions, but non of them works, getting the same problem every time. When I reach the login screen, the comp just locks immediately, mouse moving every 5 seconds. Sometimes I get "GPU lockup" after 15 seconds

Hardware:

i7 3770k @ 4.5ghz
Nvidia 580GTX
Intel 520 240GB SSD
Asus Sabertooth Z77

Any tips on how to solve this problem? Searched the whole internet but couldn't find a solution, seems like it is a gpu driver problem.. Anyway to update the drivers?

---

### Post by Bashing-om on 2012-10-18
Selvinus; Hi ! Welcome to the forum.

What results when booting with the "nomodeset" option ?
[INDENT]try'n to help <==BDQ

[/INDENT]

---

### Post by Selvinus on 2012-10-19
Excellent! Now I can access the desktop :)

Do I ned to run in nomodeset permanently?

EDIT: Everything works perfectly now. I installed the nvidia-current driver, solved the problem! Thanks for your help :)

---

