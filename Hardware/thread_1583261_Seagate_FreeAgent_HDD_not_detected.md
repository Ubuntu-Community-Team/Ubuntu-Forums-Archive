---
title: "Seagate FreeAgent HDD not detected"
date: 2010-09-27
forum: Hardware
---

### Post by Phpaw on 2010-09-27
hello,

I'm a new Ubuntu user, in general a new Linux user

I installed Ubuntu 10.04 inside windows vista. I tried to plug Seagate FreeAgent HDD 320 GB but  I couldn't find it. it was detected before but I don't know what happened now I can't find it when I connect the USB. it is working fine in windows vista
:confused:

---

### Post by Phpaw on 2010-09-30
up :rolleyes:

---

### Post by lisati on 2010-09-30
Do you remember to use Vista's "Safely remove hardware" when you've finished with it?

---

### Post by Yougo on 2010-09-30
when you used it last time in windows, did you just yank the plug out, or did you go the "remove hardware safely" route? (left click icon in tray, choose device)

if it's the first case, windows couldn't unmount and release the volume. this is why linux can't acces it now. go back to windows, plug it in, remove it safely, unplug, go to linux, plug it in.

did that help?

---

### Post by Phpaw on 2010-09-30
> **lisati said:**
> Do you remember to use Vista's "Safely remove hardware" when you've finished with it?

yup I did safely remove hardware :(

Thanks lisati.

> **Yougo said:**
> when you used it last time in windows, did you just yank the plug out, or did you go the "remove hardware safely" route? (left click icon in tray, choose device)

if it's the first case, windows couldn't unmount and release the volume. this is why linux can't acces it now. go back to windows, plug it in, remove it safely, unplug, go to linux, plug it in.

did that help?

yes I did that, and I did it again using Windows 7 but no use :(
Thanks Yougo.

---

### Post by Phpaw on 2010-09-30
up :rolleyes:

---

### Post by davidmohammed on 2010-09-30
a quick [google]("http://www.theinquirer.net/inquirer/news/1039498/seagate-snubs-linux") reveals that your HDD isnt linux friendly.  Infact - seagate will not support linux.

It is hit and miss whether linux will recognise your drive - sounds like, you've been unlucky.

Hope someone else has a solution for you.

---

### Post by Phpaw on 2010-09-30
> **davidmohammed said:**
> a quick [google]("http://www.theinquirer.net/inquirer/news/1039498/seagate-snubs-linux") reveals that your HDD isnt linux friendly.  Infact - seagate will not support linux.

It is hit and miss whether linux will recognise your drive - sounds like, you've been unlucky.

Hope someone else has a solution for you.

It was working before ,but I don't know what happened :confused:

I think I did some things by mistake when I was trying to install a driver for Huawei E1550 Modem :(

Thank you davidmohammed.

---

### Post by bhaverkamp on 2010-09-30
This article suggest that the sleep feature can be disabled from a windows system. Then the drives should work fine with Linux.

---

### Post by jtingkir on 2010-10-01
Had the same problem, just bought the HDD (freeagent goflex 500GB-and I thought the mac compability thingy would help), the freeagent is not recognized at all (no entry on lsusb). 

Before plugged to my ubuntu, it's plugged to a win7, and yes I safely remove it before unplugging the device.

same problem detected here too: 
[http://newyork.ubuntuforums.org/showthread.php?t=1498124&highlight=freeagent](http://newyork.ubuntuforums.org/showthread.php?t=1498124&highlight=freeagent)

---

### Post by jtingkir on 2010-10-01
problem solved, I moved my seagate to another usb port and problem solved, apparently, the usb port didn't give enough power (thus my freeagent generate beeping sound).

you might wanna try "tail -f /var/log/messages" -> then see does ubuntu detects the usb freeagent being plugged. good luck mate!

---

### Post by Phpaw on 2010-10-06
> **bhaverkamp said:**
> This article suggest that the sleep feature can be disabled from a windows system. Then the drives should work fine with Linux.

no use :(
Thanks bhaverkamp.



> **jtingkir said:**
> problem solved, I moved my seagate to another usb port and problem solved, apparently, the usb port didn't give enough power (thus my freeagent generate beeping sound).

you might wanna try "tail -f /var/log/messages" -> then see does ubuntu detects the usb freeagent being plugged. good luck mate!

I tried to use another USB port but again no use :confused:
Thanks jtingkir.

---

