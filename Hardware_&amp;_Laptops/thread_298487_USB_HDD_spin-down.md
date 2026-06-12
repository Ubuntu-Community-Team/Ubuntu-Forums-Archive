---
title: "USB HDD spin-down"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by Ben Jao Ming on 2006-11-12
Hi all,

So I'm trying to spin-down my external USB-drive since it's mainly used for nightly backups.. but all this failed:

hdparm, sdparm and scsi-spin

Is there another way?

I know why hdparm and sdparm doesn't work, and I have a feeling that scsi-spin isn't supposed to work, either.. but currently it produces a kind of weird err:

```
root@hostname:~# scsi-spin -d /dev/sda
SG_IO: status = 0x2 cmd = 0x1b
No such file or directory
```

Thanks for reading!

/ Benjamin

---

### Post by Bd0g on 2007-07-14
Old thread to pick up on.. but I thought it would be nice to add this as a suggestion:

[http://hd-idle.sourceforge.net/](http://hd-idle.sourceforge.net/)

---

### Post by smoker on 2007-07-14
> **Bd0g said:**
> Old thread to pick up on.. but I thought it would be nice to add this as a suggestion:

[http://hd-idle.sourceforge.net/](http://hd-idle.sourceforge.net/)

hi, thanks for that link, BdOg,

cheers :-)

---

