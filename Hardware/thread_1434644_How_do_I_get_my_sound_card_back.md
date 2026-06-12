---
title: "How do I get my sound card back"
date: 2010-03-20
forum: Hardware
---

### Post by Fitch on 2010-03-20
Just installed OSS and alsa drivers to get vgetty working.
Now I have no sound card.  The Nvidia AC97 onboard sound is not recognised.
The 'configure devices' part of volume control, sound preferences is empty.

I have re installed all of alsa.  
installed [oss-linux-v4.2-2002]("http://www.4front-tech.com/release/oss-linux-v4.2-2002-i686.tar.bz2")
installed the AC97 driver for Linux,

The last one did come up with below, but kept on going.

p: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1

I continues, and at the very end say it's succeeded and even plays something, don't know what 'cos I can't hear it.
Alsa player comes up and 'plays' any file I open, but nothing comes out of the speakers, and sound preferences still shows no card on the hardware list.  The output tab just shows "Dummy output"
Still no sound card
What next?

---

### Post by IcarusR on 2010-03-21
There are several threads on this subject on the forum with several fixes.
I believe this is a problem mainly for Intel sound chip.
Disable any winmodem modules was one, don't remember others.
Search for 'dummy' should get you there with a bit of reading.

---

### Post by Fitch on 2010-03-23
Looks like my hard drive is faulty..
Have replaced it and reloaded Ubuntu
Lets see what happens...

---

### Post by Fitch on 2010-04-09
Yup! definitely the hard drive..

---

