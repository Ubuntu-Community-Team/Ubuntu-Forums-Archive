---
title: "IBM R50e laptop blank screen when trying to use LiveCD - Lucid"
date: 2010-07-13
forum: Hardware
---

### Post by Ray Hamilton on 2010-07-13
When I try to use the Lucid LiveCD I get a blank screen.  I have tried the option nomodeset with the same result.  This is the same whether I use an external CD (the internal one has given up) or from a USB (which boots fine on my desktop PC.) I have seen reference to fixes but these seem to assume that I have upgraded and give instructions to install things from the repository.  I have 9.04 and XP dual booting and do not want to upgrade, I want the option of having all three available.

---

### Post by jobr on 2010-07-13
Google is your freind :)

1) At the purple screen with a keyboard and stickfigure, press Enter to get to the menu.

2) Hit Enter to select your language, and then press F6 and then Esc.

3) Add "i915.modeset=1" after "quiet splash".

4) Press Enter to boot the LiveCD.

 [http://jachermocilla.blogspot.com/2010/05/ubuntu-1004-lts-on-my-ibm-thinkpad-r50e.html](http://jachermocilla.blogspot.com/2010/05/ubuntu-1004-lts-on-my-ibm-thinkpad-r50e.html)
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by Ray Hamilton on 2010-07-17
Yes, I "knew" that from Googling but thanks for your help in actually putting it into practice. I now have it installed. Now to find that thread where I can make this permanent

---

