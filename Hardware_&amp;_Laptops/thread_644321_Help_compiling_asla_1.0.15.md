---
title: "Help compiling asla 1.0.15"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by parvenu on 2007-12-18
I'm very new to linux and was trying to fix a microphone problem. Someone pointed me in the direction to compile new alsa drivers following this page: [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

I got to the Manually Specify Module Parameters section and I couldn't figure out anything beyond that.

Now my sound doesn't work and if i click on the volume control, it says "No volume control GStreamer plugins and/or devices found."

I'm using Gutsy on a Thinkpad T61 with the HDA Intel ICH8 Family audio controller.

Can anyone help??

---

### Post by TheLions on 2007-12-20
i know this is old version but it has included installer

[ftp://202.65.194.212/pc/audio/realtek-linux-audiopack-4.07a.tar.bz2]("ftp://202.65.194.212/pc/audio/realtek-linux-audiopack-4.07a.tar.bz2")

just kick terminal 

```
sudo su

cd /unpackedpath/

  ./install
```

---

### Post by parvenu on 2007-12-20
thanks.
i reverted back to 1.0.14 following another thread.
does anyone know how to upgrade to 1.0.15 or is that not necessary to get external microphones working?

---

