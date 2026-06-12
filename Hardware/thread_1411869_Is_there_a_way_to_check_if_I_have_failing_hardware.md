---
title: "Is there a way to check if I have failing hardware???"
date: 2010-02-20
forum: Hardware
---

### Post by Joe Ker1086 on 2010-02-20
Is there a way through ubuntu that i can see if my hardware is failing? i looked in the logs and dont really know what i am looking for.....i had a very hard time reinstalling ubuntu after i accidently deleted it...and now it is saying i have kernel errors...

---

### Post by ubunterooster on 2010-02-23
var/log/messages | less

this shows sys logging. I think error codes should start w/ (EE)

---

### Post by Joe Ker1086 on 2010-02-23
Thanks...don't see any of those....had a real hard time getting ubuntu to install (after like the 4th hd reformat) so i was worried that it was my hard drive failing. looks to be the cdrom is prolly bad, i installed it via usb drive and it layed down ok with some minor errors. at least i finally have my laptop set up how i want... the thing has been reformatted at least 40 times i think...or at least 1 partition has been.

---

### Post by ubunterooster on 2010-02-23
the command will not likely show errors for hardware (it may w/ some errors) but will for software (missing/corrupted drivers and the like). It appears then that the problem is hardware. :(
 If you look closely, you may be able to something out of place (Loose soldering joints, burned capacitor..).
If you see something, and feel handy enough to do some micro-soldering, see if they have a replacement part at radioshack. [I've fixed radioes, a tv, and a USB thumbdrive among other things this way; it's not that difficult, and if you ruin it, it wasn't working properly anyway,so...]

---

### Post by dabl on 2010-02-23
The Parted Magic Live CD has some useful utilities, in addition to partitioning.  There's a GUI front-end that runs smartmon to test your hard drive, for example.

[http://partedmagic.com/download.html](http://partedmagic.com/download.html)

---

### Post by Joe Ker1086 on 2010-02-23
I have a copy of that....never played with the utilities though, thanks for the tip :)

---

### Post by ubunterooster on 2010-02-23
researched and found there is smartmontools in synaptic as well as smart-notifier, so no liveCD is needed.

---

### Post by Joe Ker1086 on 2010-02-23
cool, ill download them and give them a try :)

---

