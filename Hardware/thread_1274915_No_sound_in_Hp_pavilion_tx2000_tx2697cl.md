---
title: "No sound in Hp pavilion tx2000 tx2697cl"
date: 2009-09-25
forum: Hardware
---

### Post by faedpi on 2009-09-25
I cant play any sound in my laptop, the speakers are Altec Lansing. I am in version 9.04 Jaunty
Any idea? 
Thanks

---

### Post by Favux on 2009-09-25
Hi faedpi,

Welcome to Ubuntu Forums!

The following line works for TX2500 users:
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```
Add it to the end of the file "alsa-base.conf" at "/etc/modprobe.d/". Don't worry that it says Toshiba.

To edit it enter in a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf

```
Save, close, and reboot.

Also check to see if the mixer is muted. Make sure the sliders (including PCM) are up.

I hope this is helpful.

---

### Post by faedpi on 2009-10-11
Wow, thank you very much. Couldn't have been easier! 

Thanks, 
Faedpi

---

### Post by Favux on 2009-10-11
Hi faedpi,

You're welcome.  Glad it worked for you.

---

### Post by alving on 2009-10-23
hi all

i have an old toshiba satellite pro 6000.
i couldnt get the sound to work at all.
typed in the above commands.
TYVM
i can finally listen to my music:)
the unfortunate part is, i still cant listen to streaming audio from a radio station.
but at least i have my music now.

thanks
alving

---

### Post by Favux on 2009-10-23
Hi alving,

Great!

If you're interested you could add your model to markbuntu's "snd_hda_intel options database" thread here:  [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

You could also check if some of the other Toshiba entries work better for you.

---

