---
title: "NVidia Geforce 210 (pny) audio over HDMI lead - HELP"
date: 2010-08-09
forum: Hardware
---

### Post by andy_cowman on 2010-08-09
Hi all

I have looked over the forums, and the nvidia site and have made some progress - well compared to where I started!

The situation is:

P4 3.2 ghz, 2gb ram and an ASROCK board with onboard sound and gfx

I have disabled the audio from the Mainboard
I have a fresh install of 10.04 with all updates installed
I have removed Alsa from apt and recompiled the latest source (utils, tools, the lot)
Nvidia drivers from the restricted hardware manager 

aplay - l now only shows ONE of the HDMI Nvidia outputs since I got the others hidden by adding a line to the sound-base.conf file and it is the right one I believe. 

alsamixer sees it as the sound card and I unmuted it.

Sound from preferences menu sees it as my sound card and says all is good, Aplay test doesn't error, VLC sees it and seems happy to use it.

All great, it looks like everything works only there is no sound. Not so much as a beep!! from anything.

It all worked fine in Windows 7 so I know the hardware can do it. I have no more ideas and can not find any other guides to follow!! Does anyone have any ideas!?

Many thanks

Andy

---

### Post by andy_cowman on 2010-08-09
Trying a fresh install of MythUbuntu .... since I also want to use my Hauppage HVR 1110. So far it won't tune any channels despite saying that the card is there and usable and still no sound. 

I will give it one more night then its back to Windows 7 until the hardware is supported properly. A shame as I really liked the updates to the style and usability across the rest of 10.04.

If anyone has any ideas please let me know.

---

### Post by RosscoAU on 2010-08-10
> **andy_cowman said:**
> Trying a fresh install of MythUbuntu .... since I also want to use my Hauppage HVR 1110. So far it won't tune any channels despite saying that the card is there and usable and still no sound. 

I will give it one more night then its back to Windows 7 until the hardware is supported properly. A shame as I really liked the updates to the style and usability across the rest of 10.04.

If anyone has any ideas please let me know.

With the GF210 as I believe you will have already done you will need to download from source, compile and install ALSA 1.0.23 to get the support for the card.

The for the moment remove the .asoundrc configuration you have set up as it may not be correct (and TBH is not needed).  Running ALSA mixer should allow you to select the card and you should have 4 HDMI devices all of them muted.  If you unmute all four of them then you should get sound.

With the Tuner I don't have any experience with that model but this may be of help [http://forums.debian.net/viewtopic.php?p=130129](http://forums.debian.net/viewtopic.php?p=130129)

HTH

Rossco

---

