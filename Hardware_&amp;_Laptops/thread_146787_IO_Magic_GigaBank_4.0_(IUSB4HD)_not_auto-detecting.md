---
title: "I/O Magic GigaBank 4.0 (IUSB4HD) not auto-detecting"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by eqisow on 2006-03-19
As stated in the title, this portable USB HD will not auto-detect/auto-mount in Kubuntu/Ubuntu. USB flash drives all auto-mount fine, and the IUSB4HD auto-mounts fine in WinXP. I'm afraid I can't find anything reguarding this device and Linux. Has anybody had any experience with this or a similiar device? Any advice would be much appreciated. :)

Edit: I added the following line to my fstab and am able to mount it manually, but it still does not automount.

```
/dev/sdb1 /media/usb auto rw,user,noauto 0 0
```

---

