---
title: "Computer lock up"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by vestudio on 2008-01-15
Ever since I installed Ubuntu (7.10) a few weeks ago on my laptop (Acer Aspire 9402WSMi) a few seeks ago, it totally freezes for 15-60 seconds every 5-15 minuets. I've tried running only specific programs to nail down a program issue. No luck. It seems to happen more often with internet based programs, but not necessarily. Any ideas?

1 more unrelated issue. When I use the scroll button on my mouse over the desktop it changes desktops (great feature!). But when I change to another user, it doesn't work.

Ok, last issue, for now... How do you get a 5 button mouse to work?

Mike H.

---

### Post by tgalati4 on 2008-01-15
Do you have dual boot?  Is the Windows partition mounted on the desktop?  If so, then unmount it and see if that improves the behavior.  There is an issue with having ntfs mounted partitions that can cause slow-downs.

5-button mouse requires editing /etc/X11/xorg.conf file.  Search the forums for what lines need to be modified.  Backup your existing file first.

>sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak

>sudo gedit /etc/X11/xorg.conf

---

### Post by vestudio on 2008-01-16
Thanks for the quick reply.

Ok tried that (had to turn root access on, log out, log in as root unmount, log out, log in as me - a bit of a pain each time I start the computer). It didn't work.

I noticed it's started happening in Windows too. Could it be bad RAM?

---

### Post by tgalati4 on 2008-01-16
Run memtest overnight.  You need 30 complete passes and no errors to validate RAM and rule it out as a problem.

---

### Post by vestudio on 2008-01-16
Ok. But, why overnight? I ran "memtest all 33" and it had a run time of 5 seconds (0 errors).

Anything else it could be? I'm beginning to think that this machine just doesn't like Linux. The windows problem could be that I took away it's D drive partition.

---

### Post by vestudio on 2008-01-16
My system specs are (laptop):
512 RAM DDR2 (reporting as 494.4)
Pentium "M" 735A, 1.7GHz
~35GB HD, 27.6GB free
~400MB swap
Built in 802.11 g/b
17" wide screen
Intel graphics media accelerator 900

---

### Post by tgalati4 on 2008-01-18
You need to run memtest86+ from either a Live CD or from the GRUB boot menu.  It will take several hours to get 30 passes.  Each pass is 10 different tests.

---

