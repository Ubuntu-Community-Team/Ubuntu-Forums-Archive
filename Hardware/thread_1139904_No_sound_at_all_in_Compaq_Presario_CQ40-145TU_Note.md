---
title: "No sound at all in Compaq Presario CQ40-145TU Notebook PC"
date: 2009-04-27
forum: Hardware
---

### Post by joseinbaraj on 2009-04-27
I am trying Ubuntu for the first time ....

After a clean install there is no sound in my system ( model mentionted int eh title )

the output for aplay -l is 

jose@Parikrama:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


__________________________________________________________________________


and the audio drive that is inbuilt in my motherboard is 

Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

______________________________________________________________________________


Can someone please tell me the solution for the problem in step by step as i am a newbie to ubuntu ....

Thanks in advance.

---

### Post by joseinbaraj on 2009-08-29
edit the file with the next command

gksudo gedit /etc/modprobe.d/alsa-base.conf  ( for 9.04 )

add this lines at end of the file
____________________________________________________


options snd slots=snd-hda-intel,snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1

__________________________________________________

save and restart the sys.. sound works fine for my system

---

### Post by web032009 on 2009-09-13
@joseinbaraj thank you this work for my Compaq Presario CQ40-108TU
 
 
-----------------------------------------------------------------------------------
 
options snd slots=snd-hda-intel,snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1
 
------------------------------------------------------------------------------------

---

