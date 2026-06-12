---
title: "intel HD 5500 graphics, choppy video"
date: 2015-09-23
forum: Hardware
---

### Post by jaarvidsen on 2015-09-23
hi, i just got myself an ultrabook with 5. gen Intel Core&#8482; i7-5500U prosessor 2.4GHz ~ 3.0Hz cpu and Intel HD Graphics 5500 and im running 14.04 lts

im  very pleased with it except its graphics performance, i cant really  watch videos on it. it runs for a bit then stops briefly, then runs  again, it gets rather annoying, like a dodgy stream (except its not, ive tried several videos, avi etc, its always the same problem)

im wondering if this is to be  expected with this kind of hardware or if it is supposed to run videos  smoothly, and if it is then what can i do? i noticed i dont have an  xorg.conf

thanks

edit: ive tried both totem and vlc, as well as youtube, same problem whatever i do

---

### Post by ajgreeny on 2015-09-23
It looks to me as though you may need to make sure you have the 15.04 hardware enablement stack [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) tells you about how to do that in trusty.

It appears that Ubuntu 15.04 does not suffer in this way, so I think just keeping 14.04 but updating to the hardware enablement stack for 15.04 should overcome the problem for you.

There is also a possible workaround by creating an /etc/X11/xorg.conf file  to replace SNA graphic acceleration and return to UXA acceleration, though it may have some other performance problems.  See [https://wiki.archlinux.org/index.php/Intel_graphics#SNA_issues](https://wiki.archlinux.org/index.php/Intel_graphics#SNA_issues) if you want to try that.  If it does not work as you wish just remove the xorg.conf file then logout and in again.

---

### Post by jaarvidsen on 2015-09-23
@ajgreeny
thanks a lot for you reply
method 1 - the 1504 hw enablement stack - made no difference :(
method 2 - uxa - made no difference :(
i rebooted after both changes

i also tried xubuntu 15.04 live from a usb3 stick, it had exactly the same problems :/

do we know that this hardware ive got is supposed to be capable of displaying video smoothly @1920x1080 ?

---

### Post by mörgæs on 2015-09-24
For Intel HD I agree that it's a good idea to try the latest releases of Buntu but I would go a little further. Have you tried [15.10 (beta)]("http://cdimage.ubuntu.com/lubuntu/daily-live/current/") in a live boot?

---

### Post by monkeybrain20122 on 2015-09-25
Maybe you can try 15.04 with the development driver. [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by jaarvidsen on 2015-09-25
thanks for all suggestions

good news, fired up ubuntu mate 15.10 beta2 on live usb3 stick and all is very smooth and just as it should be :)
thanks all

---

### Post by mörgæs on 2015-09-25
Good, enjoy! New hardware should always run with the newest of software in order to get the best support. 

Though, remember that 15.10 is a work in progress, and though the risk is small at this point in the development cycle it could still break. Always back up important files.

---

