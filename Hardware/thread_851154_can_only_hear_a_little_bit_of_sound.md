---
title: "can only hear a little bit of sound"
date: 2008-07-06
forum: Hardware
---

### Post by carman3756 on 2008-07-06
I have installed ubuntu 8.04 on a toshiba satellite A305 I havent had any problems with anything but the sound volume is very low even with everything turned all the way up.  I know that the problem is not the hardware because when running windows vista (pile of junk) the sound is very loud when cranked up.

any help would be great, I would consider myself a new to Intermediate user but a little more on the new side of things and im not afraid of the terminal.

Thinks guys

---

### Post by tech0007 on 2008-07-06
open terminal and run 'amixer'. turn them all the way up.

---

### Post by jcsteele on 2008-07-06
This use to happen with gutsy on my toshiba notebook - below is what corrects it.


Fix:

Edit: /etc/modprobe.d/alsa-base

Add: "options snd-hda-intel position_fix=1 model=3stack" to end of file (without quotations)


Reboot

---

### Post by carman3756 on 2008-07-06
tech0007 = amixer brought up the terminal editing version and I couldnt figure out how to change any of the values but I did a little searching and found a help file that said to use "alsamixer" and that brought up the graphical interface.  The speakers were set to 80% so I turned them up.

jcsteele = tried adding the line as you suggested but it didnt seem to make a difference on my computer, but you know how it is different things work on different computers

Thanks for your help guys!!

---

### Post by ante.wessels on 2008-07-08
I had no sound at all at my Toshiba 140 15B. That was with Kubuntu 7.10. I upgraded to 8.04, from 7.10. Still no sound. 

I tried a lot of things, like compiling stuff and going to an install party. There I installed gnome on my Kubuntu, they were more familiar with that. Then I had a little sound, I found out when I got home (too much noise at the party to notice).

A magazine came with an Ubuntu live cd, and well, sound worked!

I tried to find out why it worked running the live cd. Then I did a few things, I installed totem (live cd has it), I copied /etc/modprobe.d/alsa-base from the live cd to my hard disk. Restarted. Now turning some kmix volumes up gave sound in KDE, the same in Gnome. 

Some of these steps or all together helped...

---

