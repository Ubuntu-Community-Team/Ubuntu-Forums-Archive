---
title: "IX250 USB boot problems"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by frank.trampe on 2007-08-09
I have an Itronix IX250 notebook . I have upgraded the processor to a 1GHz Pentium III , upgraded to 512MiB of memory , and installed a 120GB hard drive , but it is basically identical to my previous IX250 , which ran Ubuntu ( and was stolen ) . After I installed Ubuntu on the new system , the system began to report at start-up « hub 1-2:1.0: Cannot enable port 2.  Maybe the USB cable is bad? » . I was able to get the graphical interface to boot , but the messages continued and blocked attempts to hibernate . I installed Ubuntu a second time , hoping for a resolution of the problem , but now I cannot even reach the shell . The boot sequence continues after the messages begin to appear , but seems to stop during the hardware driver loading . For a while , the system also reports that it is adding a « new low speed USB device using uhci_hcd and address » something . The address changes at every report . This message stops after a while . Adding « nousb » as a kernel option makes no difference . I'm booting from kernel 2.6.20-15 . I did upgrade the kernel after the first installation , but it failed to correct the problem , so I'm hesitant to go to the trouble of upgrading the kernel a second time considering the trouble of booting from some other drive , downloading the new kernel package and attempting to configure it correctly on an inactive installation . I suspect that I may have a hardware problem of some sort . In that case , I'd like to disable the offending device . If I have a software problem , I'd like to correct it .

---

### Post by frank.trampe on 2007-08-09
The system indicates that it is starting the display manager , but stays in text mode .

---

### Post by pvilleSE on 2007-08-18
I just purchased the same laptop.  When I tried to install more than 256MB of ram it would no longer boot.  A little research on the internet showed that the system does not support more than 256MB, but I'm not sure if this is really true.  Maybe that is your problem.  Otherwise, since the system only has one USB port and the touch screen is supposed to be a USB touchscreen, maybe there is a problem with your touch screen, otherwise maybe try the alternate CD, that seemed to work for me.

On the one you did have working did you get the touch screen working correctly.  Mine recognizes that I am touching it but I cannot figure out how to calibrate it, including the fact that it recognizes the screen upside down.  I didn't install anything extra for the touchscreen, just the drivers that installed when I installed the OS(feisty) using the alternate install disk.

---

