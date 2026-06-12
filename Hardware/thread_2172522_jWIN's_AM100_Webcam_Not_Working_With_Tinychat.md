---
title: "jWIN's AM100 Webcam Not Working With Tinychat"
date: 2013-09-05
forum: Hardware
---

### Post by panthraxnation on 2013-09-05
Hi.

I'm not sure if this should of been posted in Multimedia & Video or not, so if this is in the wrong place I apologize up front.

I am new to Linux, really. I've used Linux several times before in the past. Slackware, Mandrake, Fedora, and now Ubuntu/Kubuntu. Still, I never really played too long with Linux because more often than not, and especially back then, none of my hardware wanted to work and I didn't have the desire to try and figure it out and make it work. Things have changed.

I'm a computer repair technician by trade, but I only use Microsoft's Windows operating system at work. We don't work on Mac's and we certainly don't touch a Linux-box.  What I am trying to get at is, I'm very experienced with computers and their hardware, just not so much with Linux and how it utilizes that hardware.

Anyway, I'll get to the point. I installed Kubuntu alongside an older Windows XP laptop I had. It's beautiful, KDE looks amazing these days (you must remember it's been some 8-10 years since I last saw KDE). All my hardware runs just fine except for 2 things (one of which I will get to in another thread). This thread is about my webcam.

I installed Mozilla Firefox and then Adobe Flash and logged on to tinychat.com to test it out. As I sort of expected, when I tried to broadcast my webcam's feed, tinychat says "webcam not available". 

Here are the results of lsusb if it helps any:

```
panthrax@Duality:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f3:02f4 Elan Microelectronics Corp. 2.4G Cordless Mouse
Bus 003 Device 003: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 003 Device 004: ID 093a:2620 Pixart Imaging, Inc. 


```

I did a Google search for this and I saw some open questions about it but they were either gone unanswered or the question was kind of avoided altogether. I'm trying to use this webcam in tinychat, a flash-based video chat room. I'm not interested in using Cheese to take pictures and video, nor am I interested in using Skype or Empathy's video chat features. I am only interested in getting this webcam to work in Tinychat. 

I know it's probably a tall order, but I figured I would ask here and see if there is anyone out there who can help me. I appreciate it very much and I hope I can get this webcam to work because it's the only thing keeping me from switching over to Linux from Microsoft's Windows.

---

### Post by scbingham on 2013-09-05
Although you don't want to use cheese, it is a good way to test if your camera will work with linux.

This link may help:[URL="https://help.ubuntu.com/community/Webcam"]
https://help.ubuntu.com/community/Webcam[/URL]

Under 7. External links, link no 4 does list some Pixart cameras but not your exact model.

I hope this helps to point you in the right direction.

---

