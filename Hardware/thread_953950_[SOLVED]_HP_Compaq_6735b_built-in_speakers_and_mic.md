---
title: "[SOLVED] HP Compaq 6735b: built-in speakers and microphone not working"
date: 2008-10-20
forum: Hardware
---

### Post by misiu369 on 2008-10-20
**EDIT**: Problem solved, check my next post.

It's actually the first time I'm posting a question, but I've given up. Can't find any solution to my problem after googling and testing for nearly two weeks now...

I've bought a **HP Compaq 6735b, model KU211EA**, natively with Vista (still there just in case).
The problem is, I've got sound and microphone working only by plugging in headphones and microphone. It seems Ubuntu "can't switch" to built-in speakers and microphone when I have nothing plugged in (of course, they work fine under vista).

I know there's a lot of post about it, but none I've found helped.
I've tried putting "options snd-hda-intel model=*XYZ*" in *alsa-base* with some random (from ALSA-Configuration.txt) values instead of *XYZ*, but as I can't identify the exact sound chipset, didn't check all the possible options.

I'd be greatful for any help you can give me...



The notebook is based on chipsets: AMD M780G SB700

Here's info about the sound card:```

**$ lspci | grep -i audio**
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia

**$ cat /proc/asound/cards**
0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd6500000 irq 18

**$ head -n 1 /proc/asound/card0/codec***
==> /proc/asound/card0/codec#0 <==
Codec: Analog Devices ID 194a
==> /proc/asound/card0/codec#1 <==
Codec: Generic 11c1 ID 1040
```

If any more info is needed, just let me know.

Thank in advance, even for the time spent reading. ;)

---

### Post by linux_tech on 2008-10-20
If your audio is ADI SoundMAX AD1984A Audio
then this post may help, working with the alsa-driver-1.0.16
[http://ubuntuforums.org/showthread.php?p=4937154](http://ubuntuforums.org/showthread.php?p=4937154)

For alsamixer info
- [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
- [http://man-wiki.net/index.php/1:alsamixer](http://man-wiki.net/index.php/1:alsamixer)
- [http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/)

---

### Post by misiu369 on 2008-11-10
> **linux_tech said:**
> If your audio is ADI SoundMAX AD1984A Audio
then this post may help, working with the alsa-driver-1.0.16
[http://ubuntuforums.org/showthread.php?p=4937154](http://ubuntuforums.org/showthread.php?p=4937154)
Tried it. Didn't work.

Besides, I've got no idea what audio chipset I've got. That code I've pasted is all I've found out.

**EDIT:** Just found drivers for my laptop on hp site. Turns out it is ADI SoundMAX AD1984A. Gonna try this method again, maybe I've missed something....

**EDIT2:** Well, it still didn't work, but once I knew what driver to look for, I found out that all problems were fixed in alsa-driver-1.0.17. 
I followed [these](https://wiki.edubuntu.org/LaptopTestingTeam/HP2133#line-477) instructions (Drivers and fixes / Audio driver), only with 1.0.18.

After reboot new options showed up in alsamixer, and built-in microphones are working as well. I only had to change the default mixer to a different device, because it went crazy on the basic one - you'll figure it out.

Finally got my speakers working! :D

<snip snip>

---

### Post by pmuflon on 2008-11-12
Hi,
   unfortunately i have the same problem as you. I have one question - when you followed [these]("https://wiki.edubuntu.org/LaptopTestingTeam/HP2133#line-477") methods which parameters did you use in ```
./configure --with-cards=?
``` and in ```
options ? model=hp
```

I also don't have folder named 'ubuntu' which is mentioned in that instructions. Maybe because i'm using newer kernel (2.6.27-7) or because i'm using kubuntu (8.10)...

Regards

---

### Post by misiu369 on 2008-11-12
> **pmuflon said:**
> Hi,
   unfortunately i have the same problem as you. I have one question - when you followed [these]("https://wiki.edubuntu.org/LaptopTestingTeam/HP2133#line-477") methods which parameters did you use in ```
./configure --with-cards=?
``` and in ```
options ? model=hp
```

just as the linked instructions say:
```
./configure --with-cards=hda-intel
```
and in alsa-base:
```
options snd-hda-intel model=laptop
```

> **pmuflon said:**
> 
I also don't have folder named 'ubuntu' which is mentioned in that instructions. Maybe because i'm using newer kernel (2.6.27-7) or because i'm using kubuntu (8.10)...
can't help you there. just do all the other stuff, reboot, check alsamixer if you have some new options (and if the sound is muted).

if it still doesn't work, try finding all folders named "sound" in /lib/modules/2.6.27-7*

---

### Post by pmuflon on 2008-11-20
hey, thanks for reply.
i found that compilation of alsa-driver wasn't necessary for me and i only needed to add this line in alsa-base file```
options snd-hda-intel model=laptop
```
i also changed kubuntu to ubuntu, because it still isn't enough stable for me

---

### Post by Lindstorm on 2009-06-22
After some googling this seems to be the quick fix to try

gksu gedit /etc/modprobe.d/alsa-base.conf

and then add

options snd-hda-intel model=laptop enable=1 index=0

save & reboot

---

### Post by misiu369 on 2009-06-22
> **Lindstorm said:**
> After some googling this seems to be the quick fix to try
gksu gedit /etc/modprobe.d/alsa-base.conf
and then add
options snd-hda-intel model=laptop enable=1 index=0
save & reboot

You should mention which version of Ubuntu you've got (and which alsa-driver if you've compiled it). 
This thread was written a while back, so things might've changed since then.

---

### Post by magic_din on 2009-08-04
gksu gedit /etc/modprobe.d/alsa-base.conf
and then add
options snd-hda-intel model=laptop enable=1 index=0
save & reboot

also solved my problem .

I have also added my user group in /etc/group for audio
e.g. 
audio: x : 29 :pulse :<user group>  (no space in : and next letter) in my case my user group and user name is same.

---

