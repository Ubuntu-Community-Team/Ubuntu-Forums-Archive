---
title: "Internal Mic Not Working on Fujitsu Lifebook A6110"
date: 2010-02-16
forum: Hardware
---

### Post by sstoveld on 2010-02-16
hey guys, i can't seem to get my mic to work at all. haven't been able to get it working in any past version of ubuntu either

here's a screenshot of my alsamixer in terminal:
[IMG]http://img69.imageshack.us/img69/6092/alsamixer.png[/IMG]

i've searched through the forums, tried a few different things and nothing works. i use skype all the time, so it would be great if i could get this to work.

all i can hear in sound recorder is static from my mic

here's my audio device from lspci:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

any help would be greatly appreciated

---

### Post by llawwehttam on 2010-02-16
A lot of people have had problems with internal mic's in 9.10 including me.
Actually I've had EXACTLY the same problem as you.
I have tried a LOT of things but I've given up and I'm waiting for lucid.
If you find a solution please tell me...

EDIT: You could always try the backports:
```
sudo apt-get install linux-backports-modules-alsa-`uname -r`-generic
```

---

### Post by Arla on 2010-02-16
> **llawwehttam said:**
> 
EDIT: You could always try the backports:
```
sudo apt-get install linux-backports-modules-alsa-`uname -r`-generic
```

Backports worked for my Lenovo laptop and fixed it perfectly, definitely my recommendation.

---

### Post by sstoveld on 2010-02-16
thanks for the suggestion

i ran > sudo apt-get install linux-backports-modules-alsa-`uname -r`

it installed, but do i have to do anything else? my mic is still only recording static. sorry, i'm quite newb with this stuff :(

---

### Post by msrinath80 on 2010-02-16
> **sstoveld said:**
> hey guys, i can't seem to get my mic to work at all. haven't been able to get it working in any past version of ubuntu either

here's a screenshot of my alsamixer in terminal:
[IMG]http://img69.imageshack.us/img69/6092/alsamixer.png[/IMG]

i've searched through the forums, tried a few different things and nothing works. i use skype all the time, so it would be great if i could get this to work.

all i can hear in sound recorder is static from my mic

here's my audio device from lspci:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

any help would be greatly appreciated

sudo apt-get install aumix

Set IGain to its maximum or somewhere in between. That should get the mic working again.

Edit: While testing, make sure most sliders are set to non-zero values in alsamixer. Just makes life easier.

---

### Post by Baneblade on 2010-02-16
I'm having the same issue on my HP DV2910us.
I haven't tried installing backports yet. Is that a confirmed fix? What exactly does it modify?

If i set the volume to max and shout I can barely hear my voice during playback, so it is working. However there is too much static and serious lack of volume.

---

### Post by sendhil76 on 2010-02-19
Same issue with 8.04 LTS on the Fujitsu A6110 :( ...also the extra buttons on the notebook for volume were working when i first installed the OS...after one of the updates...they also stopped working. And i dont have a clue on how to get them working again.

Assistance will be appreciated!

---

