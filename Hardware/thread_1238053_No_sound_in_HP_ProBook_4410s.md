---
title: "No sound in HP ProBook 4410s"
date: 2009-08-12
forum: Hardware
---

### Post by setjahat on 2009-08-12
I have bought this HP ProBook 4110s and installed ubuntu 9.04. Even after updates, I couldn't get the sound to work. I've tried the "alsamixer -Dhw" and searched on the net and found the closest at [http://pradeepfernando.blogspot.com/](http://pradeepfernando.blogspot.com/) and tried his way, i.e.

quote:

[I]"open a new terminal & type,

cd /etc/modprobe.d

sudo gedit options

enter your password & it will open up the options file in the text editor.Now append this (or if the file is create by you for the first time just copy/paste this) at the end of the file.


options snd-hda-intel model=laptop


save & close the file, then re-boot the machine. Now you should hear that amazing drum sound of Ubuntu.... oh yeah, time to party."[/I]


The sound does work after creating the options file but the display seems to be setting it self back to 800x600.

Please help..

---

### Post by jroc777 on 2009-08-31
I had the same problem with a HP ProBook 4510s and the fixed worked except I have no sound if I try and play a CD from the DVD drive.
Does yours work ? 
Any thoughts?
I am using Rhythm box. It looks like it is playing yet no sound.

---

### Post by Yellow Pasque on 2009-08-31
It should be:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Now add that line ( options snd-hda-intel model=laptop ). Save the file and restart your system.
Also make sure your remove that options file you created (or you'll receive warnings about it not having a .conf extension).

---

### Post by merito on 2009-09-01
**Temüjin** this works fine on HP ProBook 4710s

Thanks :)

---

### Post by jroc777 on 2009-09-05
Added following lines and removed options file.

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=laptop
alias sound-slot-3 snd-hda-intel 


theme sound works well.
Unable to play music from hard drive or Cd 

In rhythm box the device displays "pulse"

---

### Post by prins on 2009-10-14
And this is the best solution for Skype users as well.
Now you can use Skype with PulseAudio and don't have to kill it. (y)

---

