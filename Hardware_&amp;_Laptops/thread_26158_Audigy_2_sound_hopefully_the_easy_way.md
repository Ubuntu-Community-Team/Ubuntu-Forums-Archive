---
title: "Audigy 2 sound hopefully the easy way"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by MacGyver1 on 2005-04-12
Open synaptic pakage manager and install kmix

ALT-F2 and run kmix, under output i turned up PCM right of 3D Control Sigmatel control
and front in between PCM Surround and Surround controls

Under Switches TAB enable Audigy Analog/Digital Output Jack
Dont know why this one ...but it works after i do..

You may need to do this ... not sure tho

Under System ---> Preferences ---> Multimedia Systems Selector, change both to Alsa.

This has gotten my sound to work without having to seriously do any configuring or recompiling.

Sorry if this has been already posted but and hope it helps anyone that wants to install kmix.

---

### Post by ghostcom97 on 2005-04-15
Even better:
amixer is already installed! In console run:
```
amixer sset 'Audigy Analog/Digital Output Jack',0 unmute
```
or if you are a gui dependent gnome user:
```
gnome-alsamixer
```
and in here tag 'Audigy Analog/Digital Output Jack' mark

Stuff the amixer line in a launcher/bashscript or even in the sessions startup programs :-)

---

### Post by sagara on 2005-04-15
dude, thanks a lot!!!

this fixed it for me, however one question: is the audio now set up for mono... no stereo???

---

### Post by iammrhand on 2005-04-19
[QUOTE=ghostcom97]Even better:
amixer is already installed! In console run:
```
amixer sset 'Audigy Analog/Digital Output Jack',0 unmute
```
or if you are a gui dependent gnome user:
```
gnome-alsamixer
```
and in here tag 'Audigy Analog/Digital Output Jack' mark

Stuff the amixer line in a launcher/bashscript or even in the sessions startup programs :-)[/QUOTE]
 How do I set this up at boot?

---

