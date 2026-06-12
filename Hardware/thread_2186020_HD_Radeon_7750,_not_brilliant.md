---
title: "HD Radeon 7750, not brilliant"
date: 2013-11-05
forum: Hardware
---

### Post by Kaijday on 2013-11-05
Currently on Gnome Ubuntu 13.10.

Have installed the 3.12 rc6 Kernal, with the latest Catalyst Beta driver. My internet is pretty poor at the moment, so i've not been able to try many games. But one I have tried is Paintball2, and I can only play it on 800x600 resolution. It crashes if I try anything higher than that.

Also tabs on Chrome do not display text, a problem with the FGLRX drivers.

Just a question, is it worth switching to the open source ones. Or maybe removing my Catalyst Beta and going back to a stable release?

> kai@kai-ubuntu:~$ lspci -nn | grep VGA01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde PRO [Radeon HD 7750] [1002:683f]




Thanks,
Kai

---

### Post by neigun on 2013-11-11
Hi Kai

I also have the 7750 and found that with the 3.12 kernel the card would cut out all the time.  Which version of the fglrx are you using because I found it pretty buggy in Ubuntu Gnome 13.04?

With the open source drivers I find the window decorations are unresponsive unless I right mouse click on the window or put my PC in to standby mode.


Neil

---

