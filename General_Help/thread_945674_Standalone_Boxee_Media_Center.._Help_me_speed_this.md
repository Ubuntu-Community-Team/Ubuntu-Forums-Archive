---
title: "Standalone Boxee Media Center.. Help me speed this box up!"
date: 2008-10-12
forum: General Help
---

### Post by shawnrgr on 2008-10-12
I'm running [boxee]("http://boxee.tv") on my media center pc. its the only app and auto launches boxee at start. I'm looking for ways to speed this box up as much as possible. boot time is my only major concern.

My setup so far...

Packages:
Ubuntu Minimal CLI install...
xorg
openbox
nvidia-glx
thunar
ivman
lirc + lirc-x
boxee
rungetty
alsa
nfs (for sharing media out from this box)

My goal is to make this system as lightweight as possible with nasty boot times :)

I've managed to get rungetty to auto log me in, and a few changes to my .bashrc allowed me to auto run startx at login. This way i'm able to avoid loading up a login manager (this obviously is a one user box).

Everything is working fine but my boot time is still in the 30+ second range. last time i timed it, it was about 37 seconds. This is unacceptable for me.

Anyone have any ideas on speeding this up? I figured with the ubuntu cli install I wouldn't get so many services that would slow the boot down but it didn't seem to help.

I'm reaching out to you guys for help. Anything that could possibly speed this box up, boot time or anything else. Any ideas and/or tips would be helpful! 

Thanks!

---

### Post by shawnrgr on 2008-10-13
shameless *bump*

Anyone have any suggestions on how to speed this puppy up? All I need is boxee and audio. 

Maybe launching boxee directly without launching the openbox? Would that be possible?

There has to be some more corners I can cut.

Are there uneeded processes I can cut out of the base install?

---

