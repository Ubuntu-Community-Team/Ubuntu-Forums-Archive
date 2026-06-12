---
title: "my sound broke"
date: 2009-07-10
forum: Hardware
---

### Post by Tak11 on 2009-07-10
upgrading to jaunty broke my audio completely =(

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

tak@lockpick:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and i have everything set to auto-detect. 

I've updated alsa, went through audio, and volume settings, im stumped.

---

### Post by Tak11 on 2009-07-10
I've tried this fix 

> 

1>Run the following commmand
sudo gedit /etc/modprobe.d/alsa-base
2>Add the following text to it.
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
3>Save the file.
4>Rune the following commend :
sudo /etc/init.d/alsa-utils restart
5>If this does not work try rebooting machine. Sound should be back again.


yet on restarting alsa i got this error

 * warning: 'alsactl store' failed with error message 'alsactl: save_state:1502: No soundcards found...'...      [fail]
 * Setting up ALSA...   Invalid card number.

---

### Post by Tak11 on 2010-04-05
If anyone else had this problem, here is the fix.

add 

options snd-hda-intel enable_msi=1
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel model=hp-dv5

to /etc/modprobe.d/alsa-base.conf

this took me days to find :/ so enjoy. (i forgot to post back sorry :P)

---

