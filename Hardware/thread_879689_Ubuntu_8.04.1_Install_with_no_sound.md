---
title: "Ubuntu 8.04.1 Install with no sound"
date: 2008-08-04
forum: Hardware
---

### Post by jaroon on 2008-08-04
Just did my first, and 2nd thru 6th, install on my new latop.  The OS is picking up the sound card but I get zero sound with it.  Used alsamixer and the gui volume control to unmute it.  My best guess is that it is my add on thing on the left side of the keyboard with this laptop, [http://www.newegg.com/Product/Product.aspx?Item=N82E16834115486](http://www.newegg.com/Product/Product.aspx?Item=N82E16834115486).  I was reading through the common sound issues page and found no solution so I figured it was an install or update bug and reinstalled, several times.  No dice.

---

### Post by silvanus2005 on 2008-08-04
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
See there.

---

### Post by FTBPrimeEvil on 2008-08-04
Sound fix for my laptop was to edit:
/etc/modprobe.d/alsa-base and add the line,
"options snd-hda-intel model=mbp3"

What sound card do you have? if it is an HDA Intel this should work for you.

---

### Post by jaroon on 2008-08-04
I tried to do the change to the alsa-base and got a permission error.  do i need to log in as root, if so, how do i do this?

edit: I do have the hda intel sound card

edit: I used nano to open the file up, only way i knew how to.  if there is a better way, do tell.

---

### Post by jaroon on 2008-08-04
used sudu -s to login as root, changed the file, no luck.

do i have to activate the change? did a reboot and unmuted everything i could in the alsamixer and unmuted and maxed the gui volume control.

---

### Post by jaroon on 2008-08-04
just tried to change the alsa-base with the option labeled in [http://www.tellmehow.nl/?p=8](http://www.tellmehow.nl/?p=8), used the acer tag, rebooted, no luck. this is driving me crazy to have to reboot to watch vids and stuff on windows

edit: model is ALC883

edit: its ALC889 and i've been stressing about making this work with the 883 codec for like 30 hours of no sleep of frustration, i'm gonna go pass out and start lookin for solutions for the 889 when i get up, thanks for tryin to help.

---

### Post by Nepherte on 2008-08-04
Run this in a terminal to figure out the exact codec the sound card is using:
```
cat /proc/asound/card0/codec#* | grep Codec
```

Search at [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt) for (a part of) your codec. Take the model value that reflects your laptop the most. Then change your alsa-base configuration file to resemble:
```
options snd-hda-intel model=MODEL
```

---

### Post by mCion on 2009-02-07
I love you guys!!!, fixed my problem too.

nice explenations and Howto, specially for a noob like me.  

thanks again!

---

