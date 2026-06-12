---
title: "Sound over HDMI on the mobo ASUSM3N78-EM"
date: 2008-12-22
forum: Hardware
---

### Post by nite_man on 2008-12-22
Hi,

Is it possible to have sound on the HDMI output on the mobo  ASUSM3N78-EM?

TIA

---

### Post by Yellow Pasque on 2008-12-22
Probably not. Your best chance would be with the open-source radeonhd video driver (v1.2.4 or later), but unfortunately, that driver doesn't have video acceleration for 780G (because ATI's lawyers are grinches).

[http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=1)

---

### Post by nite_man on 2008-12-22
> **Temüjin said:**
> Probably not. Your best chance would be with the open-source radeonhd video driver (v1.2.4 or later), but unfortunately, that driver doesn't have video acceleration for 780G (because ATI's lawyers are grinches).

[http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=1)

Thanks for your replay, Temüjin. But physically it's possible? If it's just a matter of driver then sooner of later it'll be solved. When I tested a box with integrated ATI RadeonTM 1250 the /proc/asound/cards contained two cards: one for analog and SPDIF and another for HDMI. Now with M3N78-EM I see only one.

---

### Post by mr_raider on 2008-12-22
M3n78 uses an nvidia chipset. Some people have had success with the new version of alsamixer, and updating the nvidia drivers.

---

### Post by nite_man on 2008-12-23
> **mr_raider said:**
> M3n78 uses an nvidia chipset. Some people have had success with the new version of alsamixer, and updating the nvidia drivers.

Good point, mr_raider! I already installed the latest nVidia display drivers. So, I have to try the latest ALSA as well.

**UPDATE:** I can see info about analog audio only:
```

aplay -l
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)


```
Maybe it's a matter of kernel drivers and ALSA (I run Kubuntu 7.10)

---

### Post by mr_raider on 2008-12-24
I'm running 8.10 on a m3n78-vm. Using the default nvidia proprietary drivers (177.80). After upgrading alsa to 1.0.18a:

[http://ubuntuforums.org/showthread.php?t=962695&highlight=alsa+upgrade+script](http://ubuntuforums.org/showthread.php?t=962695&highlight=alsa+upgrade+script)

aplay -l now lists the HDMI device at 0.3.

Using the gnome sound properties tool I can set all the outputs to HDMI and I can get the test beep to play through HDMI.

I haven't figured out yet how to get MythTV, XBMC or any of the media players to work yet with audio HDMI.

---

### Post by nite_man on 2009-01-15
Found one useful [topic]("http://www.nvnews.net/vbulletin/showpost.php?p=1895025&postcount=85") on the nVidia forum which confirms that audio over HDMI works fine on the ASUSM3N78-EM. Also that ASLA wiki [page]("http://alsa.opensrc.org/index.php/DigitalOut") might be useful to configure and test sound over HDMI.

---

### Post by kxmas on 2009-04-26
It took while to get HDMI audio working on my M3N78-EM.  I think I might have misplaced the information in another thread.  Here's my post...

[http://ubuntuforums.org/showthread.php?t=1137876](http://ubuntuforums.org/showthread.php?t=1137876)

---

