---
title: "No sound in headphones"
date: 2010-05-23
forum: Hardware
---

### Post by mcarrigan on 2010-05-23
I have a Dell Studio 15, only a few weeks old and just due installed Win7 and Ubuntu 10.4.  Everything seems to work great except my headphones.  Sound comes from the speakers fine and my microphone works fine in Skype.  But when I hookup my Logitech ClearChat headphones they don't work.  They work fine in Win7 but not Ubuntu.  I've gone thru all of the sound settings I can find under system but don't seem to be getting the right one, any ideas?

---

### Post by demo360 on 2010-07-24
Hi guys, I have a working workaround to get sound in the headphone jack.

sudo nano /etc/modprobe.d/alsa-base.conf

add the following line at the end of the file:

options snd-hda-intel model=dell-m6

reboot. Check the sound level of you headphone with alsamixer.

And that's it, you should have sound now. Enjoy

---

