---
title: "LG X110 Usb problems with 9.10 (not with 9.04)"
date: 2009-11-18
forum: Hardware
---

### Post by xvilar on 2009-11-18
I've a LG X110 Netbook and I'd installed few month ago Ubuntu Desktop 9.04.

All run OK, included the Usb connectors: I was able to connect, disconnect and re-connect an usb pendrive* and ubuntu mount it so well... I'd an usb optical mouse that works well after boot, and i can unplug it during a session and plug it again, and it works.

I upgraded to 9.10 (later I've installed completly 9.10 too) and i cannot get work well the same Usb connectors ... if i connect the same pendrive* ubuntu doesn't mounts it... so i cannot use it. I've an usb optical mouse that works well after boot, but if i unplung it during a session and plug it again it doens't work!!! 

I've tried to boot with kernel parameter "irqfixup" but i've the same problems.

I've tried too to include my user in the "lp" group (i've read that it affects) but i've the same problems again.

So what i can do to use so well Ubuntu 9.10 in a LG X110? 

By the way, temporally i'm working again with 9.04.

Thnx in advance!

---

### Post by xvilar on 2009-11-26
Nobody has nothing to say?¿¿¿¿

---

### Post by ilyail3 on 2009-11-27
exactly the same problem here(with exactly the same hardware).

Nobody have an idea why this is happening?

---

### Post by Ylon on 2009-11-27
Based upon [this bug notify](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455408)... the problem is made by a integrated webcam.

On a MSI netbook someone reloved this way:
( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455408/comments/13](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455408/comments/13) )

> Isn't this the same as bug #435352 ? Im on a MSI W100, clean Karmic alpha install. Since last week's update, can't see USB devices (nothing on dmesg when i plug them in), and can't suspend. There are at least 2 workarounds proposed (no true solutions yet), that make USB ports usable. One is downgrading usbutils to Jaunty. haven't tried that. The other is blacklisting the conflicting uvcvideo module ("blacklist uvcvideo" in /etc/modules) making built-in camera unusable, but restoring full USB and suspend functionality. it worked for me.
Hope they fix this issue before release.

You can try downgrade usbuitls to jaunty, or blacklist the driver of the webcam.

---

### Post by xvilar on 2009-12-04
Thnx Ylon, but i think it will be better than Ubuntu Dev team solves this bug, isnt it?

Regards!

---

### Post by likebikes on 2009-12-04
I have a MEDION E1210 (copy of MSI Wind) and have been having same problems with USB memory sticks. However, i have applied'blacklist uvcvideo to /etc/modules.... and low and behold on re-boot not only do the USB sticks now get mounted but the integrated web cam still works.

good times!

---

### Post by Seb33300 on 2010-01-20
Hello, I have a Medion E1210 too and have the same problem !

But I don't know how to blacklist uvcvideo on /etc/modules.

Can you explain me please ? I'm beginner with linux.

Thanks

---

### Post by likebikes on 2010-01-20
> **Seb33300 said:**
> Hello, I have a Medion E1210 too and have the same problem !

But I don't know how to blacklist uvcvideo on /etc/modules.

Can you explain me please ? I'm beginner with linux.

Thanks

ok.. welcome to Ubuntu i to am a bit of a beginner and copied this fix from someone else.

first go to 'applications'---->'Accessories'--> 'Terminal'

then type: sudo nano /etc/modules
it will ask you for a password. this is the same one you use to login

after you have done this you should get:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
blacklist uvcvideo
lp


you then need to use the arrow keys on your keyboard to get down to a space between 

# at boot time...

and 
lp

as you can see i have put 'blacklist uvcvideo' in this space

then press the 'Ctrl and letter 'o' key together
then hit return
then hit ctrl and letter x key together

this will then close the 'Terminal' window.

restart your netbook

and hopefully now your USB pendrives and sd card reader will be seen. However. This DOES disable your Cam i was wrong before about the cam still working.

Please be aware this is a work around for a known bug. hopefully soon it will get fixed.

---

