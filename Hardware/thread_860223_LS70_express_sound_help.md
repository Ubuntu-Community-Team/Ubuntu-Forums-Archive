---
title: "LS70 express sound help"
date: 2008-07-15
forum: Hardware
---

### Post by hawks-SOAD on 2008-07-15
hi i need help with my sound i have a lg ls70 express with a c-media 9880 chipset and ispci wont work plz help

---

### Post by Mengus on 2009-02-20
I have an LW70 express and are perhaps having the same problem. I am getting sound in the headphones though. It just wont play in the speakers.
Does anyone know how to fix this?

---

### Post by SciB6y on 2009-04-20
The solution I found was adding the line
```
options snd-hda-intel model=minimal
```
to the file "/etc/modprobe.d/alsa-base"

It works fine in 8.10, but seems to have stopped working in 9.04. Try it if you're still having problems.

---

### Post by chrisewcs on 2009-05-08
edit
/etc/modprobe.d/alsa-base.conf
# Prevent abnormal drivers from grabbing index 0
options snd-hda-intel model=minimal

and also edit
/etc/init.d/alsa-utils
before
# Required for HDA Intel (hda-intel):
    unmute_and_set_level "Front" "80%"
after
# Required for HDA Intel (hda-intel):
    unmute_and_set_level "Front" "70%"
and
before
# HDA-Intel w/ "Digital" capture mixer (See Ubuntu #193823)
    unmute_and_set_level "Digital" "80%"
after
# HDA-Intel w/ "Digital" capture mixer (See Ubuntu #193823)
    unmute_and_set_level "Digital" "70%"
reboot
if you here nothing be shure Surround Center LFE is on in ALSA mixer

hope this helps you

LG LW70

---

### Post by gonzakloperu on 2009-06-10
Any other idea for ubuntu 9.04 on lg ls70 express with c-media 9880 chipset (snd-hda-intel). On 8.10 (and on the latest archlinux too) sound was fine with:

options snd-pcsp index=2
options snd-hda-intel model=minimal
options snd-hda-intel model=lg

on alsa-base.conf

Maybe recompile? #-o

---

### Post by ryry46d9 on 2009-06-12
> **chrisewcs said:**
> edit
/etc/modprobe.d/alsa-base.conf
# Prevent abnormal drivers from grabbing index 0
options snd-hda-intel model=minimal

and also edit
/etc/init.d/alsa-utils
before
# Required for HDA Intel (hda-intel):
    unmute_and_set_level "Front" "80%"
after
# Required for HDA Intel (hda-intel):
    unmute_and_set_level "Front" "70%"
and
before
# HDA-Intel w/ "Digital" capture mixer (See Ubuntu #193823)
    unmute_and_set_level "Digital" "80%"
after
# HDA-Intel w/ "Digital" capture mixer (See Ubuntu #193823)
    unmute_and_set_level "Digital" "70%"
reboot
if you here nothing be shure Surround Center LFE is on in ALSA mixer

hope this helps you

LG LW70

what sound mixer are you using the default mixer next to the clock doesn't show the sliders for the other channels HDA Intel (Alsa mixer) only shows PCM and PC Speaker (looked through all the options/clicked them all to show)    so as of right now this fix fails for 9.04 

I know this laptop isn't that popular but you would think the dev team would stop breaking this for the 5 users it has  ;)

---

### Post by gonzakloperu on 2009-06-17
Try: 

# modprobe snd-intel8x0m  

it works for me with "options snd-hda-intel model=minimal" on /etc/modprobe.d/alsa-base.conf

LG LS70 Express

---

### Post by mattgeldard on 2009-12-03
Has anyone had any luck with 9.10 yet? I have tried all the above with no success

---

