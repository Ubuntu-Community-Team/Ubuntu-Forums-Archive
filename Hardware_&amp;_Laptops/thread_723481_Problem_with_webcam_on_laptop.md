---
title: "Problem with webcam on laptop"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by mesder on 2008-03-13
I have this laptop with integrated webcam, which Gutsy doesn't recognize. No program find a webcam, ie:

magnus@magnus-laptop:~$ camgrab 
open /dev/video0: No such file or directory

The result from lsusb: (but it is connected via USB when it's integrated?)


magnus@magnus-laptop:~$ lsusb
Bus 005 Device 002: ID 1058:0901 Western Digital Technologies, Inc. 
Bus 005 Device 003: ID 0c45:624f Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

I'm not totally sure even what brand the webcam is. I've tried to run easycam2, but it doesn't seem to help.

Any help?

---

### Post by linuxwizard on 2008-03-13
This is your webcam > Bus 005 Device 003: ID 0c45:624f Microdia > 
Drivers for Microdia webcams you can get here > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by intel on 2008-03-14
**Microdia** (Webcam Support group for all Microdia chipsets under Linux)
 
Q) Is my webcam a "microdia"? 
A) Execute the following command 
    #lsusb
If you see any of the following numbers, you have a "microdia" webcam
0c45:6027, 0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624e, 0c45:624f, 0c45:6242, 0c45:6253, 0c45:6260, 0c45:6270, 0c45:627b, 0c45:8105
(basically 0c45:<xxxy> above is enough to conclude you have a microdia webcam) 

All of the above webcams are unsupported under Linux

[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)



 
Please join this Group, to help each other get better support for these webcams from Linux.

---

### Post by mesder on 2008-03-15
Thanks a lot!

---

### Post by vivalant on 2008-03-15
mesder, your webcam is supported by the SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by mesder on 2008-03-16
Thanks Vivalent. It's just quite annoying that it is a time limited trial :\

---

### Post by srv104 on 2008-07-05
Please check this post on making the microdia cameras work.

[http://ubuntuforums.org/showthread.php?t=501460&highlight=627b](http://ubuntuforums.org/showthread.php?t=501460&highlight=627b)

---

