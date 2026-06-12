---
title: "Failed to start scanner: Invalid argument"
date: 2014-07-21
forum: Hardware
---

### Post by webmanoffesto on 2014-07-21
I have a new Ubuntu 14 install. I have a Brother MFC-7460dn multifunction printer. I am now able to print just fine. But I want the scanner to work too. 

At first Ubuntu didn't "see" the scanner at all. I followed the instructions here [http://ubuntuforums.org/showthread.php?t=783599](http://ubuntuforums.org/showthread.php?t=783599). 
**[FONT=courier new]sudo chmod a+w /dev/bus/usb/003/013 [/FONT]**[FONT=courier new]
[FONT=arial]thought I was making progress because Ubuntu did "see" the printer/scanner. [/FONT][/FONT]

But then I go the error message
[FONT=courier new]Failed to start scanner: Invalid argument[/FONT]

**Output from the "lsub" command**[INDENT][FONT=courier new]tom@Toms-Laptop-K55A:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bc2:a013 Seagate RSS LLC 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 015: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 014: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 003 Device 013: ID 04f9:024e Brother Industries, Ltd 
Bus 003 Device 012: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 011: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tom@Toms-Laptop-K55A:~$ sudo chmod a+w /dev/bus/usb/003/013 
[sudo] password for tom: [/FONT]
[/INDENT]

I'm on Ubuntu 14
Printer is Brother MFC-7460dn

[IMG]http://i1232.photobucket.com/albums/ff365/webmanoffesto/XSaneScannerAlmostWorkedv01.png[/IMG]

What do you recommend?

---
Following directions [here]("http://forums.fedoraforum.org/showthread.php?t=247308&highlight=Failed+to+start+scanner%3A+Invalid+argument+HPc6380").
tom@Toms-Laptop-K55A:~$ scanimage -L
device `brother4:bus2;dev3' is a Brother MFC-7460DN USB scanner
---

The printer works because I already used
Driver Install Tool - The tool will install LPR, CUPSwrapper driver and scanner driver (for scanner models).
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7460dn_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7460dn_all&os=128)

---

### Post by pdc on 2014-07-21
forum admins will ask you to NOT double-post; this post could be deleted as you are running another

---

### Post by webmanoffesto on 2014-07-22
Yes, I did that by mistake. Then I tried to delete one, but I couldn&#8217;t.

---

