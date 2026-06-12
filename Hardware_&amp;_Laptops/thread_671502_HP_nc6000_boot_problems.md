---
title: "HP nc6000 boot problems"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by OpenSys on 2008-01-18
Hello community,
I have recently installed ubuntu 7.10 on my laptop, all works good.
I am needed to install slackware in the same laptop.
 I now have tree OS booting correcty (windows, slackware and ubuntu).
At now the boot loader its the lilo from slackware, but when boots the ubuntu, i do not see the running kernel console booting, I see only a blank screen with a blink cursor at the top  left of the screen.
The system do not boot without I press ctrl+f1 and press enter. After this the laptop runs, with the same blank screen, then shows the login screen and all work good.

Tanks for you time.

---

### Post by OpenSys on 2008-01-19
Found some above, the kernel parameter "vga=" is blanking the screen.

What is the default vga value em ubuntu kernel ?

---

