---
title: "How to select default sound device?"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by Gianni Exile on 2005-04-08
My machine has multiple sound cards installed.  The default chosen is the low-quality motherboard sound device.  I would like to use /dev/dsp2 as the default sound device.  

My current solution is to write an init script (running as root)  that renames the boot-time defaults and symlinks the desired device.

```
for f in dsp audio mixer ; do 
    mv /dev/$f /dev/${f}0 ;
    ln -s /dev/${f}2 /dev/${f} ;
done
```
where the device I want to use comes up as device 2.

Debian/ALSA/Gnome-specific info is here: 
[http://lists.debian.org/debian-user/2005/02/msg00766.html](http://lists.debian.org/debian-user/2005/02/msg00766.html)
[http://lists.debian.org/debian-user/2005/02/msg00768.html](http://lists.debian.org/debian-user/2005/02/msg00768.html)

So, my question is
** What is the Ubuntu way of dealing with this??**

---

### Post by dukeinlondon on 2005-04-08
> **Gianni Exile]My machine has multiple sound cards installed.  The default chosen is the low-quality motherboard sound device.  I would like to use /dev/dsp2 as the default sound device.  

My current solution is to write an init script (running as root)  that renames the boot-time defaults and symlinks the desired device.

```
for f in dsp audio mixer  said:**
> http://lists.debian.org/debian-user/2005/02/msg00766.html[/url]
[http://lists.debian.org/debian-user/2005/02/msg00768.html](http://lists.debian.org/debian-user/2005/02/msg00768.html)

So, my question is
** What is the Ubuntu way of dealing with this??**
 Yeah, I'd like to know too.

---

### Post by Gianni Exile on 2005-04-09
I put the above snippet in at the bottom of /etc/init.d/bootmisc.sh , FYI.
Works fine.

Only for ALSA apps do I need to set anything, and usually that can be chosen by the card model.

---

### Post by Gianni Exile on 2005-04-23
Okay, I got it.

Use the above to get OSS apps working (from first post, put in /etc/init.d/bootmisc.sh

Then run: "sudo vi /etc/asound.conf" and place the following there: ```

pcm.!default {
	type hw
	card 2
}

ctl.!default {
	type hw           
	card 2
}

```
Replace "2" with your card number (usually 1 2 3 or 4).

Run "sudo /etc/init.d/alsa restart".

Now alsa apps will default to your chosen device, as will OSS ones.

To avoid conflicts, add to  /etc/esound/esd.conf ```

default_options=-nobeeps -as 3

```

which will tell ESD to release the sound device when not in use.

Also run:
sudo apt-get install libesd-alsa0  esound-clients

Now ESD will use the ALSA device.

---

### Post by rmax75 on 2005-04-23
Very thanks for your help. :razz: 

It work great for my configuration with 6 audio device!!!
3 OSS mixer + 3 Alsa mixer
(1- VIA AC97, 2- SB LIVE, 3- BT878 TV CARD)

---

### Post by Gianni Exile on 2005-04-23
Other posts on this topic

general sound setup
[http://ubuntuforums.org/showthread.php?t=26567](http://ubuntuforums.org/showthread.php?t=26567)

2 sound cards
[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)

Note: I don't agree with the advice in these other threads because it doesn't work for me.... auto-spawning ESD causes choppy out-of-sync sound, and ESD doesn't release the device when it's done.  The settings given for /etc/asound.conf also give slow sound (period_time / period_size / buffer_size / periods), however the defaults work for me.

I have hardware mixing on my card, and directly using ALSA works fine, and flash, ESD, ALSA, and OSS applications all work together using the three steps I list here: adding the lines to /etc/init.d/bootmisc.sh, and to  /etc/asound.conf, and installing the esd-alsa library.

Note #2: I use the kernel OSS layer (alsa-oss isn't installed), that may be an option to try -- but everything works fine for me as is.

Note #3: For gnome apps, run gstreamer-properties and set output to ALSA, in KDE use kcontrol /  Sound & Multimedia / Sound system.

Linux sound is a mess!!

---

