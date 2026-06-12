---
title: "Sound Card issue"
date: 2008-08-16
forum: Hardware
---

### Post by Zeus26 on 2008-08-16
Hi Ubuntu-users,

Anyone could help as my soundcard is not working using Ubuntu Hardy Heron. Here is the following soundcard installed in my pc....
===================================
zheck@Ubuntu-desktop:~$ aplay -l 
**** List of PLAYBACK Hardware Devices **** 
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
zheck@Ubuntu-desktop:~$ 
=========================================

Is there something that i should install or some kind of driver to install?

Could someone help or give me the commands to install this coz im quite new in using Ubuntu.

Thanks so much.

Z

---

### Post by Yellow Pasque on 2008-08-16
It looks like you have two sound devices. Try disabling your onboard audio in the BIOS.

---

### Post by Zeus26 on 2008-08-19
> **Temüjin said:**
> It looks like you have two sound devices. Try disabling your onboard audio in the BIOS.

==============

Dude that did the trick! Sound is workin fine. 

Milli Gratzie Dude!!!!


Z

---

