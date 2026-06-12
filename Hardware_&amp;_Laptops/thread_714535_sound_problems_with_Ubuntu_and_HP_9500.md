---
title: "sound problems with Ubuntu and HP 9500"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by kvalenza on 2008-03-03
I just got an HP 9500 with a Realtek sound card.  I have tried various soloutions on this board, and some of them are too tough to figure out. None of the solutions I tried have worked. This is really frustrating because I have used ubuntu with no problem at all on my old Dell computer.  Can anyone help?  Also, to those who are designing the next upgrade...will you try to make it so that Ubuntu can use the Realtek sound card?

---

### Post by nikhilcdac on 2008-03-04
I know of two causes for not hearing the sound.
first cause: there are many options in the mixer. double click the volume icon to open the mixer. change the mixer device to hda-intel. Then open the settings menu. there will many options like PCM, front, mic etc. select them all, and press ok. Now make sure that all option are to max volume and are not muted. you should look for "Front" option specifically. If all these options are ok and sound is not coming, you need to install updated alsa. This is the secaond caue.
Second cause: for Updating alsa, you need to follow few steps that are very well documented on [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) .
BTW, i am new to Ubuntu and linux world and since 2 days back started getting into linux world.

---

### Post by superprash2003 on 2008-03-04
if that doesnt work.. try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

