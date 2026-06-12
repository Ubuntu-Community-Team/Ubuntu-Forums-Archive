---
title: "gnome volume control crashes when using oss"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by madubuntuer on 2006-03-26
Hi I use oss free but for some reason gnome-volume-control crashes when I start up the drivers.


(gnome-volume-control:15622): GnomeUI-WARNING **: While connecting to session ma nager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.


********************   WARNING   *******************************
Warning! gnome-volume-control uses ALSA emulation instead of the native OSS API
****************************************************************

snd_mixer_set_callback()
gnome-volume-control: relocation error: /usr/lib/gstreamer-0.8/libgstalsa.so: sy mbol snd_mixer_set_callback_private, version ALSA_0.9 not defined in file libaso und.so.2 with link time reference

also how do I load oss automatically because am sick of loading it via the terminal. The soundconf program complains about my system not having chkconfig scripts

---

### Post by SoulSmasher on 2008-04-10
i have the same issue, also alsa stopped to work , but oss works great in apps when selected.
for compatibility, how can we set either use oss when selected and alsa as default for apps (like login screen, tiny games etc which i can't hear a thing)

---

