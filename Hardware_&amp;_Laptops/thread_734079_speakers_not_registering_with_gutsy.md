---
title: "speakers not registering with gutsy"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by freddy_engels on 2008-03-24
I just salvaged some old Boston Digital BA735 speakers (two of them) and subwoofer, but when I plug them in, ubuntu doesn't notice that they are there. 

Here is some of my command line output:

 aplay -l
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/cards
>  0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x9b500000 irq 19

 lspci | grep -i audio
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

It knows my laptop speakers are there (obviously), but says nothing about the speakers that I have plugged in.

What should I do to get them working? 

Oh, also, I am using a macbook pro with gutsy gibbon (no dual boot), and my kernel version is 2.6.22-14.

---

