---
title: "acpi=off, no wifi; acpi=on no usb storage, what to do?"
date: 2013-05-04
forum: Hardware
---

### Post by harveyp on 2013-05-04
UBUNTU 12.04.01
new install

FUJITSU SIEMENS AMILO L7310/8650

raw -> no usb storage visible, although usbhid mouse works, albeit slowly
acpi=off -> no bootable disks seen as bootable, no wifi connection, BUT usb storage is visible!!
acpi=off added with boot-repair which can mount my usb storage under /mnt/boot-sav/ before the changes are executed
but I can't mount my usb storage with usb-mount (vfat not a valid format), pmount or mount

What am I not doing? What am I doing incorrectly?

I need both wifi AND usbstorage working. I've already lost access to my printer ...

Harvey

---

### Post by Toz on 2013-05-04
Can you try the following kernel boot parameters? One at a time then check if usb and wireless work:
```
acpi=force
```
```
irqpoll
```
```
acpi=force irqpoll
```

---

### Post by harveyp on 2013-06-02
> **Toz said:**
> Can you try the following kernel boot parameters? One at a time then check if usb and wireless work:
...
```
acpi=force irqpoll
```

Thanks a lot!! 

So far so good!! 

I now have wifi AND detection of/access to usb storage connected at bootup. Now if I could swap my usb storage without rebooting ...

It is much improved now so thanks anyway  :D

Harvey

---

