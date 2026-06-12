---
title: "TiLp2 configured for TI-83+ SilverLink USB on Feisty Problem"
date: 2008-07-14
forum: General Help
---

### Post by mweston2 on 2008-07-14
I have tried finding someone with a similar issue on Google, but to no avail... :( 

I am running Windows XP with a VMware server hosting Ubuntu 7.04 (Feisty). 
I built and installed TiLp2 1.11 using the source code, and followed the helpful instructions I found here:

[http://ubuntuforums.org/showthread.php?t=427472](http://ubuntuforums.org/showthread.php?t=427472)
 
I am able to execute the built & installed application, and configure it to use my TI83+ (with SilverLink USB cable).  My problem is, if I try to do a DirList or dump the ROM, I always get the following message:
 
Msg: timeout occurred while reading to the device.
Cause: check that link cable is plugged and/or the 
calculator is ready.
System: Resource temoporarily unavailable (errno = 11)
 
Here is the output from the console by simply starting up TiLp
configured to use my TI83+, and then pressing the DirList button
on the GUI. 
 
---------start of output---------------
ubuntu@ubuntu:~$ sudo tilp
TiLP2 - Version 1.11, (C) 1999-2008 Romain Lievin
THIS PROGRAM COMES WITH ABSOLUTELY NO WARRANTY
PLEASE READ THE DOCUMENTATION FOR DETAILS
built on Jul 13 2008 21:27:12
tilp-INFO: setlocale: en_US.UTF-8
tilp-INFO: bindtextdomain: /usr/local/share/locale/
tilp-INFO: textdomain: tilp2
ticables-INFO: ticables library version 1.2.0
ticables-INFO: setlocale: en_US.UTF-8
ticables-INFO: bindtextdomain: /usr/local/share/locale
ticables-INFO: textdomain: libticables2
ticables-INFO: kernel: 2.6.20-17-generic
tifiles-INFO: tifiles library version 1.1.1
tifiles-INFO: setlocale: en_US.UTF-8
tifiles-INFO: bindtextdomain: /usr/local/share/locale
tifiles-INFO: textdomain: libtifiles2
ticalcs-INFO: ticalcs library version 1.1.2
ticalcs-INFO: setlocale: en_US.UTF-8
ticalcs-INFO: bindtextdomain: /usr/local/share/locale
ticalcs-INFO: textdomain: libticalcs2
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found  on #1, version <1.03>
ticables-INFO:  found TI-GRAPH LINK USB on #1, version <1.03>
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3 
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
ticalcs-INFO: Checking hand-held status:
ticalcs-INFO:  PC->TI: RDY?
ticalcs-INFO:  TI->PC: ACK
ticalcs-INFO: Requesting folder & vars & apps listing:
ticalcs-INFO:  PC->TI: REQ (size=0x0000, id=19, name=, attr=0)

(tilp:8638): ticables-WARNING **: usb_bulk_read (error sending control message: Protocol error).

ticables-INFO:  found TI-GRAPH LINK USB on #1, version <1.03>
---------end of output---------------
 
I also will mention on some occasions I am able to do a screen
capture successfully.
 
I have tried running tilp from a user, sudo tilp, and from root.
 
Any help someone could provide would be greatly appreciated!

---

