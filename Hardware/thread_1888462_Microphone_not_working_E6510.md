---
title: "Microphone not working E6510"
date: 2011-11-29
forum: Hardware
---

### Post by buntu_hugenewbie11 on 2011-11-29
I cannot get the microphone working on my Dell E6510.
Sound works otherwise just no internal microphone.

In my /etc/modprobe.d/alsa-base.conf 
I added the following:
options snd-hda-intel model=dell-s14

And still I get nothing.

In terms of the sound card KDE thinks I have it is the following:
cat /proc/asound/card0/codec* | grep Codec
Codec: IDT 92HD81B1C5

If somebody knows how to get this working please help.

---

### Post by searchfgold6789 on 2011-11-29
Try looking at it with Phonon (System Settings > Multimedia > Phonon)

---

### Post by buntu_hugenewbie11 on 2011-11-29
I have nothing that says phonon though according to apt-get it is installed.
According to lspci | grep Audio
I have the following audio devices:

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

---

### Post by searchfgold6789 on 2011-11-30
You can select the default sound card with:```
alsamixer
```

---

### Post by buntu_hugenewbie11 on 2011-11-30
I have selected the Intel card and the internal microphone still does not work. Actually since it was the default it was selected anyway. There must be some way to get the internal microphone working.

---

### Post by MoreOrLess on 2011-11-30
From your post history, it looks like you're still using Lucid. The bug was fixed in Maverick: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605047](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605047)

---

### Post by buntu_hugenewbie11 on 2011-11-30
Yes I am using lucid which is the latest LTS version.
Can I fix it in lucid?

---

### Post by MoreOrLess on 2011-11-30
The easiest way is using this PPA, but it looks like the package for the latest Lucid driver is a bit outdated:  [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

---

### Post by buntu_hugenewbie11 on 2011-12-20
Is there a way to get updated drivers for Lucid?
I tried using pulse, but that was disaster.
Currently I have to switch to Windows anytime I need the mic, which ends up being quite a hassle.
Ideas other than moving away from LTS?

---

### Post by MoreOrLess on 2011-12-20
You can compile your own: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)
Install libsdl1.2-dev first.

---

### Post by THOUCUSA on 2012-05-30
HERES WHAT WORKED 4ME...I I WENT TO KUBUNTU PACKAGEKIT AND INSTALLED <<PULSAUDIO>> AND SET MY USB MIC EXTERNAL MIC AS PREFERED..that kmix and phonon  is NOT compatible with my external usb mic..I HAD BEEN SEARCHING FOR DAYS 4 A SOLUTION.

---

