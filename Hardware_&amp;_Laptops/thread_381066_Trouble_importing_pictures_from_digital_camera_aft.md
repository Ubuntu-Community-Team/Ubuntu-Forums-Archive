---
title: "Trouble importing pictures from digital camera after libgphoto update"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by glennric on 2007-03-10
Recently there was an update for libgphoto from edgy-backports.  Before the update I had no problems plugging my digital camera into the usb port and copying pictures onto my computer.  After the update I get 

```

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

```

I tried forcing the version of libgphoto back to the previous (edgy) version and it worked fine again.  Oddly enough I have the upgrades installed on two other computers and it still works fine on those.  I thought at first that it might be the kernel I compiled, but it doesn't work on the generic kernel either.  

Any ideas?

---

### Post by Mateusz Ho&#322;ysz on 2007-03-11
I have suffered the same. After upgrade to backported version 2.3.0 it is not possibble to import
photo from Canon S1 IS (ptp mode). 
Program says that usb port can't be reached (used)

Regarding this I prepared bug raport.
[https://launchpad.net/bugs/91265](https://launchpad.net/bugs/91265)

---

### Post by villindesign on 2007-03-11
I am having the same problem after update. See attached

---

### Post by MrFahrenheit on 2007-03-11
dang, I just noticed that I'm having the same problem.  Does anyone know how I can downgrade to the previous version so I can get the pictures off my camera?

---

### Post by villindesign on 2007-03-11
a temporary solution is to use gtkam and run it as su:

$ gksudo gtkam

---

### Post by PrairieShaman on 2007-03-12
Im having this same problem. gonna try and find a way to go back a version of the photo proggy or somethin.... i duno ?

---

### Post by endtroducing on 2007-03-12
Yep same thing here with Canon EOS Rebel xti / Canon 400D! :(

I tried to downgrade the package but that didn't do it.

I backed up, clean installed, left backport commented.

---

### Post by PrairieShaman on 2007-03-13
yeah, i tried going back to 2.21 or whatever the last one was and it didnt work for me either.. any ideas yet? :guitar:

---

### Post by phenest on 2007-03-13
The bug reports reply says it will be fixed in the -Edgy2 release of the backport. What does that mean and when will it happen?

I tried installing the old versions of libgphoto2-2, and libgphoto2-port0, (version 2.2.1-2ubuntu4) but the problem remains.

---

### Post by jackpack on 2007-03-13
Same problem with my Canon S1 IS. Downgrading libgphoto to 2.2.1-2ubuntu4(edgy) solved the problem.

---

### Post by akos on 2007-03-16
I have got the same thing - buggy - with my Nikon Coolpix 4100 and Nikon D100. They both worked fine on previous Ubuntu versions. With Edgy it sucks. I have tried a lot to fix /etc/udev/rules.d/45-libgphoto2.rules, but that has not worked. I have also tried to downgrade libgphoto2, but that has not worked, either. There remained 2 ways to get my pics down from my cameras: #1: gksudo gtkam (that works best, **thanks for this trick mate!**  #2: switching the cameras from PTP to Mass USB mode.

---

### Post by goonies on 2007-03-16
can someone help me with my problem, think its the same as everybody elses

heres the thread

[http://ubuntuforums.org/showthread.php?t=385505](http://ubuntuforums.org/showthread.php?t=385505)

---

