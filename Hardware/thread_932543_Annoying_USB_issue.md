---
title: "Annoying USB issue"
date: 2008-09-28
forum: Hardware
---

### Post by jason6g on 2008-09-28
Ok

laptop is a dell 1501

ALL usb works perfectly fine under windows XP and windows vista

Usb:
1 usb hub
1 usb receiver for wireless mouse
1 usb charging cable to charge the wireless mouse

Usb drives:
1 usb 256mb flash drive (fat)
1 usb 2gb flash drive (fat)
1 usb 320gb external hard drive (ntfs)

The problem - ALL usb crashes when sending/receiving data from any of the usb drives.

My resolution has always been to run:

```
sudo modprobe -r ehci_hcd
sudo modprobe ehci_hcd
```

in the terminal, but just today this stopped working, and the drive crashes again.

after about half an hour worth of trying to fix this I gave up, went over to windows and all usb works PERFECT on same hardware so I believe its not a hardware issue

I am running ubuntu 8.04 - and I never had any usb issues when running fiesty

If I must give up USB 2.0 to get things to just work so be it, but it is so annoying that this does not work.

Please list any log outputs which would help in getting this resolved, and also help point me in the right direction to a resolution.

Thank you!

---

### Post by jason6g on 2008-09-28
bump :/

---

### Post by Sef on 2008-09-28
Please wait 24 hours before bumping your thread.

---

