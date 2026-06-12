---
title: "Intel:Low Volume-mixer correct/asound pre-amp not added to mixer/hda-analyzer crash"
date: 2014-01-05
forum: Hardware
---

### Post by ronniepinsky on 2014-01-05
This problem has been present on the last three computers I have bought recently, all popular models that are still in stores now.  Asus Transformer TF101, HP Split X2, and now Lenovo Yoga.

1. The first way would be to simply max all volume controls within the graphic mixer or alsamixer - this does not bring the volume to an acceptable level
[https://wiki.ubuntu.com/Audio/CheckForMutedSpeakerVolume](https://wiki.ubuntu.com/Audio/CheckForMutedSpeakerVolume)

2. The second way would be to use the "softvol" alsa plugin to add a control that when chosen, boosts the PCM gain - this control is not added despite several different attempts at asound.conf / .asoundrc .
[https://bbs.archlinux.org/viewtopic.php?pid=1090109](https://bbs.archlinux.org/viewtopic.php?pid=1090109)

3. The third way would be to use hda-analyzer to change the gain directly at the sound "nodes" - hda-analyzer crashes with "ValueError: wrong proc file format (unknown dig1 bit 'KAE')"
[https://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg29456.html](https://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg29456.html)

This explains why:
[http://webcache.googleusercontent.com/search?hl=en&q=cache:6HtGH8mH3kcJ:http://comments.gmane.org/gmane.linux.alsa.devel/105321%2Bhda-analyzer+wrong+proc+file+format&gbv=1&ct=clnk](http://webcache.googleusercontent.com/search?hl=en&q=cache:6HtGH8mH3kcJ:http://comments.gmane.org/gmane.linux.alsa.devel/105321%2Bhda-analyzer+wrong+proc+file+format&gbv=1&ct=clnk)

This is one person's workaround:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/950494](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/950494)

Unfortunately, the bug I am seeing cannot be worked around with such a simple edit, and will require a thorough change by someone familiar with the code.  Is there any hope for me if I want to listen at greater than whisper volume?

---

### Post by ronniepinsky on 2014-01-06
I am still having this problem and wanted to bring it back to the the top.  Is there perhaps a Kernel that is supposed to work better with this hardware?  I thought Intel hardware was well supported in Linux.  I have never had a low volume or any sound issue on any of my AMD PCs!

---

