---
title: "Scanner installation problem"
date: 2008-10-02
forum: Hardware
---

### Post by alllenwilkyrobertson on 2008-10-02
I just installed Ubuntu and for the most part I love it. 

HOWEVER, I am having trouble with some hardware. I would like to start with my scanner.

When I start XSane with no scanner attached I get the (expected) message "No Device Available".  After plugging the (Microtek ScanMaker 4800) scanner in (to the USB port) and running XSane, I get the error message "Failed to open device "sm3840 libusb:001:004": Access to resource has been denied."  

Sooooo, it's recognizing the scanner (sm3840 is the correct backend according to the sane website).  What is wrong, and how does this newbie fix it?

Thanks for your help!

---

### Post by nixscripter on 2008-10-03
Scanners are only allowed to be used by members of group scanner, which should have been created when XSane was installed.

Open a terminal and run the command: ```
groups
``` If "scanner" isn't in the list, you need to add yourself to it: ```
sudo gpasswd -a **username** scanner
```

---

### Post by alllenwilkyrobertson on 2008-10-03
Scanner was listed. 

The result was: adm dialout fax cdrom floppy audio dip video plugdev scanner fuse lpadmin admin sambashare

Thanks! Any more ideas?

---

### Post by alllenwilkyrobertson on 2008-10-05
Thanks to nixscripter for being the ONLY person to respond to my posting on seven different support sites including two local LUG's.

Due to the fact that there are a total of four hardware devices that are not working (scanner, fully functioning sound card, modem, Pinnacle AV/DV card), and also that I have not been able to get support (except from nixscripter - thanks again), I am going back to Microsoft Windows XP.

Simply put, it works.

I last tried Linux about eight years ago. Ubuntu has brought Linux a  LONG  way! Perhaps I will try Linux again in another eight years.

---

