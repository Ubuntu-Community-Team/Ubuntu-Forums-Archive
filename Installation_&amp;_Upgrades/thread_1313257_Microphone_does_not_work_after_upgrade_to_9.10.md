---
title: "Microphone does not work after upgrade to 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by egabriel on 2009-11-03
Hi, 
I upgraded my Fujitsu Siemens Amilo laptop from 9.04 to 9.10 and now my microphone does not work again: I can hear my voice in the speaker, but the capture (sound recording, skype) does not work.
I had the same problem with Jaunty as well, but I could solve them using the advices in the ubuntu forums (some additional lines in alsa-base.conf and removing pulseaudio)
Now the problem returned and I can't get rid of them.

I've googled the problem an a lot of people have similar issues. I've tried the different tips and tricks mentioned in the topics / bug reports below, but no success.
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://ubuntuforums.org/showthread.php?t=342681](http://ubuntuforums.org/showthread.php?t=342681)
[http://ubuntuforums.org/showthread.php?t=703456](http://ubuntuforums.org/showthread.php?t=703456)
[http://ubuntuforums.org/showthread.php?t=1028710](http://ubuntuforums.org/showthread.php?t=1028710)
[http://ubuntuforums.org/showthread.php?t=1284546](http://ubuntuforums.org/showthread.php?t=1284546)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/437192](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/437192)
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/400973](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/400973)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/458680](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/458680)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/391114](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/391114)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/434511](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/434511)

The laptop has an intel hda AC861 sound card.

The current state is, that I removed pulseaudio and I use alsa and the previous version (9.04) of gnome volume control and gnome sound properties and I use "options snd-hda-intel model=lenovo-nb0763 position_fix=1 enable=yes" in alsa-base.conf. The "Recording" tab of the HDA Intel (Alsa Mixer) device in Gnome Volume Control displays only two options: Capture and Digital, however in Jaunty I had also "Front Mic Capture".

Any ideas?

Thanks,
Endre

---

