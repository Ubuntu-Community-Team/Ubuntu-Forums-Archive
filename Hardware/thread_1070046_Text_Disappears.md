---
title: "Text Disappears"
date: 2009-02-14
forum: Hardware
---

### Post by antiderivative on 2009-02-14
I know this has been discussed before, but I still couldn't get much help out of the forums. Anyway, for those who haven't seen this problem before, the toolbar (and button) text disappears on programs like OpenOffice and Wine. I learned that this was an nvidia driver problem, but I never could find a good answer on how to fix it. One option was to turn off compiz and desktop effects, but I don't want to do that! Is it possible to just install an older version of the driver, because I used to be able to use desktop effects with OpenOffice and Wine without the text disappearing.

By the way, I put this in the hardware section because it seems to be a hardware driver conflict with my nvidia card.

---

### Post by binbash on 2009-02-14
One nvidia driver fixed that.I am not sure which one but if i remember correctly it is 180.Before installing the driver try this and see if this trick works : 

System> preferences > appearance >fonts >enable subpixel smoothing

---

### Post by antiderivative on 2009-02-14
> **binbash said:**
> One nvidia driver fixed that.I am not sure which one but if i remember correctly it is 180.Before installing the driver try this and see if this trick works : 

System> preferences > appearance >fonts >enable subpixel smoothing

I'm afraid installing the nvidia 180 driver only succeeded in screwing up my graphics. The subpixel smoothing only made the OpenOffice text show, but Wine, and a few other programs with the same problem were not fixed.

---

### Post by antiderivative on 2009-02-15
Anyone know if nvidia plans on fixing this bug (also known as Bug #308830)? Nvidia has updated 4 times (since I've had this problem), but they still seem to have ignored this bug. I so far cannot find a way to completely fix it, only for OpenOffice.

---

### Post by alain.derycke@telenet.be on 2009-02-20
The toolbar in OOo (writer,etc) version 2.4 and even version 3.0 is unreadable within ubuntu 8.10. I am a novice to this forum, but maybe the driver of my nvidia-card (version 96) might be causing problems? I do not know or find out to remedy this problem.
If anyone can help, thank you

---

### Post by mattech420 on 2009-02-20
if you have an older amd procesor or anything older than a Prescot Pentium4, DO NOT CHANGE YOUR DRIVER, KEEP IT AT 96. make sure that your procesor supports the SSE3 instrution set or the newer driver will only give you a bigger head ache. At this point I only know a fix for Wine.it is here[http://ubuntuforums.org/showthread.php?p=6696429]("http://ubuntuforums.org/showthread.php?p=6696429")

---

### Post by cariboo on 2009-02-20
Does everything work when you turn compiz off? If you want to know if the bug is going to be fixed, wouldn't it be better to go to the [source]("http://www.nvidia.com/page/support.html") of the problem?

Jim

---

### Post by Payperbiz on 2009-02-20
Better go to a technician to provide solution to this otherwise you might lose all your files.

---

### Post by sharathpaps on 2009-02-20
@antiderivative

Hey, I had this problem and I managed to find a solution. 

The Bad News  : You won't have Extra Visual Effects
The Good News : The fix works
 
I posted the solution that worked for me in [this thread]("http://ubuntuforums.org/showthread.php?t=1020727")


I'd prefer that programs like Wine and Open Office work as opposed to having fancy effects. What says you? :-)

---

### Post by alain.derycke@telenet.be on 2009-02-21
Dear sharathpaps,

your solution works fine. OOo (even version 3.0 as I installed it as I first thought it was a bug in OOo 2.4, works fine). Only I feel a bit disappointed my compiz eye candy is not working at all any more. But if I have to choose between a valid OOo and some eye candy, for the moment I can live with it. However I hope the Nvidia bug is resolved as soon as possible. 
Thank you all!

---

