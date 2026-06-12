---
title: "Need help to access integrated webcam"
date: 2008-06-30
forum: Hardware
---

### Post by cmpunk on 2008-06-30
I've got a Velocity Micro laptop with 7.10 Ubuntu running on it and I can't access the integrated webcam. 

I have installed the application Cheese, but every time I open Cheese up, it says this:
Unable to find a webcam, SORRY!

NEED HELP!

---

### Post by linuxwizard on 2008-06-30
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If webcam does not work post the results of the command > lsusb

---

### Post by cmpunk on 2008-06-30
It didnt work.
Now here's what I got with the command lsusb:

Bus 005 Device 003: ID 0c45:624f Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-06-30
Your webcam > Bus 005 Device 003: ID 0c45:624f Microdia  > for Microdia webcams this is the driver you need > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by cmpunk on 2008-07-01
when i tried to install the driver, it would give me an error telling me this:

Error: Dependency is not satisfiable: linux-image-generic

what should I do?

---

### Post by bcschmerker on 2008-07-01
:!: From the posts to date, it appears that cmpunk's system may be missing nodes in udevfs, a problem I happen to need help remedying (my own Everex gPC system unit is not communicating with my Emprex G40).  What nodes are listed upon running ls /dev/video*?  (As of this post, mine still gives the error message bash: /dev/video*: No such file or directory.)

For my own situation, see:
[http://ubuntuforums.org/showthread.php?t=838323](http://ubuntuforums.org/showthread.php?t=838323)

---

### Post by cmpunk on 2008-07-01
Still Need Help!](*,)

---

