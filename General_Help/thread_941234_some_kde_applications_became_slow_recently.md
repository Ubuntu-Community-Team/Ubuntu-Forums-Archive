---
title: "some kde applications became slow recently"
date: 2008-10-07
forum: General Help
---

### Post by bricedebrignaisplage on 2008-10-07
Amarok, kstars, kate... for all of them the GUI became very slow. up to 5 seconds delay in amarok, a bit less in kate. animation in kstars is terrible. I guess that I must have changed a kde configuration setting somewhere... I tried to reinstall those apps but it doesn't do. Any suggestion? I know that there is no much info here to help, but that's all I got.

Using Kubuntu 8.04, KDE 3.5, on i386 with plenty of ram. Hardware is working fine, since under debian I don't have any problem.

---

### Post by bricedebrignaisplage on 2008-10-08
Well, after trying a few things I figured out that this slowness is due to my xserver config. I am using a nvidia card with TV-out ability (GeForce4 MX 440 with AGP8X). It works fine in cloned mode, but when I configure it to have 2 separate x screens with xinerama it causes some apps to slow down. And the strange thing is that it seems to be only with KDE applications...

---

### Post by sergiodlc on 2008-10-20
> **bricedebrignaisplage said:**
> Well, after trying a few things I figured out that this slowness is due to my xserver config. I am using a nvidia card with TV-out ability (GeForce4 MX 440 with AGP8X). It works fine in cloned mode, but when I configure it to have 2 separate x screens with xinerama it causes some apps to slow down. And the strange thing is that it seems to be only with KDE applications...

I have the same problem, but I'm a Gnome user. I also remember that I unsuccessfully tried to set up two screens some time around the starting of the failure.

---

