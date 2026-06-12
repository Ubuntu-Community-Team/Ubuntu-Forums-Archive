---
title: "Weird Touchpad Issue - Works as root but not in main profile"
date: 2010-06-15
forum: Hardware
---

### Post by tdkx89 on 2010-06-15
I'm running 10.04 on a HP dv6700. My touchpad doesn't work, but the thing is that it used to work. After 10.04 came out, I did a fresh installation: the touchpad worked. I tried the recommended NVIDIA driver and experienced problems with Ubuntu, so I removed it (all through the GUI tools). After this, my touchpad would not work. However, when I boot to the login screen, it works then. If I login as root, I can use it. I can't use it if I log in on my main profile.

I've searched all over for a solution, tried fiddling with synclient and my X settings.

Does anyone know what could be the problem?

---

### Post by PoMeO on 2010-06-16
I have the same problem, notebook HP Pavilion dv6760er, Ubuntu 10.04 .
A couple of days ago touchpad worked, yesterday does not work. In login screen, it works.

---

### Post by kiddykoff on 2010-06-21
something is up. I'm on an hp pavillion dv6815nr. and my touchpad stopped working sometime during the weekend. I didn't realize it until i had to go without my bluetooth mouse.

synclient TouchpadOff=0 in terminal doesn't work, nor does fiddling around in gsynaptics

running xinput list shows me that i have

Virtual core pointer id=2 [master pointer (3)]
 Virtual core XTEST pointer id=4 [slave pointer (2)]
 Macintosh mouse button emulation id=12 [slave pointer (2)]
 SynPS/2 Synaptics TouchPad id=11 [slave pointer (2)]

---

### Post by quirkification on 2010-06-21
I have had this problem too, a little entertaining and a little annoying... But since I looked up any advice two days ago, it has been fine...go figure.:lolflag:

---

### Post by kiddykoff on 2010-06-21
this worked for me.

[http://ubuntuforums.org/showpost.php?p=9172983&postcount=6](http://ubuntuforums.org/showpost.php?p=9172983&postcount=6)

---

### Post by tdkx89 on 2010-06-21
Great Space! It worked! Thank you, kiddykoff.

---

