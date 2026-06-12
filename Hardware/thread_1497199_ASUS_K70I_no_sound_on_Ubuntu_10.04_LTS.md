---
title: "ASUS K70I no sound on Ubuntu 10.04 LTS"
date: 2010-05-30
forum: Hardware
---

### Post by Snapdog on 2010-05-30
Hey, I'm somewhat new to Ubuntu and now I've decided to install Ubuntu on my new laptop (ASUS K70I). Everything else seems to run fine except the sound.
Ubuntu has detected my sound-card and drivers seem to be running normally.
The only way that I can get sound is by plugging headphones in.
I've also tried changing volume settings through alsamixer with no luck

/edit oh yea I run the 64bit version of ubuntu
Please help :(

---

### Post by Snapdog on 2010-05-31
bump, ideas anyone? :/

---

### Post by dino99 on 2010-05-31
install paprefs and gnome-alsamixer (with synaptic) and set your prefs with gnome-alsamixer

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Snapdog on 2010-05-31
I got this solved,
I added this line to the alsa-base.conf:

 options snd-hda-intel model=asus-mode3
Upon restart the Xorg server crashed, but i could open gnome in low graphics mode,
then I tried opening the nVidia control panel and it wanted me to do this:

 sudo nvidia-xconfig
and to restart the xorg server... Well now it seems to run fine, sounds come through the built-in speakers and I have high resolution. Thanks for the help ! =)

yay =D

---

### Post by lidex on 2010-05-31
For others to reference, would you post the output of this command please:
```
head -n 1 /proc/asound/card*/codec#*
```
Thanks!

---

### Post by Snapdog on 2010-06-01
Here you go: 

```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC662 rev1

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID a
snap@snap-laptop:~$ 



```Anyways after adding those lines to the alsa-base.conf my nVidia driver stopped working. I got it working by reinstalling the driver so its fine now :>

---

