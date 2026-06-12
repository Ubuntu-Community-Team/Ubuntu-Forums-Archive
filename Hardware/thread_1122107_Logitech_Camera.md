---
title: "Logitech Camera"
date: 2009-04-10
forum: Hardware
---

### Post by exell on 2009-04-10
Hello I am relatively new to Ubuntu, and so far so good, but the odd things wont work like my webcams. I have a logitech camera and I was wondering if there is any "easy" way to get the camera working?

---

### Post by starcannon on 2009-04-10
Many of the logitech camera's "just work" and many more are easy to get going; which one do you have?
lets have a peek at the output of:
```
lsusb
```
And also be sure to include any details you know about the camera; things like, model, version, revision, etc...

GL

---

### Post by exell on 2009-04-10
Ehm I would if i could but i dont know what you mean by the outlook of liusb if you mean terminal? sorry but i cant find it lol.... I have no clue on the model... but it looks like a ball

---

### Post by exell on 2009-04-10
Got the terminal and got thwese results


Bus 002 Device 008: ID 093a:2460 Pixart Imaging, Inc. Q-TEC WEBCAM 100
Bus 002 Device 006: ID 05ac:0306 Apple, Inc. Optical USB Mouse [Fujitsu]
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


please note pixart is another webcam i cant get working

---

### Post by starcannon on 2009-04-10
Is the logitech webcam plugged in right now?
Is the logitech webcam plugged in through that hub? if so can you plug it in directly for now?
I'll dig around for some Pixart info as well.

GL

---

### Post by exell on 2009-04-10
Bus 002 Device 009: ID 046d:08f6 Logitech, Inc. Quickcam Messenger Plus
Bus 002 Device 006: ID 05ac:0306 Apple, Inc. Optical USB Mouse [Fujitsu]
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by starcannon on 2009-04-10
Here's a guide that has the Pixart cam, it is translated from German.
[http://translate.google.com/translate?hl=en&sl=de&u=http://wireless.subsignal.org/index.php%3Ftitle%3DDave%27s_Web-Log&ei=xMLfScnnG4TwtAOAuIitCQ&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3DBus%2B002%2BDevice%2B008:%2BID%2B093a:2460%2BPixart%2BImaging,%2BInc.%2BQ-TEC%2BWEBCAM%2B100%2Bubuntu%26hl%3Den%26sa%3DG](http://translate.google.com/translate?hl=en&sl=de&u=http://wireless.subsignal.org/index.php%3Ftitle%3DDave%27s_Web-Log&ei=xMLfScnnG4TwtAOAuIitCQ&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3DBus%2B002%2BDevice%2B008:%2BID%2B093a:2460%2BPixart%2BImaging,%2BInc.%2BQ-TEC%2BWEBCAM%2B100%2Bubuntu%26hl%3Den%26sa%3DG)

GL

---

### Post by exell on 2009-04-10
Sorry dude but that is beyond what i am capable of... But I must thankyou for your help

---

### Post by starcannon on 2009-04-10
Perhaps try this first, it could be a nice solution to both of your cameras:
[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

GL

---

### Post by exell on 2009-04-10
I dont understand what any of that means apart from adding repostories which I knew how to do previously

---

### Post by artsci2 on 2009-04-11
I tried to add the "blognux" software sources given in the instructions for Easycam and recieved a "Could not download all repository indexes" for the two new added repositories.

Could somone verify this?

---

### Post by executorvs on 2009-04-12
the sources I used this morning on an intrepid box were:
   deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
   deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
there is no repo key needed

Then just use the package manager, System-->Administration-->Synaptic package manager, and search for easycam if you are using ubuntu install the easycam2-gtk package and if you're using Kubuntu install the easycam2-qt package

this does not work yet for Jaunty, I'm trying to find a work around. so if anyone knows a work around for jaunty please share.

---

