---
title: "Usb 3.0 testing"
date: 2011-01-22
forum: Hardware
---

### Post by psychok7 on 2011-01-22
Hi..how can i check my usb version (2.0 or 3.0) in linux and how can i check the speeds?

---

### Post by Yellow Pasque on 2011-01-22
Linux supports USB 3.0 since kernel 2.6.31. You can look at your USB info with:
```
sudo update-usbids
sudo lsusb -vv
```

---

### Post by psychok7 on 2011-01-23
> **Temüjin said:**
> Linux supports USB 3.0 since kernel 2.6.31. You can look at your USB info with:
```
sudo update-usbids
sudo lsusb -vv
```

thank thats it i guess.. but can't i filter the information? theres a lot of info coming out with that command..

---

### Post by psychok7 on 2011-01-23
forget about it.. i figured it out..thanks

---

### Post by psychok7 on 2011-01-23
READ somewhere about this command also sudo lspci | grep USB

---

### Post by Yellow Pasque on 2011-01-23
> **psychok7 said:**
> READ somewhere about this command also sudo lspci | grep USB
Shows your USB controllers.

---

### Post by soborobo on 2011-11-30
Thanks a lot for this information!

But still this does not explain why my USB 3.0 device does not show anything being mounted?  Supposedly Ubuntu only sees the drive if something is in IT at boot!  And once that the usb stick is removed, then nothing more is visible in the USB 3.0 device.  This happens under ubuntu 10.04.3  kernel .35 generic!

I would say that nothing is solved!  <but all is still an open question

---

