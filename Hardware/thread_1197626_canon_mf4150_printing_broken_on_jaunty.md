---
title: "canon mf4150 printing broken on jaunty"
date: 2009-06-26
forum: Hardware
---

### Post by quackeroni_pizza on 2009-06-26
I have a Canon MF4150 printer/scanner connected over USB to a Jaunty machine. I installed printer drivers from the Canon Asia website. 

A few observations-
1. My printer worked on the Intrepid just fine.
2. Scanning works with xsane on Jaunty as well as Intrepid. (Related post: [http://ubuntuforums.org/showthread.php?t=878966](http://ubuntuforums.org/showthread.php?t=878966))

Here's a portion of the CUPS error log
> 
E [26/Jun/2009:10:54:54 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Jun/2009:10:54:54 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Jun/2009:10:54:54 -0400] cupsdAuthorize: Local authentication certificate not found
E [26/Jun/2009:10:58:21 -0400] [Job 9] Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4a9_26a3_SDF680281822B_if1_printer_noserial": Permission denied
E [26/Jun/2009:10:58:21 -0400] PID 6339 (/usr/lib/cups/backend/hal) stopped with status 1!
E [26/Jun/2009:10:58:23 -0400] [Job 9] src = libcanon_pdlwrapper.c, line = 630, err = -1Â¥nError Response:ReqNo=2, SeqNo=3,errorno=-2


Relevant launchpad bugs:
1. [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/364877](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/364877)
2. [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/367594](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/367594)

---

### Post by quackeroni_pizza on 2009-08-15
Upgraded driver to 1.8 from 1.7 but still no joy. :(:(:(

---

### Post by bertmanphx on 2010-01-27
Hello,
Did you ever get this working?  I've got an MF4370dn here at work, trying to get it working with Ubuntu 9.10 and the Canon driver version 1.9 from their site.

bertmanphx

---

