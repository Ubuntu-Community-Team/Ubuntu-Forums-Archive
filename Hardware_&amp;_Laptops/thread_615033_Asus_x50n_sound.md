---
title: "Asus x50n sound"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by dave.007 on 2007-11-16
Hi,
I just bought an Asus x50n from the F5 entertainment series, Ive got the graphics card and all the other hardware working, but im having trouble with getting the sound to work.
I have followed 3 guides on this forum but still cant get it to work, it recognized the card out of the box but failed to produce any sound.
```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC660-VD
Codec: Motorola Si3054

```
```
root@dave-laptop:/home/dave# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Out of the box it looks like it has recognized the card and it is in use but there is no sound at all. The volume control image that shows up when the volume hotkey is pressed also works straight away.

??
Thanks
Dave

---

### Post by dave.007 on 2007-11-18
anybody?:confused:

---

### Post by dave.007 on 2007-11-19
bump
I promise ill kill the winxp partition i ever get this sound working:lolflag:

---

### Post by dave.007 on 2007-11-26
:popcorn:

---

### Post by richardhundt on 2007-12-10
I got it working with:

options snd-hda-intel model=lenovo

In /etc/modprobe.d/alsa-base

Reboot and kill that nasty Vista partition ;-)

---

### Post by weirdfrog on 2007-12-10
Hi Dave-- I have the same setup in my Asus a8dca1 laptop--it took me a month to figure this out.
If richardhundt's suggestion about adding the "options snd-hda-intel model=lenovo"  line  to /etc/modprobe.d/alsa-base doesn't work for you, insert the same options line, or alter the existing one if it's already there, in  /etc/modprobe.conf instead.
(I compiled and installed the newest alsa driver and lib - 1.0.15rc3, and the newest alsa utils --1.0.15rc1 first. You may or may not need to do that, but that's what I did before adding the code.)
Nothing I tried in /etc/modprobe.d/alsa-base seemed to make a difference, but as soon as I put it in /etc/modprobe.conf and rebooted, it worked like a charm.

This works for the Asus f3sa-a1 in Fedora 8 as well, according to [http://www.zer0.net/2007/11/asus-f3sa-notebook-and-linux.html]("http://www.zer0.net/2007/11/asus-f3sa-notebook-and-linux.html")
Good luck!

---

### Post by MikeMix on 2007-12-13
Hello Dave.

I hope you can help me. I also bought Asus X50N (F5) and i try to install linux on. Unfortunately no luck. I try different latest distros-Ubuntu,Kubuntu,Mandriva,Fedora,Slax,DamnSmallLinux, etc.
Always problems with X...for example with Ubuntu i get message: Kernel panic...
All installation are automatic, from livecd. 

Please advice with short description. I already want to throw this notebook to garbage!

Best regards,
M.

---

### Post by dave.007 on 2007-12-16
@Frog - Thanks for the advice on the sound setup, ill try that as soon as possible as i have exams on at school at the moment and time is hard to find and ill let you know how it goes.

@Mike -
I had a few problems with getting it to run X at first, to run the livecd i had to use safe graphics mode, and i got 800x600 so i had to set it up with half the controls missing but its not too hard. Once its installed you have to install the restricted drivers for the gfx card. Then just go into the display thingy and have a play around. Also i tried xubuntu and that picks up all the resolutions fine even without the restricted drivers.

@richard - thanks too didnt see ure post up there

---

### Post by dave.007 on 2007-12-17
Thank guys so much
all i needed was the
options snd-hda-intel model=lenovo
line and it works a charm

---

### Post by weirdfrog on 2007-12-22
Hey there dave.007 -- Glad you got it working! Just to satisfy my own curiosity, what worked for you---adding that options  line to /etc/modprobe.d/alsa-base or to /etc/modprobe.conf?

---

### Post by dave.007 on 2007-12-22
alsa-base
I just hadnt tried that one before.
Asus laptop has a lenovo model?:confused:

---

### Post by jpr0 on 2008-01-11
Hi Dave
I also have an asus x50n. I tried installing ubuntu 7.10 on it, but i just can't boot after installation. I can install and boot 7.04, but still have trouble with the graphics card. I was just wondering if you're using 7.10 or 7.04? If you're using 7.10, did you experience any other problems other than the graphics card? I *think* the problem with 7.10 on my laptop is to do with the SATA drive.. it looks like it fails because can't find the hard disk (even though it partially boots??). 
I'd be really interested to know you managed to install this because I've been trying for weeks with no luck..

---

### Post by jpr0 on 2008-01-14
Just an update to the sound issue. I tried everything mentioned in this thread, but nothing would work. I tried everything in this post (which says basically the same thing, only in a bit more detail) 

[http://ubuntuforums.org/showthread.php?t=539595&highlight=A135](http://ubuntuforums.org/showthread.php?t=539595&highlight=A135)

It still wouldn't work for me though. Finally this worked: 

[http://www.mail-archive.com/edubuntu-users@lists.ubuntu.com/msg02581.html](http://www.mail-archive.com/edubuntu-users@lists.ubuntu.com/msg02581.html)

I'm not sure if the first step is really necessary, i.e. whether the second step fixes everything. Either way, my sound is working now.

---

### Post by dave.007 on 2008-01-26
I had no problems at all with the graphics or booting.
This laptop seems to be very strange as everybody has different problems with it, the only problem I had with it was the sound, but some people I have helped with it on other forums cant even get it to boot in safe graphics mode. And I'm not too sure about it as it shows weird results on any hardware scans...
I am using 7.10 and that installs easier than 7.04 for me, it doesn't seem to be a linux friendly laptop, I couldn't get fedora to work with it or mint linux, OpenSuse works quite well and the sound is easier to setup in that because it has a GUI for it.
](*,)

---

