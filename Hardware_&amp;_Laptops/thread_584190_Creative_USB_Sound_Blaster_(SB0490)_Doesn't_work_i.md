---
title: "Creative USB Sound Blaster (SB0490) Doesn't work in Ubuntu 7.10"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by nikola.borisof on 2007-10-20
Hi All,

I got from a friend a:

Creative USB Sound Blaster (SB0490) 

I'm using Ubuntu 7.10 and i would like to get sound out of this card. Unfortunately when I plug it into my laptop I don't get anything. Even the lids on the card doesn't lite up. I searched a lot in Google for someone that have this hardware working but no luck. Any ideas will be helpful.

Thanks in advance.

Nikola Borisov

---

### Post by elfstonewise on 2007-12-09
Hi Nikola.

The SB0490 external sound card should work well with linux. Currently I'm listening with amarok and this external audio device.

First try to connect and type in console:
lsusb 

and see what it returns. Maybe you'll must manually load module for this device:
modprobe snd-usb-audio

And there could be problem with having more than 1 sound cards in system. Then you must set the index for each of the cards. I don't know where it is in ubuntu cause I'm using Archlinux. In my OS it's the 
/etc/modprobe.conf

and you should make the options look like this

options snd-usb-audio index=0
options snd-hda-intel model=3stack index=1

the second position is the built-in sound card.
In ubuntu the file should be placed in
/etc/modprobe.d/alsa 
or something like that.


And for the LED not glowing... In linux you can toogle the LED to light or not.
For example the Kmix in KDE can do that and the console alsamixer also. The LED isn't vital for working of this device.

Give feedback if it will work now.

---

### Post by Junho Ryu on 2008-02-06
I'm using the same version(7.10) of Ubuntu. I have no idea what the option means, but it works. Great!

I changed one line in this file
/etc/modprobe.d/alsa-base

from,
options snd-usb-audio index=-2

to,
options snd-usb-audio index=0

Thanks

---

### Post by brandongk on 2008-02-28
This got it working with 2 speakers.  Thanks!

Brandon

---

