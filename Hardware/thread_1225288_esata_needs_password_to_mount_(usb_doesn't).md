---
title: "esata needs password to mount (usb doesn't)"
date: 2009-07-28
forum: Hardware
---

### Post by jtappin on 2009-07-28
I have an external hard drive that can be connected via esata or usb. When I connect by either method, the "Device notifier" tells me it's been connected and offers to open it in the file manager.

The difference is that with esata, I then get a prompt for my password (i.e. sudo is needed to mount it), while this does not happen with a USB connection. The same occurs when unmounting.

In both cases, after the disk is mounted, both /dev/sdb and /dev/sdb1 have ownership root:disk and permissions rw-rw----.
My groups (other than my primary group) are:
```
adm disk dialout cdrom sudo audio plugdev lpadmin admin sambashare
```

Is there some other group I need to add? and if so what?

N.B. In the original System76 set up I was not in group disk and then all external disks (including USB pen drives) asked for a password.

---

