---
title: "boot freezes, ndiswrapper?"
date: 2008-09-01
forum: General Help
---

### Post by rikard99 on 2008-09-01
Hi,

Background
----------
I had been using ubuntu for about half a year when I installed a wireless card (Trendnet TEW-423PI C1.0R). This is detected by lspci but the drivers appears to be bad so I do not get a "wlan0" entry at ifconfig. I followed the instructions for installing a Windows driver using ndiswrapper. I downloaded the latest version of both ndiswrapper and driver, compiled ndiswrapper and installed with modprobe etc. OK, this did not work, but here comes the nasty part>

The problem
-----------
Ubuntu gets stuck on the splash screen at boot up. It is completely non responsive. If I do <Ctrl>+<Alt>+<F1> before it gets stuck I get some error messages (will copy by hand tonight). Sometimes I instead get a message which goes something like "CPU#0 timed out after 11s", repeated infinite times. From there I can <Ctrl>+<Alt>+<Del> and then <Alt>+<F6> to get the "tty" login prompt. I can access / but not change the files, even with sudo, since everything is mounted as read only. (I think the reason why I cannot startx is due to it cannot create the .Xauthority file). The situation is the same if I try with the recovery mode from Grub. I will try with a Live CD next.

What I want
-----------
How do I restore the Ubuntu installation to what it was before messing it up with ndiswrapper?

Specs
-----
I am using the latest official generic kernel on Ubuntu 8.04, AMD 64x2, ASUS A8N-SLI Premium, and / is mounted on sda3, Vista64 on sda1, boot on sda2. Btw, Vista is perfectly fine, I am writing this using the said wireless card on the same machine.

I am grateful for any help I get.

---

