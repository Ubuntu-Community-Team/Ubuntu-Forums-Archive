---
title: "How to Check for Stereo Input on NE71B06u?"
date: 2017-07-29
forum: Hardware
---

### Post by mcman56 on 2017-07-29
Is there a way to see if there is stereo input on a Gateway NE71B06u?  It seems to have two sound cards but I have no idea what that really means.  See below...is that really two cards?  I want to use Xoscope for a 2 channel sound card oscilloscope so stereo input is essential.    


dan@dan-NE71B:~$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 1: Generic_1 [HD-Audio Generic], device 0: CX20588 Analog [CX20588 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 2: CX20588 Alt Analog [CX20588 Alt Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

---

### Post by mcman56 on 2017-09-20
[h=2][COLOR=#4c4c4c][FONT=Ubuntu Beta, UbuntuBeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]PulseAudioVolume Control -  If you load this and run, it will identify allof your sound devices, not in detail but generically.  Iteven recognizes a USB sound card.   The Gateway doeshave stereo input on the microphone port.[/FONT][/COLOR][/h]

---

