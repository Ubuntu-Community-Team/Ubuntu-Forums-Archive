---
title: "Reading and understanding data send to USB device"
date: 2009-06-12
forum: Hardware
---

### Post by TheForumTroll on 2009-06-12
Calling this a Linux question might be stretching it a bit but I'll try to explain and hope it is okay anyways as in the end it could be good for some users =)


Some multimedia/gaming keyboards have functions/buttons that isn't activated until it receives a signal from the PC. What I'm trying to do is listen to USB traffic between my PC and a keyboard to find the signal that activates the extra functions and hopefully then I'll be able to enable them in Linux.

So far I have a log from Windows taken when the keyboard is unplugged and then plugged in again. Unfortunately even with the USB specifications in hand I'm in way over my head. So I was hoping someone here might be able to tell me where to look in the logs or where to find more information. First I was thinking about debugging the .exe that is installed with the drivers in Windows but it resulted in a crash (big surprise) ;)


Here is the USB log from a replug:
[http://undskyldviroder.dk/ekspertendk/usblog.txt](http://undskyldviroder.dk/ekspertendk/usblog.txt)

And here is some more info about the subject:
[http://www.win.tue.nl/~aeb/linux/kbd/scancodes-1.html#ss1.10](http://www.win.tue.nl/~aeb/linux/kbd/scancodes-1.html#ss1.10)

---

### Post by TheForumTroll on 2009-06-16
I found the difference between with and without the keyboard software. Now how to do this in Linux...

This part is only there when keyboard software is installed: [diff.txt](http://undskyldviroder.dk/ekspertendk/diff.txt)

---

