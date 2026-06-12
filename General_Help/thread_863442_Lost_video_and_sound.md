---
title: "Lost video and sound"
date: 2008-07-18
forum: General Help
---

### Post by equate975 on 2008-07-18
Hello, I'm running 8.04 with an intel ac'97 onboard audio and a nvidia gf2mx440.

Basically I installed virtualbox to work on some stuff, it was complaining that I didn't have the ose modules installed, I installed "virtualbox-ose-modules-2.6.24-19-386" which required a reboot.

When I rebooted my sound card is no longer detected, and my video card is no longer detected. I was using pulseaudio with my sound card before, and I had the nvidia working just fine, something skipped the track and I don't know where to begin.

lspci -i

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

So they are still there, just not working.


Any help would be great, thanks!

---

### Post by Mgiacchetti on 2008-07-18
first of all uninstll all virtualbox ose related software, and go with sun xVM virtualbox.

Second try killall pulseaudio in terminal    (just a guess here)

---

### Post by equate975 on 2008-07-18
Yeah I uninstalled all of virtual box already.

I killed pulse audio, but it still complains that I don't have any sound devices.

---

### Post by Mgiacchetti on 2008-07-18
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by equate975 on 2008-07-18
I've done all of that, it fails when I try to compile from source. none of the other options worked either.

I'm beginning to wonder if the board is just going out. I just lost a stick of ram and nothing I stick in it will work... I've had a few issues in the past and I know its kind of flaky.

---

