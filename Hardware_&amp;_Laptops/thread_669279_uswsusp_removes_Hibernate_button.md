---
title: "uswsusp removes Hibernate button"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by A_Lyle on 2008-01-16
Just finished researching suspend/hibernate issues and managed to achieve a partial solution...

Hardware: Samsung Q1U UMPC

* Intel 800MHz A110 processor
* Intel GMA 950 graphics chip
* 1Gb RAM

I set up a 1GB swap partition - the hard drive isn't huge, so I thought that would be adequate.

Suspend and hibernate just didn't work out of the box, or rather resume didn't - I had the infamous 'black screen of death' problem. So I installed uswsusp, but it complained that it couldn't use the swap space. After a bit more research I tried changing /etc/uswsusp.conf to use the device address instead of the UUID string, ran sudo dpkg-reconfigure uswsusp and went through the configuration process accepting the defaults. I also replaced the HAL scripts with simple shell scripts to call s2disk and s2both.

I now have something resembling a working suspend/hibernate, with two provisos:

* I now have no 'Hibernate' button!

* On the initial suspend, I got sensible-looking command-line output, but on subsequent occasions I get screen distortions (coloured chequer-board patterns), though the process takes the same amount of time and seems to work OK

Compared to no suspend at all, it's a big improvement, but I was wondering if there were ways to fix the above?

TIA

---

