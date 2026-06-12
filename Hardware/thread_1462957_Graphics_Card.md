---
title: "Graphics Card"
date: 2010-04-26
forum: Hardware
---

### Post by matt3206 on 2010-04-26
I recently switch from XP to Ubuntu, and I am unsure if all of my graphics drivers are up to date.

ACER Aspire one Pro
Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

Its a netbook and I am not playing anything really intense, but I was able to play EVE Online when I had XP. I am trying to full screen a game that I got from the software center, so it might just be the game won't fit to the screen ratio of the monitor. However I still want to make sure everything is up to date.

Thanks
PUG

---

### Post by Penguin Guy on 2010-04-26
Open [COLOR="Green"]System -> Administration -> Update Manager[/COLOR] and make sure your computer is up-to-date. If it isn't, install updates, reboot, and see if that fixes the problem. You may also want to take a look at the drivers you're using in [COLOR="green"]System -> Administration -> Hardware Drivers[/COLOR]. Hardware support on Linux usually isn't as good as on Windows.

---

### Post by matt3206 on 2010-04-26
Ok well I went to hardware drivers and it looks as if the only driver is the wireless broadcom driver nothing about the vga.

I know i need a **** ton of updates but i cant get them all now be ause of connection issues. Is there a way to find that particular update out  of the 200 MB size update.

---

### Post by klemes on 2010-04-26
Look for xserver-xorg and xserver-xorg-video-Intel packages updates but it wouldn't hurt if you got all xserver-related packages upgraded as well. :guitar:

---

### Post by matt3206 on 2010-04-26
> Look for xserver-xorg and xserver-xorg-video-Intel packages updates but it wouldn't hurt if you got all xserver-related packages upgraded as well.

Thanks I just upgraded all the xserver-xorg drivers and it fixed the full screen issue.

---

