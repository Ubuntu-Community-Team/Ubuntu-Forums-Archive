---
title: "X-Fi Working w/out ALSA or OSS?"
date: 2009-12-15
forum: Hardware
---

### Post by lashelle on 2009-12-15
Creative X-Fi Platinum

After installing Ubuntu 9.10, there was no sound.

I followed the OSS documentation:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

As soon as I removed PulseAudio, I noticed I was getting system sounds (from pressing delete in terminal). I continued with the guide and backlisted/removed ALSA and the sounds still worked. As soon as I installed OSS, there was no sound again. I tried both the DEB and the Murcurial source and no luck.

I removed OSS with...
```
sudo apt-get remove oss-linux
```...and sounds started working again.

So now I'm confused... I've got sound, but I don't have OSS or ALSA installed. It's not a big deal now, but later I'll want to play with the sound driver and I may not even have one.

Does anybody know what to do?

---

### Post by Pedro82 on 2009-12-15
I'm a newbie into this, but
if I'm not wrong, ubuntu 9.10 works with the Pulse Audio server. Try to check it out.
This link might help you....

[http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio)

I don't know if you can install it without installing OSS or ALSA, or if it will work.

---

### Post by DaVince21 on 2009-12-15
ALSA can't be remove unless you recompile the kernel without the ALSA module. So unless you did that, you probably still have ALSA (with PulseAudio as the mixer on top of it, if you're not using Xubuntu (which leaves out PA)).

---

### Post by Webe12 on 2009-12-24
I too had problems using Alsa or Pulseaudio.  But I had success with OSS.  Try these links....

[http://www.4front-tech.com/wiki/inde...ions_for_OSSv4]("http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4")

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

It is not perfect and not the most friendly but it works.  I am learning more all the time about OSS. The audio will just drop at times. But can be regained by pausing and restarting again, most of the time. Sometimes I have to move the cursor back and forth until the sound returns.

---

