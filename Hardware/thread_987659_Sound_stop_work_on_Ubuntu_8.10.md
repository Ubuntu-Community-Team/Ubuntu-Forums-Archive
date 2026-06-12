---
title: "Sound stop work on Ubuntu 8.10"
date: 2008-11-19
forum: Hardware
---

### Post by jmarques on 2008-11-19
Hello,

I install Ubuntu 8.10 in my notebook HP Pavillion DV6120us, and the sound work very well, but after a few days its stop to work, my sound card is:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I try change sound configurations, but no one work.

Can any one help me?

Thanks.

---

### Post by CyberPrime on 2008-11-19
I am having a similar problem here:
[http://ubuntuforums.org/showthread.php?p=6214145#post6214145](http://ubuntuforums.org/showthread.php?p=6214145#post6214145)

Are there any similarities to yours?

---

### Post by jmarques on 2008-11-21
Yes, this is similar with my problem, but how could I uninstall pulseaudio?

---

### Post by gusto5 on 2008-11-21
I also have this problem. reinstalling pulseaudio does not seem to aid in any way.

---

### Post by Afanluc on 2008-11-22
Well, I have a Toshiba laptop and had the same problem, with 8.10 sudendly no sound.

First, in a terminal type 'groups' and see if you have audio there. If not, then go to preferences, users and groups and be sure that your user is allowed to use sound devices (that was one problem I had!).

Then, at sound configuration I changed the autodetect to ALSA. Note that at first it DID NOT work, and I got a continues annoying beep from PCM after closing session and login again.. but after reboot everything was perfect (I am not sure why, but it worked for me).

---

### Post by jmarques on 2008-11-23
Hi,

I do this but does not work too.

---

### Post by jmarques on 2008-11-23
Finally I got make the sound work.
I found that the problem is with the device number assignment, I change the option:
from options snd-usb-audio index=1 to **options snd-usb-audio index=0** in /etc/modprobe.d/alsa-base file. And after reboot the sound work very well.

Thanks for all.

---

