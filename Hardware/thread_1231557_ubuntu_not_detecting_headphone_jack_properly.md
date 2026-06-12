---
title: "ubuntu not detecting headphone jack properly"
date: 2009-08-04
forum: Hardware
---

### Post by gravity_blast on 2009-08-04
i plug in my headphones and it plays the audio out of them and the speakers

---

### Post by Yanatsu on 2009-08-04
Make sure they're plugged in all the way (wiggle them and plug them in harder, turn, whatever), and failing that, right click on the volume control, and fiddle with the mixers-one might work better with your hardware than another.

---

### Post by gravity_blast on 2009-08-04
already done all that sh*t bro, same deal

---

### Post by Yellow Pasque on 2009-08-04
Your jack sensing isn't working properly. You probably need to specify the model in /etc/modprobe.d/alsa-base.conf

There's also a chance you'll need a newer version of ALSA: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

More info is needed, like what kind of laptop or system you have and what audio codec it uses.

---

### Post by Yanatsu on 2009-08-04
You did the mixers and all, or just playing with the cable?
As he said, updating ALSA may do you good.

---

### Post by gravity_blast on 2009-08-04
> **Temüjin said:**
> Your jack sensing isn't working properly. You probably need to specify the model in /etc/modprobe.d/alsa-base.conf

There's also a chance you'll need a newer version of ALSA: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

More info is needed, like what kind of laptop or system you have and what audio codec it uses.

the model of what? i have no idea what that means dude

and my desktop is just a p4 with 3gb ram and a x1950with some realtek junk. im not using it at this sec so thats about all i can say

---

### Post by gravity_blast on 2009-08-04
> **Yanatsu said:**
> You did the mixers and all, or just playing with the cable?
As he said, updating ALSA may do you good.

both

---

### Post by biggerben on 2009-08-04
try going through alsamixer and muting and unmuting all the items there. I once had a "headphone jack" or something that if left "unmuted" gave me the same problems you seem to be having.

---

### Post by Yanatsu on 2009-08-05
I would say to update the ALSA drivers.
If you have a Conexant card, you can get updates [here.]("http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86.php")

---

