---
title: "ATI radeon HD 3200 mobile grapic problems.."
date: 2009-10-07
forum: Hardware
---

### Post by ElevenWarrior on 2009-10-07
I have an Acer ASpire 6530G with a HD 3200 moblie chipset. Whenever I put the grapic settings on extra (visual effects) I can't play DVD's right (shows only half the DVD screen audio dosen't work etc).
Anyone know what could be wrong?
the system has 3GB of ram, Dual Core 2.1 ghz plently of HD space, I'm not sure whats wrong.
I know that if I put the graphics on low, it runs everything with no problems.
any ideas???:confused:

---

### Post by lavinog on 2009-10-07
does the same thing happen if you play the videos in the example folder?

try playing the dvd with vlc

---

### Post by ElevenWarrior on 2009-10-07
yep still messe's up with example folder sample movie. playing sample with VLC messe's up text on bottom of the screen (in movie) and  there is no audio. same with MPlayer

---

### Post by lavinog on 2009-10-07
Are you using the video driver from the hardware manager?
If so that is a beta version and had alot of bugs.
You can use the updated driver from the ati website, or wait until karmic comes out, and see how the opensource driver works.

see what this outputs:
```
dmesg|grep ' fglrx '

```

---

### Post by ElevenWarrior on 2009-10-07
[   11.200515] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors

thats the output.
ATI has newer drivers for ubuntu?

---

### Post by lavinog on 2009-10-07
They release a driver every month...it is commonly known as fglrx
It used to be kind of a pain to install, but since about last year, the installer supported ubuntu.

---

### Post by ElevenWarrior on 2009-10-07
*downloads driver right now* will install and see how they work
thank you!

---

### Post by ElevenWarrior on 2009-10-07
yep problem sloved.

---

### Post by IsolatedSheep on 2009-10-18
I have the same problem. but **dmesg|grep ' fglrx '** wont output anything..

btw, i'm new to Ubuntu...

---

### Post by lavinog on 2009-10-18
> **IsolatedSheep said:**
> I have the same problem. but **dmesg|grep ' fglrx '** wont output anything..

btw, i'm new to Ubuntu...

Welcome to Ubuntu.
For future reference, it is best to start your own thread because you might not have the same issue, and this thread has already been marked as solved so no one is going to look at it anymore.

If it doesn't output anything, you are not using the restricted driver.
Do you have the same video card?
If so, go to system>administration>hardware drivers.

It should let you activate the FGLRX driver.
reboot, then see what happens.
If you still have the same problem you should update to the latest driver from the ati website.

You can also try Ubuntu 9.10 beta since it will be released in 11 days, and will have all of the latest drivers.

---

### Post by IsolatedSheep on 2009-10-18
there's no need i guess... problem solved!! thanks to you... i can now run compiz after weeks of searching the solution =_=... again, thanks!

---

