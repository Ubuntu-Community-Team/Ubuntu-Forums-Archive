---
title: "Laptop soundcard problems..."
date: 2009-03-12
forum: Hardware
---

### Post by Admiral Nesquick on 2009-03-12
Hey guys,

I'm using Ubuntu for a couple of months now ( and i love it :D ). But, i still have this one problem. It"s quiet, to quiet... I have a headphone that i can connect to my laptop using a headphone jack. But this doesn't work. I know that my sound card is working because when i plug in a USB headphone and reboot i hear the jungle welcome jingle. But, my USB headphone is really uncomfortable and my headphone connected to jacks sits a lot better. I have a Realtek high definition integrated sound card. I have already tried **sudo dpkg-reconfigure linux-sound-base** and have tried Alsa, PulseAudio and OSS. But unfortunately this doesn't seem to work. 

Here is the output of **lspci | grep -i audio**

> 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller

Can someone be so kind to help this Ubuntu newbie out ? Thank you very much in advance. :guitar:

---

### Post by Chemical Imbalance on 2009-03-12
Same problem here with this integrated soundcard:
 
nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)

---

### Post by khelben1979 on 2009-03-12
Take a look at the settings in [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer").

You might need to adjust some of the bars a bit. If this doesn't help, then I suspect that you need to reinstall the ALSA sound system and you may haveto do it the hard way... compile up ALSA from source code and install using a Ubuntu script which can be found [here]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+script").

---

### Post by Chemical Imbalance on 2009-03-12
> **khelben1979 said:**
> Take a look at the settings in [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer").

You might need to adjust some of the bars a bit. If this doesn't help, then I suspect that you need to reinstall the ALSA sound system and you may haveto do it the hard way... compile up ALSA from source code and install using a Ubuntu script which can be found [here]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+script").

It had nothing to do with volume levels or the mixer.  It had to do with the kernel loading the module for the device.  Upgrading to Jaunty fixes the problem (for me).

Admiral Nesquick, the problem seems to be fixed in the developmental Jaunty release.
It is not recommended you update on a production machine (it is unstable and alpha quality) but if you really are desperate this will upgrade you to Jaunty and possibly fix your sound issue (it has for me):
```
sudo update-manager -d 
```
then click the button that mentions updating to Jaunty.
Again this is a sloppy fix, but it works for me.

---

