---
title: "After Sleep USB does not work"
date: 2010-03-26
forum: Hardware
---

### Post by Garibaldi3489 on 2010-03-26
I am running the lucid beta and whenever I put the computer to sleep/suspend and bring it out again, my USB mouse no longer works. Moreover, I cannot use any USB device until I reboot. [A similar issue](http://ubuntuforums.org/showthread.php?t=1314754) has been reported in karmic but I thought I'd make a separate posting for this issue in lucid. I've tried
```
 $ sudo modprobe -r usbhid && sudo modprobe usbhid
```
but even unloading the module does not fix this issue. Its like the USB ports are no longer getting power. Any ideas?

Thanks!

---

### Post by conradin on 2010-03-26
Just an idea. Turn off ACPI. 
```
acpi=off  
```

---

### Post by Garibaldi3489 on 2010-03-26
Unfortunately acpi=off generates a whole host of other problems and additionally usb won't work at all if I turn off acpi... hm... very strange. Any other suggestions? This is a new IBM Thinkpad T410 if that makes any difference...

Thanks!

---

### Post by shutterbc on 2010-06-09
Since you posted this, I realized I was also affected by this.  Fortunately it looks like there is now a fix:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566149/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566149/)

Just waiting for an update to the Lucid mainline now, though this is important enough that I may just patch for the time being.

---

### Post by Garibaldi3489 on 2010-06-13
Thanks for the reply. I had also found this bug report and manually applied the patch to the 2.6.34 kernel. I am glad to report that my USB sleep problems are fixed!

---

