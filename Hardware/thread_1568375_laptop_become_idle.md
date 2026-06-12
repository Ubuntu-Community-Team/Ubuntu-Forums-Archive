---
title: "laptop become idle"
date: 2010-09-05
forum: Hardware
---

### Post by magnxpyr on 2010-09-05
Hi,

I have a laptop Fujitsu Siemens Amilo Pi 2550 and if I don't move the mouse for a few seconds becomes idle. Sometimes become idle after 1-2 seconds, sometimes after 1 minute (it happens randomly). When that happens everything stops including sound, but when I move the mouse everything go back to normal.
Right now I'm using ubuntu 10.10 beta x64. On ubuntu 10.04 I can prevent the laptop become idle if I listen music but the sound stop sometimes for a second. (seems like is an alsa driver problem)
Right now the only solution is to install OSS driver and to play music all the time.
Anyone have some better solutions to solve this problem?

Thanks

---

### Post by dino99 on 2010-09-05
check your power saving settings: system prefs powersaving (or so), and maybe the bios settings too

---

### Post by magnxpyr on 2010-09-05
> **dino99 said:**
> check your power saving settings: system prefs powersaving (or so), and maybe the bios settings too
I checked the powersaving and bios settings. I tried even to disable the powersaving using
```
sudo hdparm -B 255 /dev/sda
```
and still nothing

---

### Post by magnxpyr on 2010-09-18
Update:
I tried arch linux and I figure out until I start xorg + gnome I don't have the idle problem
my laptop has an integrated video card (ati mobility hd 2400); someone told me  this can cause some problems because when my video card become idle, my motherboard can become idle too.
Now I'm using ubuntu 10.04 x64

---

### Post by Billy71 on 2010-11-19
Have you tried the latest BIOS update? 

[http://ts.fujitsu.com/support/downloads.html](http://ts.fujitsu.com/support/downloads.html)

---

