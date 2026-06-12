---
title: "No Sound"
date: 2009-09-20
forum: Hardware
---

### Post by cylux on 2009-09-20
Hey guys

This is a fresh install of latest stable Ubuntu release. This is an HP dv6 and everything works tip top except for the sound.

Gnome default mixer is detecting all the devices but for some reason I can't hear any sound- any ideas?

I've done the basics, alsamixer is unmuted etc. etc.

---

### Post by dv3500ea on 2009-09-20
Try this fix:
 	Code:
 	sudo gedit /etc/modprobe.d/alsa-base.conf 
into a terminal and then adding:
 	Code:
 	options snd-hda-intel model=hp-m4 enable_msi=1 
to the end of the file.

There are plenty of threads on sound issues - you probably should have searched before posting this.

---

