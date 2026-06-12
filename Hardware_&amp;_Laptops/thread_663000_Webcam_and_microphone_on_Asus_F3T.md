---
title: "Webcam and microphone on Asus F3T"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by mikhalek on 2008-01-09
I have ASUS laptop model F3T with Ubuntu 7.10 installed. Everything works fine only to fully use Skype my built in webcam Syntec Semiconductor with microphone doesnt work. Anybody can help me on this issue&

---

### Post by mikhalek on 2008-01-10
Anybody can help? Please!

---

### Post by idella4 on 2008-01-10
Hi there,
your description is very brief, so difficult to choose where to best focus.
I shall be putting my own post up for my own, but I know enough to get you started.

Firstly, are you sure your skype is up to tranferring a video stream?  I know mine is substantially less equipped than a Windows version, especially re video streaming. 

Secondly, do you have a video stream?  See that you can get one into a desktop application first before expecting skype to catch it.

Bring up a console, check for the required /dev/video[0], either a character file or a sym link.  If it is NOT there, go no further.  Any attempt to send it to an application is doomed.  Then follow my posting!.

If you have one, then get something to prove it.  If not installed, get gqcam or camstream by the usual means, and run it.  Could try gnomemeeting if you have it since it possesses a video module.  They ALL require a /dev/video.

BEST of luck

idella4

---

### Post by stafi on 2008-02-17
I've found the decision here: [http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek)
And here [http://www.stud.fit.vutbr.cz/~xzemek02/articles/Asus-F3Tc-AP049-Kubuntu-Feisty-7.04/](http://www.stud.fit.vutbr.cz/~xzemek02/articles/Asus-F3Tc-AP049-Kubuntu-Feisty-7.04/) U'll find how to get mic working and may be something else usefull.
I've got the same laptop.

---

