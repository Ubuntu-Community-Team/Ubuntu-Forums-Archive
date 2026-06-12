---
title: "Change premissions on USB nokia 6630"
date: 2008-07-27
forum: General Help
---

### Post by pjalegria on 2008-07-27
Hi 

How can i change the Volume premissions when i log my nokia 6630 by USB cable? I can read the volume but i cant write ...

Thanks

---

### Post by dexter.deepak on 2008-07-27
you should first unmount your usb-drive:
```
sudo umount /dev/<device_name>
```
then mount it with :
```
sudo mount -t <filesystem> -o rw,defaults <device_location> <Mount_Point>
```

---

