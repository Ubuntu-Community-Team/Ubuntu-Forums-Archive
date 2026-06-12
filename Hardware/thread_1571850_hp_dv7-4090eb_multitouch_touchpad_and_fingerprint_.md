---
title: "hp dv7-4090eb multitouch touchpad and fingerprint reader"
date: 2010-09-10
forum: Hardware
---

### Post by warddr on 2010-09-10
Hello all,

I got ubuntu working on my new hp dv7-4090eb notebook, there are only some minor issues I couldn't solve, anyone any solution?:
1. My touchpad is working, but multi-touch isn't supported (wrong driver?)
2.  (less important) my fingerprint reader doesn't work
I found this in the specifications:

# Touchpad: HP Clickpad with Multi Touch

---

### Post by warddr on 2010-09-13
anyone?

---

### Post by daigorobr on 2010-09-14
I've been looking for the info lately. Guess our train is too early and we'll have to wait for the support.

---

### Post by Carl.Spackler on 2010-09-18
Not sure about the multi-touch on the trackpad but I believe the fingerprint reader is not supported. You may want to check to make sure that you have the same reader that I have in my dv7-4060us to be sure. Should be a Validity VFS101 or 201. According to the last wiki I read, this is not supported.
 
lsusb should show a Digital Persona Fingerprint Reader but it's real name is Validity.
 
[http://www.validityinc.com/default.aspx](http://www.validityinc.com/default.aspx)
 
Question though: How did you handle the ATI hybrid graphics? Did you get the accelerated driver to load using the 5650 chip?

---

### Post by vedovatti on 2011-04-10
Hi there

If you have the VFS101 fingerprint reader it has been fixed.

Check this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089)

add the ppa and it will work.

About the multitouch, there is a package dkms-synaptics that enables the basic multitouch and works ok.

And about the ATI hybrid graphics is not possible to use the accelerated property driver on hybrid cards. You have to use the xorg driver and it supposed to be supported 3d accelerated on Ubuntu 11.04.

---

