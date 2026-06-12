---
title: "Headphones No Sound"
date: 2009-04-29
forum: Hardware
---

### Post by screaminj3sus on 2009-04-29
My Headphones do not work AT ALL. they used to work in 8.10 as long as they  were plugged in while it was booting (but if you take them out you had to restart with them in again)

In 9.04 they do not work at all, I jave tried unmuting every channel ect.. in the mixer but nothing works and there is no headphone channel or anything similar.

Mixer screenshot:
[http://i43.tinypic.com/2zfn8ux.png](http://i43.tinypic.com/2zfn8ux.png)


I am running Ubuntu 9.04 64 bit on a gateway m6862 laptop. any way to get my headphones working?

---

### Post by jhann on 2009-04-29
Yeah i'm having the same problem myself running Ubuntu 9.04, I haven't tried booting with the headphones in though.
I can play music from the laptop speakers but not with the headphones plugged in.


*EDIT* I just restarted with the headhones plugged in and they still don't work

---

### Post by screaminj3sus on 2009-04-29
Yeah I can play sound via the laptop speakers as well, and when I put my headphones in it even stops playing sound from the speakers like it detects them being in but no matter what I get no sound through them.

Any help would be appreciated.

---

### Post by flipper9 on 2009-05-03
I had the same problem with my Asus Eee PC 1000h where I could get sound out of my laptop speakers, but not when I plugged in headphones.  I found a thread somewhere that told me to add...

[php]options snd-hda-intel index=0 model=basic[/php]...to the end of my "/etc/modprobe.d/alsa-base.conf" file.

After a reboot (I think there is a way to do it without rebooting, but I forget) I got sound, and had more options in the volume control panel.  This might not work for your particular laptop model, but might point you in the right direction.

---

