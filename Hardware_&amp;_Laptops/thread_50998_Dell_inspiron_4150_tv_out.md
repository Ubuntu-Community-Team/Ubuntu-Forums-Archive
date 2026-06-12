---
title: "Dell inspiron 4150 tv out"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by Ampersand on 2005-07-22
Hi
Has anyone managed to get the svideo out on an inspiron 4150 (using ATI mobility radeon 7500 graphics) working under Linux? I've looked around, but most howtos seem to be about the 9000 series.
Thanks
Richard

---

### Post by s_p_a_r_k_y on 2005-07-22
[QUOTE=Ampersand]Hi
Has anyone managed to get the svideo out on an inspiron 4150 (using ATI mobility radeon 7500 graphics) working under Linux? I've looked around, but most howtos seem to be about the 9000 series.
Thanks
Richard[/QUOTE]
I have not tried it as I don't have a TV, but the best way is probably to have fgrlxconfig generate the xorg conf file for you. It does a pretty good job (it did my dual monitor setup). Always backup your working file. I keep them in /etc/X11/xorg.conf.ati_single_monitor /etc/X11/xorg.conf.ati_dual_monitor and /etc/X11/xorg.conf.composite_on

So I can quickly switch between the config files.

An important thing I've read is that the svideo cable and TV should be on before you boot your computer. ALSO don't reboot it, turn it off then turn it back on. You will probably be able to watch linux boot on the TV but until you get X setup with fglrxconfig (then modify and add your own changes) the TV probably wont be able to show you the X screen but garbage.

Hope it helps

---

### Post by Ampersand on 2005-07-22
Nothing comes up on the tv during boot. I tried the fglrx config, but X only seems to start when I'm using the ati or radeon drivers.
Richard

---

