---
title: "PC goes to slow..."
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by Turk on 2005-09-24
I installed Ubuntu 4.1 on a 350 Mhz P II MMX 64MBRAM 6GB 8videoram(agp x2), int went very slow. Then I tested it with my Celeron 2600 256mbram(pc3200), onboard 64 mb graphics, it went just 20-40% faster but not yet comfortable, I cannot watch movies (mpeg/divx) without frequent lags, what's wrong? How can I resolve this?
Boot time : 2 minutes

---

### Post by pmjdebruijn on 2005-09-24
Hi,

Well please note that Ubuntu 4.10 is very outdated.

256MB RAM is a bit on the tight side...

You could check your /etc/X11/xorg.conf file for which graphics driver is being used, this could influence performance...

The movie issues, could be related to the codecs and not the CPU speed, I'd highly recommend trying to run the Breezy Live CD and compare the results...

Regards,
Pascal de Bruijn

---

### Post by heimo on 2005-09-24
[QUOTE=Turk] frequent lags [snip]
Boot time : 2 minutes[/QUOTE]
Both of these could be caused by DMA (direct memory access) being disabled. This was/is very common at least in Hoary, so it might have been with 4.10. In any case, you should try Hoary - Breezy will be out in about month. 256MB should be enough, but 64 is too low for Gnome. You could try xfce (alternative desktop / window manager) or you could even try another distribution on that slower computer - I'd definitely check [http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")

Instructions for enabling DMA:
[https://wiki.ubuntu.com/DMA]("https://wiki.ubuntu.com/DMA")

---

### Post by Turk on 2006-05-31
Now that I use Dapper Drake, the performance isn't different (Celeron 2600). I also see in the forum that other persons had problems with Celeron computers (also speed issue).
What can the problem be...

---

