---
title: "DVD drive not in /dev"
date: 2012-08-31
forum: Hardware
---

### Post by erdalronahi on 2012-08-31
I had a broken CD drive which I removed from the configuration. 

Now I have a new DVD drive which is not recognized. In /dev the respective entries are missing (no /dev/cdrom/ , /dev/dvd, /dev/sr0)

How can I tell the system that there is a DVD drive installed now?

---

### Post by drmrgd on 2012-08-31
In wonder if the port you connected it to is not functioning or there's a problem with the drive.  Can you detect it in BIOS?  Maybe try a different SATA port?

You might also try the package 'hwinfo' (not installed by default)  to see if you can find it.  Once you install it, you can run:

```
sudo hwinfo --cdrom
```

If there are no connection problems, that should output details on the device and show you the /dev association.

---

### Post by erdalronahi on 2012-08-31
The problem was a loose cable, sorry to bother you. ):P

---

### Post by drmrgd on 2012-08-31
Excellent!  Glad it was a simple fix!

---

