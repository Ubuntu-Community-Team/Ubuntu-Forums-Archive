---
title: "Missing sound device on Zepto 6625WD"
date: 2009-12-13
forum: Hardware
---

### Post by DarkFox.DK on 2009-12-13
Just after I installed Karmic on my Zepto, the sound card showed up fine in the hardware tab of sound preferences.

But after a reboot, it wasn't there any more.

I can get sound working in boxee, via spdif some times. It seems really random if it works or not, when I reboot.

I have tried following some guides from archived threads, but to no avail.

Latest I tried this one, using alsa-driver-1.0.21, alsa-lib-1.0.21a and alsa-utils-1.0.21: [http://ubuntuforums.org/attachment.php?attachmentid=56177&d=1200150008](http://ubuntuforums.org/attachment.php?attachmentid=56177&d=1200150008)

replacing "model=toshiba" with "model=zepto", as per the guide that worked for me on 8.10.

Where should I go from here?

---

### Post by barras on 2009-12-18
I have same problem

---

### Post by MONK_DUCK on 2010-01-24
Likewise same problem I can only see the internal speaker and nothing else.

Ok Fixed mine by using there instructions:-

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

In the end all that was required was to do this:-

sudo nano /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=zepto

If anyone has any thought how this fix could be sent upstream........?

---

