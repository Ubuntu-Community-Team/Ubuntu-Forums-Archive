---
title: "no sound capture with RS780 azalia controller"
date: 2010-08-26
forum: Hardware
---

### Post by livram79 on 2010-08-26
My friend (he is a linux beginner) is using **Ubuntu 10.04** on a **Gateway md2614u** laptop, see here details [http://support.gateway.com/s/Mobile/2009/Ajax2/MD26/MD26sp2.shtml]("http://support.gateway.com/s/Mobile/2009/Ajax2/MD26/MD26sp2.shtml"). The playback sound works well but there is no sound capture. We tried all posibilities in ***Sound preferences*** but nothing works. The ATI driver in **Menu>Administration>Hardware Drivers** is installed and enabled. But as far as I can understand from internet search the problem is **/etc/X11/xorg.conf** file configuration. How to configure **xorg.conf**? what to write in that file?
Thanks.

---

### Post by livram79 on 2010-08-26
Solved by adding to the bottom of**/etc/modprobe.d/alsa-base.conf** file these lines:

[B][SIZE="4"]options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes[/SIZE][/B]

Reboot computer after adding the lines.

---

