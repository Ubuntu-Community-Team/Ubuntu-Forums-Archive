---
title: "Ubuntu boot problem with Toshiba 480CDT"
date: 2006-07-17
forum: Hardware &amp; Laptops
---

### Post by Matthew Bartram on 2006-07-17
I am trying to install Xubuntu on my friend's old Toshiba 480CDT which has no OS on it.

The boot menu comes up, and after telling it to boot, it brings up a box saying "Loading linux kernel". This goes fine.

Then the screen goes into text mode, and displays:
```
Uncompressing Linux... Ok, booting the kernel.
[4294667.296000] ACPI: Unable to locate RSDP
```The normal boot screen comes back up, and gets through:```
Loading essential drivers...
Mounting root file system...
Moving mount points...
```without problem, then gets stuck on
```
Adding live CD user...
```Then, after a while, the booter evidently exits, because the screen switches back to the earlier text. ("Uncopmpressing Linux...")

---

### Post by Matthew Bartram on 2006-08-23
Anyone got any ideas?

---

### Post by doobit on 2006-09-07
> **Matthew Bartram said:**
> Anyone got any ideas?

There are two things going on here. 
1. There is a problem with the installer on the Xubuntu Desktop CD. I had this same trouble (as have many others) trying to install to a desktop. If you hit alt+f1 during this process you will see some caching errors listing your CDROM drive as the culpret. I had to install a different CDROM to finally get it to install. This error has been discussed in another thread and  list of possible fixes are there. [http://www.ubuntuforums.org/showthread.php?t=186115&page=2&highlight=Xubuntu+hang+install](http://www.ubuntuforums.org/showthread.php?t=186115&page=2&highlight=Xubuntu+hang+install)

For me the best fix was to put acpi=force in the boot command line. However, I don't know if the 480 CDT supports acpi, I think it's APM only. I had one a while ago and had DamnSmall Linux loaded on it and it worked great.

2. Get the alternate install CD, because you can install in a text-based mode. The graphics in the normal desktop install CD really can stress the video RAM in that old laptop.

---

### Post by Matthew Bartram on 2006-09-08
Thanks. I will try the alternate CD. If that doesn't work then comes the 21 pages from your link :-)

---

