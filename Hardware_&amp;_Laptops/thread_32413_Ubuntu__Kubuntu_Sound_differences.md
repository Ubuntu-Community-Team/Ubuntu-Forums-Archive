---
title: "Ubuntu / Kubuntu Sound differences?"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by mortram on 2005-05-07
I've installed both Ubuntu and Kubuntu on my system and both detect and use my M-Audio Quattro USB.  However the sound is clear with Kubuntu and grainy/distorted on Ubuntu.  Is there a reason the two would be different?  I'm assuming they both use ALSA, so is there a configuration file in Ubuntu that I can edit in order to get clean sound as it is in Kubuntu?

Perhaps it's a problem with the default buffer size?  What would be the configuration files to look at?

---

### Post by JonahRowley on 2005-05-08
KDE and Gnome use different sound servers.  KDE uses *arts* and Gnome uses *esd*.  I've had bad luck with both, but as for audio quality, I've had better luck with arts.  This may be what's happening here.

---

### Post by mortram on 2005-05-09
is it possible to use *arts* within Gnome?

Ubuntu is actually the only distribution I've used that hasn't properly setup the card... it was automatically configured and sounded clear with Fedora, Mepis, Kubuntu, and Knoppix.  This leads me to believe it should be a simple configuration change...

or not?

---

### Post by mortram on 2005-05-10
I just found this tutorial on switching to ALSA for sound... followed the instructions verbatim and it worked great!  Sound is *crystal clear* now!

---

### Post by mortram on 2005-05-10
i mean, THIS tutorial: [http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

---

