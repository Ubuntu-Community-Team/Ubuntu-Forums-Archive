---
title: "Cannot find ANY &quot;ppd&quot; files for my printer!"
date: 2010-12-28
forum: Hardware
---

### Post by OxentroT on 2010-12-28
I have a new HP PhotoSmart Printer c4385. On the first day i brought it home I seemed to have successfully installed it without a problem. However, this morning when I needed to scan a document with this device I was indicated that the wireless and the USB was not connected when in fact the USB cable was connected. I promptly looked into this issue and tried a few solutions to this to no avail.

    For some reason after a few tries of upgrading this and re-installing that, I begun receiving "fsck fail attempts" and "unexpected inconsistency" errors when rebooting (luckily I have had that problem before and resolved it..);)

   I have been looking all morning for a solution to this problem and for the love of me can not seem to find anything that can help. The few solutions that I did find were for SUSE and such. All I [think] I need thus far is a PPD file for when installing this device through means of HP-Toolbox GUI. (which I can find NOWHERE)


Is there anyone who has any slight bit of information in helping resolve this terrible issue. I want to SCREAM! I don't understand how things worked SO FINE the first day I installed this device and now It is as helpful as a paperweight at this point.


Below is results when Running HP-Setup via Term: 
```

bn0@b3163y:~$ sudo /usr/bin/hp-setup
[sudo] password for bn0: 

HP Linux Imaging and Printing System (ver. 3.9.2)
Printer/Fax Setup Utility ver. 8.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None) desc=0)
error: No PPD found for model photosmart_c4380_series. Trying old algorithm...
error: No PPD found for model photosmart_c4380 using old algorithm.
error: No appropriate print PPD file found for model photosmart_c4380_series


```

Any.. Any bit of information on where I could find these illusive PPD files or how to find and edit .Config file for 'hplip' I will bee truly.. truly great full. 

Thank You!

---

