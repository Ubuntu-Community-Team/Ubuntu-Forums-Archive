---
title: "Medion 96290 - No sound"
date: 2009-10-19
forum: Hardware
---

### Post by Skyline649 on 2009-10-19
[SIZE=3][COLOR=Black][B]Hello guys ,

I'm having problems with my Medion soud drivers and devices probably.

I have only sound when I plug in an external device such as stereo system through my stereo input, I've made a couple of changes according to my devices , and the only thing I know is that my sound card comes from Intel.

Can anybody just tells me or just navigates me through the process of fixing this.

Thanks :)
[/B][/COLOR][/SIZE]

---

### Post by John Bean on 2009-10-19
If you mean no sound from the internal speaker but it's ok if you plug in headphones/whatever then open this file:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
and add this line to the end:
```
options snd-hda-intel model=laptop
```
Save and reboot.

---

### Post by Skyline649 on 2009-10-19
It's still not working , I 've tried to reinstall the ALSA , and to update it , but that works not too. So now I'having no sound at all , no stereo system , no internal speakers , so I suggest if you can tell me how to install again ALSA from the terminal

Thanks :)

---

### Post by John Bean on 2009-10-19
Sorry, too many variables and not enough information to determine what you did. I suspect that after initial installation sound was working but the internal speakers were not and this fooled you into thinking it wasn't working, but whatever you've done to try to fix it has broken something else.

I'll leave it to others with direct experience to explain how to completely reinstall the sound system, I've never had to do it.

---

### Post by Skyline649 on 2009-10-19
I've made it , I just realize that if you want to update ALSA software you have to save first all you conf.files otherwise after the renewing it's all gone , and you have no sound at all

---

### Post by Ghosty.be on 2009-11-14
Ok looking a bit around on some german thread about this laptop i found that you don't need to try and fix anything to alsa driver.
The standard alsa driver in karmic just works but ...
What John Bean suggested is the way but the line to add at the end should be:
```
options snd-hda-intel model=auto
```

and that appears to work. (tested this through IRC communication with a guy with the same laptop model, this seemed to work, the model=laptop did not seem to work.)

---

