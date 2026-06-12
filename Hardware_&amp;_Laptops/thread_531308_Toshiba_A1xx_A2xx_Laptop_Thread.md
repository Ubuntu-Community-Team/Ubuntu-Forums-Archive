---
title: "Toshiba A1xx A2xx Laptop Thread"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by stchman on 2007-08-21
Hello all, I have been getting a lot of questions about how I got Feisty working on my laptop and I figured that I would start a thread about it.

I currently own a Toshiba A135-S2246 laptop and have been happily running Feisty on it for some time.

Laptop specs:

Intel Celeron M 1.73GHz
1 GB RAM (512MB initially)
ATI Radeon Xpress 200M
Atheros 5006EG Wireless card
Realtek 8139 Ethernet
15.4 Widescreen LCD
DVD/CDRW

For the most part everything worked out of the box with Feisty with these exceptions:

SB450 Audio
ATI Radeon Xpress 200M
56K modem (I have never tested)
Logoff black screen

The Atheros card had the restricted drivers enabled by default.

I was able to get the audio working by doing the following:

```
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=3stack

sudo gedit /etc/modprobe.d/alsa-base
# Add the following line at the very end of the file
options snd-hda-intel probe_mask=8 model=3stack
```

The enabled the restricted driver to support the Radeon Xpress 200M

When I would logoff I would get a black screen and this was the fix:

```
sudo gedit /etc/X11/gdm/gdm.conf-custom
# Add the follwing in the [daemon] section

AlwaysRestartServer=true
```

The laptop I have is somewhat basic but it suits my needs.  I would like it if other members posted their experiences and how they got their devices working.

I know that in other Toshiba laptops owners have not been able to get the media reader and web cam working using Feisty.

---

