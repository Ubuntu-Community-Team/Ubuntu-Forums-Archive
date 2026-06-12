---
title: "I tried every available option and still no mouse...."
date: 2004-12-06
forum: Hardware &amp; Laptops
---

### Post by jglerner on 2004-12-06
Hi guys!

As I boot after installation and general update/upgrade all I get is a frozen mouse, no matter which command is issued.

I have tried every single option from 
```
$ sudo dpkg-configure xserver-xfree86
``` 
concerning mouse options at no avail.

That's an ordinary PS2 mouse ( I' ve tried also an optical M$ Intellimouse mouse) and nothing unnusual,  an Asus MB, P3 1Gb, 512Mb DDR, an ATI (Rage) videocard., HD and CD-Rom.

I'm out of ideas...

Regards,

Jacques

---

### Post by Tyche on 2004-12-26
I've run into this problem a couple of times  ](*,)  and finally figured out what MY probelm was.  I have a "Aiptek HyperPen" graphics pad attached to a USB port.  Both Knoppix and Ubuntu, during boot up, see that as a mouse and ignore the regular PS/2 mouse port, hence what appears to be a lock-up.  I disconnected the pen tablet and re-booted, and had no problem.

FYI - I am running this off an Ubuntu LiveCD.  I have been looking around for alternate distros since FedoraCore2 doesn't recognize that NVidia GForce4 is a valid video card and I wanted to move up to a more recent kernal.  This is the first LiveCD I've tried that actually was able to find my network and allow me access to the outside world without jumping through hoops and negotiating land mines.  As a result, I will probably install the full version of Ubuntu on my dual boot system and recommend it to my friends.

Hope this helps,

Tyche
Craig A. Eddy

---

