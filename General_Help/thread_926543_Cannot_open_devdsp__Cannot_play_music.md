---
title: "Cannot open /dev/dsp | Cannot play music"
date: 2008-09-22
forum: General Help
---

### Post by Gizkaguy on 2008-09-22
Hello! I think these two problems are related, which is why I grouped them together. If they are separate, then I apologize.

Whenever I try to run flite or festival, then I get the following error:

oss_audio: failed to open audio device /dev/dsp

I have noticed that, on the first try after installing, flite works. As soon as I quite the terminal / reboot / do anything else, flite stops working. Festival never works.

A (I think) related issue is that nothing (totem, rythmbox, etc) can play music. There is no sound, and the slider showing doesn't move. I have all the plug ins required installed, I believe.

I have googled some and didn't come up with anything good. Many posts mention killing esd, and many mention installing esd. I do not have it installed.

If anyone needs any additional info, please tell me.

---

### Post by ashmew2 on 2008-09-23
Which Version are you using ? Hardy ?

---

### Post by jlanse on 2008-11-22
[http://wiki.archlinux.org/index.php/Festival](http://wiki.archlinux.org/index.php/Festival)

Debugging

If festival returns the following error message:

Linux: can't open /dev/dsp

Switch to ALSA output by adding these lines to the end of your .festivalrc file, or to /usr/share/festival/festival.scm (source):

(Parameter.set 'Audio_Method 'Audio_Command)
(Parameter.set 'Audio_Command "aplay -q -c 1 -t raw -f s16 -r $SR $FILE")

---

