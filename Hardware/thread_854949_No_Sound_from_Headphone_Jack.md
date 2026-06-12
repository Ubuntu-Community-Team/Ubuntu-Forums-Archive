---
title: "No Sound from Headphone Jack"
date: 2008-07-10
forum: Hardware
---

### Post by bstilljames on 2008-07-10
Hello! So here's the deal: I'm running Linux Mint 5 /XP on a Toshiba Satellite A135-S4666. If it weren't for the following problem, I would abandon Windows all together. This would make me one happy guy.

Sound Card:

```
brandon@Bowie ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```


So that's my sound card. In previous versions of Mint, I was able to get sound to come out, it just wouldn't mute the speakers. With Elyssa, which is Hardy based and beautiful (excellent job all), I have no sound at all no pops or clicks when plugging or unplugging. The jack works fine in Windows. I have the latest ALSA drivers. I've tried the solution proposed on this thread (which is excellent and probably helpful to many)  
[URL="http://ubuntuforums.org/showthread.php?t=616845&highlight=ALC861VD"]

If anyone has any ideas, it would be hugely appreciated! I'm still a bit of a newb, so details would be great. Thank you so much!

---

### Post by bstilljames on 2008-07-10
All right! I figured it out.

figure out what sound card you have by typing in the terminal:

aplay -l

this will tell you what model your sound card is 


Now,
in the terminal:


sudo gedit /etc/modprobe.d/alsa-base


this opens the alsa base file in gedit
after the last line of code enter the following:

options snd-hda-intel model=lenovo

save the file and reboot

lenovo may be replaced by a number of options
depending on what intel model your sound card is
find a list of models at the following website

[http://ubuntuforums.org/showthread.php?t=616845&highlight=ALC861VD](http://ubuntuforums.org/showthread.php?t=616845&highlight=ALC861VD)

these same instructions are essentially there. It's just a little more to look at.

I'm a newb and I figured it out. Good Luck!

This fix also mutes the speakers when the headphones are plugged in!

---

