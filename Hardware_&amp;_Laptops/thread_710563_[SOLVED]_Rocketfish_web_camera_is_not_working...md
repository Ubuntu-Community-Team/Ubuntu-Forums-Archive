---
title: "[SOLVED] Rocketfish web camera is not working.."
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by Kuzja on 2008-02-28
Hello everyone!!! I'm absolutely new to Linux and Ubuntu in particular (It's easy to guess since this is my first post here). I love Ubuntu a lot so far, but I have come across one problem with my [COLOR="Navy"][Rocketfish web cam ]("http://www.rocketfishproducts.com/pc-35-3-rocketfish-notebook-web-camera.aspx")[/COLOR]. It just refuses to work. I plug it into USB port and nothing happens. I'll really appreciate any help. Thanks

---

### Post by linuxwizard on 2008-02-28
Plug the webcam in than go to Applications > Internet > Ekiga Softphone > see if your webcam work/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. If it does not work post result of the command > lsusb

---

### Post by Kuzja on 2008-02-28
Thanks, I've checked Ekiga as you told me and it said that no video input device was found. Though it detects web cam as an audio device and command gives me the following result:
Bus 003 Device 007: ID 0c45:6288 Microdia
Bus 003 Device 006: ID 1058:0702 Western Digital Technologies, Inc
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c047 Logitech, Inc
Bus 001 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-02-28
This is your webcam > Bus 003 Device 007: ID 0c45:6288 Microdia > you can get drivers for Microdia webcams here > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by Kuzja on 2008-02-28
ooo, thanks a lot, looks like its working now

---

### Post by linuxwizard on 2008-02-28
That's good to hear that you have your webcam working and that driver worked. If you don't need anymore help please mark thread as SOLVED.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by likemindead on 2008-04-06
I realize this thread is listed as solved, but I have the same rocketfish cam and I'll need a bit more direction. The Linux Projects link above doesn't specify a particular package. What exactly do I need to download? And then what? If someone can give me a step by step I would be eternally grateful. Thanks in advance....

---

### Post by linuxwizard on 2008-04-06
This one is TRIAL (time limited) > [http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7)

Or this one I think this is the one most used.
[http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2)

Documentation
[http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6](http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6)

---

### Post by likemindead on 2008-04-06
Uh.... I don't suppose there's a simple .deb that'll fix me right up? :confused:

I tried to follow the link above but still I've got nothing. Thanks....

---

### Post by likemindead on 2008-04-07
Ah.... actually the TRIAL is a .deb package and it works great! They only want 7 USD for the full deal and I figure that's more than fair. So add me to [COLOR="Blue"]**SOLVED**[/COLOR] Thanks again! ^__^

---

### Post by Kuzja on 2008-04-26
Also some usefull information can be found in this thread [http://ubuntuforums.org/showthread.php?t=375005](http://ubuntuforums.org/showthread.php?t=375005).
There is also this guide [http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/](http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/) but i havent tryed it myself. It is based on this [http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/) which seems to be a promising project.

---

### Post by baya_agaa on 2008-04-26
> **Kuzja said:**
> Also some usefull information can be found in this thread [http://ubuntuforums.org/showthread.php?t=375005](http://ubuntuforums.org/showthread.php?t=375005).
There is also this guide [http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/](http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/) but i havent tryed it myself. It is based on this [http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/) which seems to be a promising project.
hi . i got the same problem with PCline 300k webcam.
i've tested on Ekiga. v4l and gspca seems doesn't work.
I used same PCline webcam 150  before and it worked great.
i wanna use my cam with Skype.
Please help

Bus 005 Device 002: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 093a:262a Pixart Imaging, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Kuzja on 2008-04-26
The only thing I can say for sure is that your web camera is "Pixart Imaging" (while we have Microdia), so I guess you need a different driver.

---

### Post by Kuzja on 2008-04-27
Maybe you can find answer here [http://ubuntuforums.org/showthread.php?t=622351&highlight=pixart](http://ubuntuforums.org/showthread.php?t=622351&highlight=pixart)

---

