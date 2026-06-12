---
title: "No sound after upgrading to 2.6.27-11!"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by TADsince1995 on 2009-02-18
Hello all,

I've just installed Ubuntu 8.10 x86_64 on my brand new PC. After the installation the sound worked perfectly on 2.6.27-7 (I have a Sound Blaster Audigy 2 card). So I did a big update and the system updated to 2.6.27-11 but the sound is completely mute. If I try to play a mp3 the system behaves as if the sound is working well and no error messages appears, but nothing goes out from my sound card, I put all volumes to 100% and from the sound control panel I tried both with pulse audio and alsa, but no way.

If I boot back to 2.6.27-7 the sound works again!

How can I have sound with 2.6.27-11 kernel?

Thank you in advance.

[EDIT] Sorry for the post, I found the solution: [http://ubuntuforums.org/showthread.php?t=1053764&highlight=sound+update](http://ubuntuforums.org/showthread.php?t=1053764&highlight=sound+update)

Thanks.

---

### Post by nzadLithium on 2009-02-20
I had this problem as well, in this bug report: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/310179](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/310179)

It's mentioned that during a kernel update the digital-analog switch was switched round, so you will have to go to the volume control, then go to the switches tab, on that list is Audigy Analog/Digital Output Jack: Uncheck that :D If it isn't on the switches tab (or switches tab doesn't exist) hit preferences go down to the bottom of the list and check 'Audigy Analog/Digital Output Jack' then press close. It should now show up on the switches tab :D

---

