---
title: "Strange graphics problems"
date: 2010-05-17
forum: Hardware
---

### Post by delsydebothom on 2010-05-17
First, I'd like to ask how to check what graphics card I have. I know it's an Nvidia, and that it is using the proprietary drivers, but I don't know how to find out which model it is :\

Anyway, I'm using Ubuntu 10.04, 64-bit. Upon restarting the computer, the Ubuntu logo flickered on and off, and the system sent me to text mode. I had to restart the computer several times for it to boot into gnome, and even then the logo flickered severely. It isn't flickering now, but I'm paranoid about turning the computer off. I shouldn't have to for a while, but would someone be kind enough to help me narrow down the problem? Thanks so much!

---

### Post by jbrown96 on 2010-05-17
You can check with ```
lspci | grep VGA
``` How did you install the Nvidia drivers? Do you use ethernet or wireless, and do you have access to ethernet?

---

### Post by delsydebothom on 2010-05-17
> **jbrown96 said:**
> You can check with ```
lspci | grep VGA
``` How did you install the Nvidia drivers? Do you use ethernet or wireless, and do you have access to ethernet?

The output says "00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)"

I have an ethernet connection. When I first installed Ubuntu about two weeks ago, it asked me if I wanted to install the proprietary drivers for my card. I did this, and used the driver labeled "current version". It hadn't given me any trouble until today.

---

### Post by jbrown96 on 2010-05-17
You need to use the legacy version. In system-->admin-->hardware drivers, there may be two versions available. You do not want the version that's like 190 or 195. Go with something like 76 or a low number.

Edit: it may be version 96.

---

### Post by 2hot6ft2 on 2010-05-17
We think we found the fix for nvidia.
First if using 64 bit you want to install the driver using the 2.6.32-21 kernel NOT the -22 kernel. We have tried pretty much every fix we could find and this one is looking like the best one yet.

So here's the fix.
[http://ultimateeditionoz.com/forum/viewtopic.php?f=69&t=1112](http://ultimateeditionoz.com/forum/viewtopic.php?f=69&t=1112)

Replace the 2.6.32-22 kernel with the server kernel
```
sudo apt-get purge linux-headers-2.6.32-22 linux-image-2.6.32-22-generic
```
when that finishes install the server kernel per Blackwolfs's instructions
```
sudo apt-get install linux-headers-server linux-image-server linux-server
```
You will have to reboot after it finishes.
That's it.
Let us know if it works or not for you, so far we're getting good results and we want this bug squashed.
:guitar:

---

### Post by manilaph on 2010-05-27
Hi,

Mine is
```
sgo@sgo-laptop:~$ lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)

```

At first I could not boot with the livecd but saw a fix that told me to write "nomodeset" etc.

This is my 2nd fresh install of 10.04. The first one, I installed NVIDIA and then I could not see anything and then I could not find a fix.

This time around, I did not install any NVIDIA drivers but I get a "low graphics" pop-up everytime I boot but this is far better than having no screen. I do not mind the "low graphics" notice because the screen looks perfectly correct so far.

---

### Post by jmarz on 2010-05-27
thanks to those that posted about it - I finally got my set up fixed so I don't have to mess with the low graphics notice

one member posted this-
[1) Hold down Shift while booting to get to grub.
2) Press 'e'. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to boot.
]]

I just let it go to grub and then hit the e key

use the dn arrow to get to the line that has the quiet splash
use arrow key to get to the words quiet splash and delete them and type in nomodeset
then do #3

after the reboot I still did have the low graph notice.

so i went to synaptic and removed all nvidia drivers -
used the search there to find it fast
did a reboot and still had the notice.

went back into synap and reloaded all nvidia stuff- clicked to sort by newest

and reinstalled a lot of the nv stuff from the top of that list - unless the description made me think it wasn't what i needed

did a reboot then - and finally it all worked and no stupid notice.


good luck I hope it works for you- I've been messing with trying to fix mine on & off for a month or so

Dual boot Ub 10+ with XP 


**************

with the flicering I was thinking it might be a bad connection somewhere...

---

