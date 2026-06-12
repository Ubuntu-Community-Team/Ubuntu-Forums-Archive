---
title: "HP DV-7 3186CL Headphone Jack Sensing Fails"
date: 2010-12-29
forum: Hardware
---

### Post by N3RVE_deact on 2010-12-29
I have a HP DV7. My laptop speakers work fine but when I connect headphones into the headphone jacks, it continues to output sound from both the laptop speakers and the earphones. I have to go under Sound preferences and change the value for "Connector" to "Analog Output" to make it output from the earphones alone. My other laptop running ubuntu 10.04 (DV6) senses the headphones alright and mutes the laptop speakers automatically. Help?

```
lspci|grep Audio
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

---

### Post by lidex on 2010-12-30
This is a generic fix for DvX series. 
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by SomeGayDude on 2011-02-09
This is AWESOME!!!  Thanks a million.  My hair can finely grow back...

---

### Post by lidex on 2011-02-09
> **SomeGayDude said:**
> This is AWESOME!!!  Thanks a million.  My hair can finely grow back...
Beats paying the "Hair Club For Men"

---

### Post by cxlxmx on 2011-02-09
Could also just mute sound on laptop speakers.  This is what I do to make sure I don't accidentally unplug my earphones and have the laptop speakers come on full blast in the middle of the library.

---

