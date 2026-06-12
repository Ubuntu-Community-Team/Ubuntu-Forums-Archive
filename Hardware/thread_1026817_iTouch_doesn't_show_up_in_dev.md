---
title: "iTouch doesn't show up in /dev"
date: 2008-12-31
forum: Hardware
---

### Post by personjerry on 2008-12-31
So, my iTouch doesn't automount, doesn't show up in gParted. The obvious drives in /dev are not it. And I can't figure out the dmesg info:

```
[ 8486.079368] usb 5-5: USB disconnect, address 9
[13307.156028] usb 5-6: new high speed USB device using ehci_hcd and address 10
[13307.290325] usb 5-6: configuration #1 chosen from 3 choices
```

(this is the only relevant part. The address increases every time I plug the usb in again, everything else stays the same)

---

### Post by damis648 on 2008-12-31
iPod Touches and iPhones don't mount like drives. See [the wiki]("https://help.ubuntu.com/community/PortableDevices/iPhone").

---

### Post by personjerry on 2008-12-31
Ah but it shows a picture of requiring to connect to itunes to do nething at all but I can't connect to ubuntu for itunes via wine, so then i can't do the settings thing either.

---

### Post by Captain_tux on 2008-12-31
In fact, the iPhone doesn't appear as a phone at all... instead, Ubuntu thinks it's a camera!

---

### Post by damis648 on 2008-12-31
> **Captain_tux said:**
> In fact, the iPhone doesn't appear as a phone at all... instead, Ubuntu thinks it's a camera!

Actually, it is. It is designed that way so that the photos can be copied from the phone. It works the same way in Windows and OS X.

---

### Post by personjerry on 2008-12-31
but do you know how I can get past the first 'connect to itunes' screen?

---

