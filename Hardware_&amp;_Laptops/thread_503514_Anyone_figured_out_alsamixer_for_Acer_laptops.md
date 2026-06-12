---
title: "Anyone figured out alsamixer for Acer laptops?"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by wastedfluid on 2007-07-18
Acer 510 here.

I've been on a reading rampage looking for solutions to my alsamixer problems.  I've tried to many tutorials, that it's getting ridiculous.  I can play most music, but say, if I run mplayer, I get this:

```

[gl2] You have OpenGL >= 1.2 capable drivers, GOOD (16bpp and BGR is ok!)
[gl2] antialiasing off
[gl2] bilinear linear
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 0 0              
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 1 0              
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 2 0              
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 3 0              
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 4 0              
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 5 0              
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 6 0              
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 7 0              
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 8 0              
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 9 0              
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 10 0             
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 11 0             
alsa-control: mixer load error: Invalid argument ??% ??% ??,?% 12 0             
alsa-control: mixer load error: Invalid argument 37% 344%  6.4% 13 0            
alsa-control: mixer load error: Invalid argument 35% 343%  6.5% 14 0            
alsa-control: mixer load error: Invalid argument 33% 341%  6.5% 15 0            
alsa-control: mixer load error: Invalid argument 31% 337%  6.5% 16 0            
alsa-control: mixer load error: Invalid argument 30% 335%  6.4% 17 0            
alsa-control: mixer load error: Invalid argument 28% 334%  6.3% 18 0            
alsa-control: mixer load error: Invalid argument 27% 332%  6.2% 19 0            
alsa-control: mixer load error: Invalid argument 26% 333%  6.2% 20 0            
alsa-control: mixer load error: Invalid argument 25% 331%  6.3% 21 0            
alsa-control: mixer load error: Invalid argument 24% 330%  6.3% 22 0            
alsa-control: mixer load error: Invalid argument 23% 329%  6.2% 23 0            
alsa-control: mixer load error: Invalid argument 22% 328%  6.2% 24 0            
alsa-control: mixer load error: Invalid argument 22% 327%  6.2% 25 0            
alsa-control: mixer load error: Invalid argument 21% 325%  6.2% 26 0            
alsa-control: mixer load error: Invalid argument 20% 324%  6.1% 27 0            
alsa-control: mixer load error: Invalid argument 20% 324%  6.2% 28 0            
alsa-control: mixer load error: Invalid argument 20% 325%  6.3% 29 0            
No bind found for key ''.                         0% 324%  6.2% 30 0     

```

$ alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument

alsamixer will not work to save the life of me.  Any ideas?  Did anyone ever figure this one out?  Google is leading me to dead ends.

---

### Post by micoams on 2007-08-29
Similar problem over here. Alsamixer is dead. 

```
alsamixer: function snd_mixer_load failed: Invalid argument
```


Linux ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
ACER Aspire 5100
ATI SB450 HDA Audio

---

### Post by RageOfOrder on 2007-08-30
Works fine for me.

Acer Aspire 9410
Slackware 12.0

Alsamixer works, Amarok has been using xine + alsa since I bought the laptop...

Must be ubuntu specific?

---

### Post by khristian on 2007-09-16
bump for solution, acer 5100 here.

---

### Post by kush_2207 on 2007-09-23
I am also getting the same error.
My Laptop is Acer 5100-5022.
Did anyone circumvent this problem ?
Please help i am not able to watch HD Movies :mad:

---

### Post by spooner on 2007-09-23
I'm bumping this as well. I have an Acer Aspire 3050 (UK version) and I have no sound since the upgrade to Kernel Patch 2.6.20-16. I have checked the alsa install and the sound card is recognized and it should be working... returning to Kernel 2.6.20-15 and everything is fine. (well speakers are controlled by the surround slider and headphones by the front slider so I can change the volume of each separately and when headphones are plugged in speakers don't mute have to do this manually but in essence everything works fine...)

Here's the output of aplay -l  for each kernel.

```

spooner@SPOONER-ACER:~$ uname -r
2.6.20-16-generic
spooner@SPOONER-ACER:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
spooner@SPOONER-ACER:~$ alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument


```

and 

```

spooner@SPOONER-ACER:~$ uname -r
2.6.20-15-generic
spooner@SPOONER-ACER:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
spooner@SPOONER-ACER:~$ alsamixer
spooner@SPOONER-ACER:~$

```

The only difference that I can see is the subdevice section with the broken one saying 0/1 and the working one being 1/1. I believe this is our problem but I don't know the solution...

---

### Post by bobpur on 2007-09-23
Not a problem with my Acer Travelmate 4230-6179 with the Live CD from Ubuntu, Mint or Pioneer. I'm not installing at this time as I may be RMAing this machine for picture / screen issues. Sometimes only half of the screen lights up while the other half stays out or is very dim. I think it's the ribbon cable that connects the screen to the computer that runs thru the hinge joint somewhere.
As soon as I get a new one Vista is outta here.

---

### Post by spooner on 2007-10-02
Sorry for the long reply... but the live disk uses the older Kernel patch still right? I have sound working fine with that... it's just the updated Kernel that broke, the one automatic updates wants you to install after you've booted into your fresh install.

---

### Post by Roobitz on 2007-10-07
Bump for an Acer 3050 - no sound at all, alsamixer command yields "function snd_mixer_load failed: Invalid argument"

I'm a total noob though so go easy!

---

### Post by spooner on 2007-10-22
Well, Gusty upgrade solve all the problems. Fast volume up and down does not work as there doesn't appear to be a master... but I changed the default to wave. So if i'm listening through headphones (Front) or using the speakers (Surround) volume is changed.

---

