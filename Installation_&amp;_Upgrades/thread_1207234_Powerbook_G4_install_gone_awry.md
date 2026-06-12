---
title: "Powerbook G4 install gone awry"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by Burnsey on 2009-07-07
Hi  I just ordered my 5th power supply for my powerbook g4 and i think they finally got it right.    I installed using the Live ppc CD and after i enter:  boot: live or boot: live-powerpc or even boot: live-video=ofonly  it begins to load some things...   And then I get a message stating:  ```
 [2.179521] 0000:00:10.0 Raedonfb Invalid ROM contents 
```  At which point the screen then displays flickering bands and I cannot continue.  Thoughts?

---

### Post by Burnsey on 2009-07-08
Fixed it with the alternate install cd.    I joined up for this!? lol, see you folks around. :)

---

### Post by Burnsey on 2009-07-08
alright i take that back...same error after the installation is complete and it tries to load the os

---

### Post by entikryst on 2009-07-08
Try installing debian first and installing ubuntu over it.  I was experimenting different ppc friendly linux and ubuntu only worked after I installed it after debian I'm not sure why but I think it has to do with the way macs boot or something debian adds to the boot process that ubuntu doesn't.

---

### Post by Burnsey on 2009-07-11
Well i tried this...it seems that after the os loads it displays a foggy or cloudy display.  is there a way to get to a prompt to allow me to make changes...all i have at the moment is a boot [s]menu[/s] prompt.

---

### Post by tgalati4 on 2009-07-11
Sounds like your ati radeon card is taking a dump.  Try booting with a mac os X disk and see if comes up normally.  Or, grab an s-video cable and hook up to a tv.  I believe the s-video bypasses the ati card and goes direct to an ntsc or pal signal.

Try an external DVI or VGA monitor.  It may work whereas the internal video is showing its age.

---

### Post by Burnsey on 2009-07-11
but i'm able to watch the boot process.  Wouldn't a blown video card even keep that from occurring?

---

### Post by tgalati4 on 2009-07-12
No because the Radeon card has different channels to process video.  It's possible that the high-resolution graphics portion of the chip is blown.  The chips get hot and lift off of the surface of the motherboard.  Nearly impossible to fix.  It's a common problem on older machines.  It's also possible that the video RAM is wonky.  Text-mode graphics don't need much RAM but the high-res graphics do.

Only by booting into OS X will you really be able to tell if your graphics are working 100%.  The linux drivers are reverse engineered and may not work 100%.  There are some diagnostic modes that you can boot into, but I believe you need the Mac disk and a special key combination, which I don't remember.

---

### Post by F0lken on 2009-07-14
Hi !
I just tried PPC live cd and have the same symptoms.
Finally I booted into live-nosplash (or whatever it called) and got ubuntu desktop. 
It is not a hardware issue, because I successfully boot into OS X and keep working.
I think, the right way is to change kernel parameter - put something like "no splash" here. 
Hope, this will help!

---

