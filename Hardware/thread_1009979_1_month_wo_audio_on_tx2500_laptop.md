---
title: "1 month w/o audio on tx2500 laptop"
date: 2008-12-13
forum: Hardware
---

### Post by haxx on 2008-12-13
hey guys.

Ive done all i know (not much compared to the tux gods). to no avail as i still have only one problem on my nessesary list of things that must work.

The audio makes nodda for sound. everything i try to look at in xubuntu 8.1 says its installed fine and working, volumes are not muted.

Ive stuck through with significant problems before such as the well known BCM43xx problems before the restricted drivers came out and eventually got through it with some big help on forums. Im greatly hoping someone out there can stick it out and help me figure this one out.

I have a feeling that the issue is somehow related to the HD3200 ati chips. this due to the fact that almost every issue ive had is related to it. (BartPE driver, XP sata driver is related to apparently.) oh and not a distro out there has worked that ive tried.

System info as follows.
-HP tx2517ca convertable tablet.
-ati hd 3200
-sata hd
-currently xubuntu 8.1 (have tried all 3 major ubu's) and vista home premium. (incredibly vlited so dont expect stuff to be there if u need me in vista)

---

### Post by Favux on 2008-12-17
Hi haxx,

First you need to go to System>Preferences>Volume Control or right click on icon at top right and Open volume control. Make sure all the volume sliders are up, including PCM, Intrepid can accidentally mute you on install.

To your /etc/modprobe.d/alsa-base file try adding the following line:

options snd-hda-intel index=0 model=toshiba position_fix=1

If that doesn't work you might also try:
options snd-hda-intel index=0 model=acer

---

