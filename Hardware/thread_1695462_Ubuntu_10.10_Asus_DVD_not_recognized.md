---
title: "Ubuntu 10.10 Asus DVD not recognized"
date: 2011-02-25
forum: Hardware
---

### Post by Teelnaw on 2011-02-25
New to Ubuntu and have successfully installed 10.10 alongside my current Win 7 setup. However, 10.10 is not recognising the DVD drive. Win 7 and the BIOS are showing it. Its plugged into a SATA II port which Ubuntu seems to recognize. Could anyone help me troubleshoot this. I'm using an ASUS DVD drive on a ASUS P6X58D MoBo.

Thanks

---

### Post by WanderingAlbatross on 2011-03-07
Same problem with my external Asus DVD/CD drive.  We are using Kubuntu 10.10.  The drive works on my Dell Inspiron 1501, but not on my Dell Inspiron n5030.  

If you can attach your drive to another linux machine, open up a terminal and type ```
lsusb
```  Then unplug the drive and type ```
lsusb
``` again and notice which line changed.  I think it will help if we identify the device code for others that may be able to help troubleshoot it.  When I do this I find the screen reads:

```
13fd:1640 Initio Corporation 
```

For some reason I can read it with Ubuntu 10.04, but not with Kubuntu 10.10.  I have also tried the Gnome environment on the same Dell n5030 and still no success.  Also our version of Debian on the same laptop is having the same problem.

---

### Post by mike1312 on 2011-11-12
try this
[http://ubuntuforums.org/showthread.php?p=11449912](http://ubuntuforums.org/showthread.php?p=11449912)

---

