---
title: "Not getting audio"
date: 2008-11-01
forum: General Help
---

### Post by Gauvenator on 2008-11-01
I'm using an old mobo with integrated VIA audio.  I'm not able to get any sound however.  I've tried adjusting all sorts of levels in the audio control panel but I'm not having any luck.  Can someone help me troubleshoot this?  Perhaps there is a special module I need to load for this chipset?

I'm using a fresh install of Ubuntu 7.1 i386, completely updated.  If you all need any other information please let me know.

---

### Post by kerry_s on 2008-11-01
try debian etch:
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso)

a lot of things were dropped from kernel 2.6.23 on, especially sound drivers/firmware, etch has kernel 2.6.18 which still has support for the old stuff.
the other option is to compile your own kernel and put the stuff back in. 

my sound driver was also dropped, i'm using debian etch which works perfectly, but i also just built a custom 2.6.27 kernel deb for later, so i have a kernel i can add to any debian install.

---

### Post by Gauvenator on 2008-11-01
Ok I will try debian etch.

Whats the difference between "businesscard" and regular cd iso's?

---

### Post by Gauvenator on 2008-11-01
Wow I need help.  I'm having issues with Debian lol...can you advise me what repositories I need to add?

I'm trying to use this tutorial (which applies to Debian):
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
but I can't seem to install any of the programs they want me to install prior to installing the driver (subversion autoconf automake1.9 libtool).

I tried installing vlc media player too, but the dependencies can't be satisfied.

This makes me think that I need to enable some repositories...you are a debian user so I imagine you've gone through this.

---

### Post by kerry_s on 2008-11-02
> **Gauvenator said:**
> Wow I need help.  I'm having issues with Debian lol...can you advise me what repositories I need to add?

I'm trying to use this tutorial (which applies to Debian):
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
but I can't seem to install any of the programs they want me to install prior to installing the driver (subversion autoconf automake1.9 libtool).

I tried installing vlc media player too, but the dependencies can't be satisfied.

This makes me think that I need to enable some repositories...you are a debian user so I imagine you've gone through this.

i'm going to assume you did a straight install so you have gnome?

press alt+f2
type> gksudo gedit /etc/apt/sources.list

i took out the source repos from mine, i don't need them.
```
deb http://www.debian-multimedia.org/ etch main 

deb http://ftp.us.debian.org/debian/ etch main contrib non-free 

deb http://security.debian.org/ etch/updates main contrib non-free  


```

for the video the driver is called "via" the easiest way
in a terminal:
su
type> dpkg-reconfigure -phigh xserver-xorg
select> via
then the screen sizes
close it
log out
press ctrl+alt+backspace
that will restart X

don't follow the ubuntu how to's, look for debian etch how to's, although ubuntu is based on debian it is very different.
once you add "contrib non-free" and the multimedia repo you should be fine on the media stuff.

hey, so does your sound work in etch?

---

### Post by Gauvenator on 2008-11-02
Alrighty so I got openchrome to work (via wouldnt give me the correct resolution).  I was surprised that the install didn't automatically add the main repository...maybe I just messed up while it was installing.  Anyway, the display driver and package manager are working great now, thanks!!

As for the sound....I'm about to boot it up again and mess around in alsamixer.  I hope this works lol..I don't want to splurge for a soundcard.

---

### Post by Gauvenator on 2008-11-02
Unfortunately the audio is not working.  It is an old motherboard, so perhaps the audio is shot.  Oh well.

I think I'll just pick up a Creative Audigy SE, which I know works well with Linux.

---

### Post by kerry_s on 2008-11-02
> **Gauvenator said:**
> Unfortunately the audio is not working.  It is an old motherboard, so perhaps the audio is shot.  Oh well.

I think I'll just pick up a Creative Audigy SE, which I know works well with Linux.

in terminal:
su
alsaconf

reboot

then try alsamixer
crank them all up, make sure the green, if its black its muted, press "m" to unmute.

---

### Post by Gauvenator on 2008-11-04
> **kerry_s said:**
> in terminal:
su
alsaconf

reboot

then try alsamixer
crank them all up, make sure the green, if its black its muted, press "m" to unmute.

Didn't work...I'm just buying a new sound card for my main pc (An Asus Xonar D1) and putting the Audigy SE in this htpc.  I've been wanting a new soundcard anyway.

---

