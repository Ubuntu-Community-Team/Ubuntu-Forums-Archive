---
title: "No sound after installing ALSA 1.0.24 on Ubuntu 11.04"
date: 2011-05-22
forum: Hardware
---

### Post by sag0th on 2011-05-22
Hi Community :)

A little problem here:

I don't have sound after installing ALSA 1.0.24 on the latest Ubuntu 11.04...
The reason for upgrading ALSA was that previously this was fixing my microphone problems on Ubuntu 10.04. So after clean install of 11.04 my mic wasn't working again so I decided to try again ALSA upgrade. I was following this guide: 

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

but I downloaded version 1.0.24 from alsa-project.org.

ALSA driver / libs / utils build went fine.
alsaconf recognized my sound as:
hda-intel VIA Technologies, Inc. VT1708/A

...and there was no sound at all. There is no hardware in Sound preferences.

I followed this guide for Troubleshooting:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
but again no sound.

I don't have any idea how to proceed and your help will be much appreciated...

btw Previously I installed PulseAudio Device Chooser. Is it possible to break the sound somehow with the new alsa??

---

### Post by sag0th on 2011-05-22
> **sag0th said:**
> 
I followed this guide for Troubleshooting:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
but again no sound.


Forgot to mention that I didn't follow the guide 100% because some of the paths for the snd modules are different in 11.04... (/lib/modules/2.6.38-xx-generic/ubuntu/media)

---

### Post by Lateefah-ubuntoo on 2011-08-21
Hello!


Did you solve the problem? At the moment I am updating alsa from the same reason and now I am afraid I will lose even the sound :(

---

