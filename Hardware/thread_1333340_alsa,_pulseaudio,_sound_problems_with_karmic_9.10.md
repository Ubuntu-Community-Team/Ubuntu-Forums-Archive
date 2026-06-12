---
title: "alsa, pulseaudio, sound problems with karmic 9.10"
date: 2009-11-21
forum: Hardware
---

### Post by washakie on 2009-11-21
Hello,

After upgrading to 9.10 I've had continuous problems with sound. 

Following the instructions on the [wiki]("https://help.ubuntu.com/community/SoundTroubleshooting"), I've generated the following output:
[http://pastebin.ca/1680913](http://pastebin.ca/1680913)

Ultimately, I can usually get the sound to work, but it requires that I type:
%sudo alsa force-reload

after every reboot. All was fine with 9.04. What configuration do I have to change to not need to do this every time my computer reboots?

One bit of troubleshooting is that under the mixer, it seems the hardware is not recognized until running force-reload. Also, I do not have the following groups:

sound
pulse-rt

but I am a member of the others:
audio
video
pulse
pulse-access

Thanks!

---

### Post by alexfish on 2009-11-21
try this 

[I]for sound output list 

 aplay -l

to check sound kernel

[/I][I]added   : to find out if the kernel matches system kernel  

modinfo soundcore 
 [/I]

---

### Post by washakie on 2009-11-21
Everything looks normal to me??

[]$modinfo soundcore 
filename:       /lib/modules/2.6.31-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-14-generic SMP mod_unload modversions 
[jfb@jfb-field opt]$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[]$

---

### Post by alexfish on 2009-11-21
hi there is a software modem 

Si3054 Modem [Si3054 Modem]

try to disable in the bios first

ps what does the system kernel show

---

### Post by darco on 2009-11-21
Check this link, I too had issues w/9.10 and sound and this resolved it.

[http://ubuntuforums.org/showthread.php?t=1326487](http://ubuntuforums.org/showthread.php?t=1326487)


darco

---

### Post by alexfish on 2009-11-21
> **darco said:**
> Check this link, I too had issues w/9.10 and sound and this resolved it.

[http://ubuntuforums.org/showthread.php?t=1326487](http://ubuntuforums.org/showthread.php?t=1326487)


darco

are you saying  pulse audio is one of the problems (because this is interesting )
   you may have spotted something

---

