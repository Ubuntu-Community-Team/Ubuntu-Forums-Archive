---
title: "Please help me get sleep to work!"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by SonicJMC on 2008-01-16
This is the third Distro of Ubuntu on which sleep fails no matter what I try. So, maybe y'all can help

Motherboard: MSI K9A Platinum
Video: ATi Radeon, I believe it's a 9800
CPU: AMD Anthlon X2
Mouse and Keyboard: Both connected via PS/2 ports
Networking: Onboard

Sleep issue in Windows...
BIOS Set to "S3" causes sleep to fail, but S1 works fine, and hibernate works fine.

Sleep issue in Ubuntu:
It never resumes from sleep, regardless if I have the BIOS set to S3 or S1, and it never resumes from Hibernate.

---

### Post by A_Lyle on 2008-01-16
There's a bug that stops sleep working with ATI cards, apparently. I installed uswsusp instead - it's not perfect but it does work...

---

### Post by SonicJMC on 2008-01-16
> **A_Lyle said:**
> There's a bug that stops sleep working with ATI cards, apparently. I installed uswsusp instead - it's not perfect but it does work...

What is uswsusp? Can you give me a walk through on getting that to work?

---

### Post by A_Lyle on 2008-01-16
I just posted it on my tutorial - scroll down to the bottom of the page:

[http://www.annelyle.com/geek/q1u_ubuntu.php](http://www.annelyle.com/geek/q1u_ubuntu.php)

Can't guarantee it'll work on completely different hardware, though!

P.S. you don't have to use vi - gedit or pico work just as well :)

---

