---
title: "two external hard drives"
date: 2018-08-11
forum: Hardware
---

### Post by greg29 on 2018-08-11
hello, i have a minor issue i think and it spans platforms cause it also happened when i had windows 10 on my rig. i have two external hdds one is 1tb and the other is 2tb, when i boot up only one is recognised. Unless i unplug the non recognised one and plug it back in then all is well. one is wd(2tb) and the other is a seagate(1tb). also it is always the seagate that gets the heave hoe. minor i know but annoying and stumped this moron any help would be appreciated.

---

### Post by TheFu on 2018-08-11
Try different eSATA cables and different eSATA ports.

---

### Post by greg29 on 2018-08-12
sorry, TheFu these drives are usb, i used ntfs-config for permissions for other software which(i don't know how) has worked but now my "restart" option in the power menu does not work. It reboots, gets back to the ubuntu loading screen and stays there. If i hard power down it will boot up fine.

---

### Post by TheFu on 2018-08-12
> **TheFu said:**
> Try different eSATA cables and different eSATA ports.

Well, if they are USB, then 
Try different USB cables and different USB ports.
Not all USB controllers are compatible with all USB devices.  You can use lsusb to see to get identification, which can be used to determine the USB controller.  With that, you can look up whether those are compatible with the specific devices - and I mean SPECIFIC devices.  "Seagate" isn't enough.  You'll need to look up the chips inside that external case.

Another option is to pull the HDDs out and connect them directly using SATA.  All HDDs are compatible, unless there is a HW failure.

---

### Post by greg29 on 2018-08-13
problem fixed thanks for the help

---

### Post by QIII on 2018-08-13
Hello!

What fixed it?  It would be helpful to future searchers if you could provide that.

Thanks.

---

