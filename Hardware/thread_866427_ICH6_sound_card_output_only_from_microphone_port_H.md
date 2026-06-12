---
title: "ICH6 sound card output only from microphone port Hardy"
date: 2008-07-21
forum: Hardware
---

### Post by Stephiroth on 2008-07-21
This is my first install of Unix.  I am pretty new to the OS, but I am not new to computers (I'm an electrical engineer) so please include any "duh" things you would assume I already know, but feel free to get into specifics. I'm having fun geeking out over my OS. :p

My problem: 
I have a Motion LE1600 tablet pc that is proving to be quite difficult.  When I first installed, I did not have sound at all.  After tweaking with a few settings in Volume Control (disabling the External Amplifier), I can get sound, but only if I plug headphones into the microphone port (weird, I know).  I can't find anything that's muted or not turned up. I have tried the tests in system>prefs>sound with every possible config on there, and I only get sound through the mic port.  

Alsa obviously recognizes the card and will produce sound. I can watch dvds, play mp3s, etc, but no external sound. 

I tried installing new alsa-firmware from medibuntu (at the recommendation of a friend)- no change

I tried uninstalling and reinstalling Alsa -no change

I tried various muting, volume levels, oss, switches, basically if it is a setting on a sound control panel I've messed with it or toggled it.  (But if you have a suggestion I will try it again.) -no change

lspci gives me:

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

Kernel: 2.6.24-19-generic  Ubuntu 8.04 

aplay --list-devices: 

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


It seems like the drivers are just sending the sound to the wrong bits of the hardware.  I'm not sure if, where, or how I would be able to edit that code.  Does anyone have and ideas/solutions for my problem?  Anything would be appreciated because I'm getting pretty frustrated.  

Thanks!

---

