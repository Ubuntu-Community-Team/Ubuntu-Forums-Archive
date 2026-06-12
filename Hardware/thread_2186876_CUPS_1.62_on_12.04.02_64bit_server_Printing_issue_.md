---
title: "CUPS 1.62 on 12.04.02 64bit server Printing issue with Cannon driver"
date: 2013-11-09
forum: Hardware
---

### Post by Windowsxpnomore on 2013-11-09
ok, 
Installed 12.04.2 64bit server on a PC. Printing to a Canon iP6000D does not work and I wanted to use this also as a print server. the print was output but was sretched.
I gave up.

I have recently installed 13.04 desktop 64bit on aonther PC  and out of box this prints to a Cannon iP6000d without any issues.
So decided to give my 12.04 another go.

The first thing I did was upgrade the CUPS and any other printing package that were fresh since I had installed the OS. I still have another 138 packages that need upgrading, but I have not done these.

I attempted to print from the 13.04 desktop PC and the same problem was there. So - 

I saw that the version of cups on 12.04.2 was not the same version as on 13.04 so I upgrade CUPS to 1.62. The other difference I was was the driver: on 13.04 its
Canon PIXMA iP6000D - CUPS+Gutenprint v5.2.9 (color, 2-sided printing) and on 12.04.02 its Canon PIXMA iP6000D - CUPS+Gutenprint v5.2.8pre1

And I now have other print problems that I did not have before:

I am a beginner so stay with me:

rodney@MediaServer:/dev/usb$ lsmod | grep usb
usblp                  18315  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
usb_storage            49288  0 

rodney@MediaServer:/dev/usb$ lpstat -a
lpstat: Success

rodney@MediaServer:/dev/usb$ ls -lrt
total 0
crw------- 1 root root 180, 1 Nov  9 18:40 hiddev1
crw-rw---- 1 root lp   180, 0 Nov  9 18:41 lp0

Webmin reports that no printers are configured.

localhost:631 works, but adding a printer and
syslog shows:
Nov  9 19:06:00 MediaServer kernel: [ 3748.642117] type=1400 audit(1384023960.628:115): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=3981 comm="cupsd" pid=3981 comm="cupsd" capability=36  capname="block_suspend"
Nov  9 19:06:00 MediaServer kernel: [ 3748.653229] type=1400 audit(1384023960.640:116): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=3981 comm="cupsd" pid=3981 comm="cupsd" capability=36  capname="block_suspend"
Nov  9 19:06:00 MediaServer kernel: [ 3748.659984] type=1400 audit(1384023960.648:117): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=3981 comm="cupsd" pid=3981 comm="cupsd" capability=36  capname="block_suspend"
Nov  9 19:06:13 MediaServer kernel: [ 3761.406914] type=1400 audit(1384023973.432:118): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=3981 comm="cupsd" pid=3981 comm="cupsd" capability=36  capname="block_suspend"
Nov  9 19:06:25 MediaServer kernel: [ 3773.686827] type=1400 audit(1384023985.748:119): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=4421 comm="apparmor_parser"
Nov  9 19:06:25 MediaServer kernel: [ 3773.687443] type=1400 audit(1384023985.748:120): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=4421 comm="apparmor_parser"

and the web interface connection is terminated.

I dont know where to go from here -
any help appreciated.
thanks

---

### Post by Windowsxpnomore on 2013-11-09
ok, just found this thread [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/912754](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/912754)
so I have upgraded apparmor from 2.7.102_0ubuntu3.7 to 2.7.102_0ubuntu3.9 and restarted cups. Made no difference.

---

### Post by tgalati4 on 2013-11-09
Wouldn't it be easier to just install 13.10 desktop and call it a server?  It is not trivial to install a newer version of CUPS on 12.04.  If your printer works with 13.10, then use 13.10 to print.

---

### Post by Windowsxpnomore on 2013-11-10
12.04 is support until 2017 13.10 isnt. googling and the upgrade from 12.04 to 13.04 isnt straight forward. why change everything beacsue of 1 problem and be on OS that I need to upgrade every whatever months ? 
sorry that doesnt sound a very good solution

---

### Post by tgalati4 on 2013-11-10
Those are valid points.  You said the print was "stretched".  Is it just a matter of European paper size vs US paper size set as the default?  Look in the printer preferences and see how it is set up.

---

### Post by Windowsxpnomore on 2013-11-11
By stretched I mean: If you were to print ABCDEFG to Z on one line and in LibreOffice Word that appear on 1 line ok, when you print it - the A would be fine, the B would be about same height as the A but would be about 2 mm wider, the C would print about 2mm wider than the B. The D about 2mm sider again and so on, until you reach J which would be at about 3 cm wide and be on the right hand edge of the A4 page. All the other text would be lost. This is the same for any line printed. Graphics do the same stretch. As does the test page.

---

