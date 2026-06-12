---
title: "Saving files to usb"
date: 2008-11-29
forum: Hardware
---

### Post by timbob1957 on 2008-11-29
I am new to ubuntu so bare with me please...I am trying to save files to a usb device but to no avail..I am running 8.10...I hope this is a simple fix...I thought drag and drop might work..nope..please help

---

### Post by taurus on 2008-11-29
What filesystem is your USB drive and does it mount automatically when you insert it in?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
mount
```

---

