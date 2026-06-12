---
title: "ram test program"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by shizow on 2005-07-15
i have a new ibm t43
but the laptop freezes out completely sporadically

i dont find something in syslog

how can i make a ram test

---

### Post by az on 2005-07-15
Hit escape when you boot to reveal the grub menu.  Pick memtest86.  Let it run for a few hours.

---

### Post by avelldiroll on 2005-07-15
Choose memtest86 in grub when you reboot (or choose this option while booting a knoppix cd).
The different tests will start automatically.
If nothing appears in the bottom half of your screen, your memory chip is ok.
If some errors are reported, then ... well ... change your ram.

For more info see :
[http://www.memtest86.com](http://www.memtest86.com) 

Cheers

---

### Post by Chris P. Bacon on 2008-01-02
If you memtest the ram from a cd, how long will it have to run before i know the rams fine?

---

