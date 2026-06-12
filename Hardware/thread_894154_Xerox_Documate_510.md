---
title: "Xerox Documate 510"
date: 2008-08-19
forum: Hardware
---

### Post by systemclock on 2008-08-19
Does anyone have any luck on getting the Documate 510 scanner to work on Ubuntu via VirtualBox (windows xp)?  It shows up "Unknown device 04A7:047C [0001 in VirtualBox.  Thanks.

---

### Post by cariboo on 2008-08-19
Your scanner is unsupported by sane, you are using virtual hardware in Virtualbox so it probably won't work there either.

Jim

---

### Post by systemclock on 2008-08-19
Yeah, it's unsupported in sane... was hoping it's recognized in VB but I guess I'm out of luck eh?  :)  Thanks.

---

### Post by mdshaver on 2008-08-25
I also have a documate 510 with Ubuntu 8.04. I understand the drivers are not supported by SANE and thus the hardware does not work with this OS. Is there any hope, for example when Ubuntu 8.10 is released in October?

---

### Post by elias@cpaefs.com on 2008-08-26
I am also in the band wagon. I pray to the Linux and Xerox Gods for a miracle.

---

### Post by cariboo on 2008-08-26
THe drivers are done by the people working on sane, it has nothing  to do with Ubuntu. THey have all the specifications on their web site just waiting for someone to have a go at creating a driver for the scanner.

Jim

---

### Post by dvigliotti on 2008-11-24
I'm not sure that I did anything special but I do have a Xerox Documate 510 running in VirtualBox 2.0.4 Windows XP Guest successfully.  Initially on plugging in I had no response but then I went to the devices menu in VirtualBox to USB Devices and checkmarked the appropriate box.  Once checked XP picked it up and installed the drivers.  I have successfully scanned from the built-in XP scanner tools.

My Ubuntu host is 8.04, Kernel Linux 2.6.24-21-generic, Gnome 2.22.3, Platform is a Latitude D610 with 2G RAM and 2Ghz processor.

Attempting to use the scanner in Linux directly was no go.  Sane would not recognize it.

--oh, and also guest additions2.0.4r38405

---

### Post by Idaho Dan on 2009-07-24
I just decided to try it again and now it works!
Maybe this is old news for some, but it is great news for me.

Still shows as unsupported on the sane list though.

---

### Post by cuyabro on 2011-12-30
Hello, 

It's been 2 years since the last post in this thread.  I just installed Ubuntu 11.04 on my PC and my Xerox Documate 510 will work only when scanning single pages from the flatbed.  However, when trying to scan from the ADF it will attempt to start but then give an error: Failed to start scanner: Error during device I/O.

Doing lsusb identifies it as Visioneer Xerox Documate 510.  

Sane still lists this scanner as unsupported.  However, I see in other threads this scanner has worked  

([http://ubuntuforums.org/showthread.php?t=1469983&highlight=xerox+documate+510](http://ubuntuforums.org/showthread.php?t=1469983&highlight=xerox+documate+510)).  

Any help would be greatly appreciated.

---

### Post by thelusiv on 2012-02-02
bump, i have the same problem with the ADF.

---

