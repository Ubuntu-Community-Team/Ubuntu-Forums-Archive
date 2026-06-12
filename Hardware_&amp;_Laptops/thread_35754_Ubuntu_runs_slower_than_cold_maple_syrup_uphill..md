---
title: "Ubuntu runs slower than cold maple syrup uphill."
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by ZarathustraDK on 2005-05-20
Not so long ago I installed Hoary on my stationary powerhouse with (almost) no problems at all, have it today, love it and it stays.

Next I tried to "convert" my girlfriend to install it on her laptop (an IBM Thinkpad a22m 700 mHz 128 mb ram). Installed hoary with 128 mb swap, no problems installing or rebooting. The problem is that execution of apps (even tiny ones like gedit) is painstakingly slow, not just slow to the point og annoyance but slow to the point of unuseability; it effectively hangs, but judging from the noises it makes it's working hard.

What separates this installation from an ordinary (clean hd and english) installation is : chinese language, and 4 primary partitions on the hard drive (1. Windows 2. Data 3. /swap 4. ubuntu)

Any suggestions? It's driving me nuts. ](*,)

Help herd the heathens into the linux-fold  :smile:

---

### Post by wulf on 2005-05-20
Run some system monitoring software (even *top* on the CLI would do) - is there a program hogging all the CPU time or sucking up all the memory? My desktop machine certainly got a lot more sprightly when I moved from 128MB to 384MB.

Wulf

---

### Post by mr_ed on 2005-05-20
If it's got 128MB of RAM, I would seriously consider trying XFCE on it (and/or try Kubuntu for kicks.  It runs faster on my machine than GNOME did).

This post was not meant to be a troll.  ;)

---

### Post by eric222 on 2005-05-21
On my laptop, I see the memory usage at around 200Mb on a clean boot.  Start a few apps and now I am at 400MB.  I would say with 128MB RAM you should set up a 500MB swap.

Eric

---

