---
title: "USB Floppy Drive Not Mounting"
date: 2012-03-20
forum: Hardware
---

### Post by mlupton on 2012-03-20
Call me old fashioned, but I still use floppies from time-to-time especially when looking at some of my older documents. Until I installed 11.10, I had no issues with my external floppy drive and it had roughly the same "plug-and-play" compatibility that Windows 7 still has. I tried using this solution [http://www.securitybeacon.com/?p=1110](http://www.securitybeacon.com/?p=1110) which suggested the following.
```
  *Edit “/lib/udev/rules.d/**80-udisks.**rules” and search for the lines*
* ——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-*
* # PC floppy drives*
* #*
* KERNEL==”fd*”, ENV{ID_**DRIVE_FLOPPY}**=”1&#8243;*
 *# USB floppy drives*
* #*
* SUBSYSTEMS==”usb”, ATTRS{bInterfac**eClass}**==”08&#8243;, ATTRS{bInterfac**eSubClass}**==”04&#8243;, ENV{ID_**DRIVE_FLOPPY}**=”1&#8243;*
* ——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**——-**–*
 *Replace those “1&#8243; (ones) with “0&#8243; (zeros). That’s all the magic.*
* Now restart the udev daemon by typing “invoke-rc.d udev restart”*
 *You’re done. It should work now.*

```But this didn't help at all. I've tried changing some settings in udisks and have also tried ```
sudo modprobe floppy
``` but that doesn't work either. Has anyone else been successful in attaching a USB floppy drive to a machine running 11.10?

---

### Post by mlupton on 2012-04-02
Anyone??

---

