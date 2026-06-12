---
title: "USB Gamepad Problems"
date: 2008-08-05
forum: Hardware
---

### Post by Woolfenstien on 2008-08-05
Earlier today I tried to install drivers for my XBox 360 wired controller using [this guide](https://help.ubuntu.com/community/Xbox360Controller) on my Ubuntu 8.04 Dell Inspiron 1525, since up and down on the left analogue stick was swapped (down was up, up was down).  However, when I got to the part where I had to run "sudo depmod -a" it returned 'Segmentation fault', so I ran it again only for the command to hang (I assumed it should need to run for over 10 minutes).  I tried installing again from the beginning, however modprobe just hangs whenever I tell it to do anything, so I gave up trying to install the drivers, and went back to my old controller (Logic3 USB Intruder, which works flawlessly with Ubuntu), but now this controller isn't working either.

I've tried unplugging and plugging in again, restarted the laptop, and using a different USB port, only to have both controllers not work.

So I guess I'm looking for a way to either undo whatever I did wrong while following the guide, or a way of doing the guide right and getting support for my XBox 360 controller.

If you need any more information, please don't hesitate to ask.

Thanks in advance for any help.

---

### Post by matt.taylor on 2008-08-05
I would get rid of these 2 drivers that you installed like this;

```
sudo apt-get uninstall jscalibrator libgii1 libjsw2
```

```
sudo apt-get uninstall linux-headers-`uname -r` build-essential automake1.9
```

It looks like these drivers messed the exisiting ones up, so i would take them off and plug the one that works back in and see if that has an effect.

Good Luck :popcorn:

---

### Post by Woolfenstien on 2008-08-05
I had to use the 'remove' option for apt-get because 'uninstall' was an invalid operation?

Anyway, I ran the two commands you posted, and neither controller is working still, even after plugging them in again.

---

### Post by matt.taylor on 2008-08-05
remove , uninstall i have been knee deep in windows dll hell and registry for hours. My brain is in Microsoft mode ](*,)

Next step is to move to the xpd directory 

```
cd xpad
```

Then,

```
sudo make uninstall
sudo modprobe -r xpad
sudo depmod -a
sudo modprobe xpad 
```

This should take off the rest of it (i think) the problem by following that method is that it removed everything eles and just left you with this drivers for an xbox pad.

If the above does not work, im sure somone will give you the code to do so. I can't think must go back to work im affraid :'(

---

### Post by Woolfenstien on 2008-08-05
Okay, I cd'd to the xpad directory, and 'sudo make install' ran fine.  However, 'sudo modprobe -r xpad' has either hung or is taking ages to do what it's meant to be doing.  How long does the average 'modprobe -r' take?  Also, 'modprobe xpad' also seems to do nothing, however it doesn't return "FATAL: Module xpad not found.", or any message for that matter...

I'll edit or post again if modprobe -r xpad completes.  Thanks for the help Matt.

---

### Post by matt.taylor on 2008-08-05
No problem, as i say im at work at the minute, ill give it whirl when i get home. 

You may have to re-install the old drivers to make the old controller work again. But hey thats part of the fun!:lolflag:

---

### Post by Woolfenstien on 2008-08-05
How would I go about installing either the old drivers or the current version of drivers without messing up?  It's not under the package manager on my computer.


Also, it definitely seems as if modeprobe-ing anything that has to do with xpad makes it hang.


Another thing is that whenever I sudo anything, it always says "sudo: unable to resolve host laptop", however the command I've sudo'd still seems to run fine.  Is this something that might be related to the problem?

---

### Post by Woolfenstien on 2008-08-07
Hello again,

I managed to get the pad working... Somehow.  I left it a few days, plugged in my Xbox360 controller, opened JSCalibrate, and everything was fine - all I had to do was flip one of the axes.  My other pad also works now too!  Great news, since I'm going on holiday and need something to do on the plane :D

So problem(s) solved, I guess

---

