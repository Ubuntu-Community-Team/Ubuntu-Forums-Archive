---
title: "external harddrive mount issues"
date: 2008-12-03
forum: Hardware
---

### Post by threatrix on 2008-12-03
I have an usb external hard drive with all my media files on it. To keep my programs seeing all my files I set a mount point. Unfortunetly I messed up the point now I can not mount my disk it gives me this error:
```

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually/)
```

is there any way I can fix this so I can mount my drive again?

---

### Post by taurus on 2008-12-03
Did you set the mount point in /etc/fstab?

```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by threatrix on 2008-12-03
no I set it in the properties menu in nautilus.

---

