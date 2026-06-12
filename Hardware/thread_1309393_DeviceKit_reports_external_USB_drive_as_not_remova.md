---
title: "DeviceKit reports external USB drive as not removable"
date: 2009-11-01
forum: Hardware
---

### Post by polo-78 on 2009-11-01
Hi everyone.
I'm using Ubuntu 9.10 AMD64, installed when it was still Beta and then flawlessly upgraded. I'm having a problem with the XBMC Media Center (launched in standalone mode, that is without GNOME running) not mounting some of my external USB hard disks. A quick look at the info provided by DeviceKit-disks shows that those disks are not being reported as removable (the "removable" flag is 0). XBMC is configured to automount removable devices only, so that's why it doesn't mount them. USB thumb drives work correctly (DeviceKit reports them as "removable: 1").

Is this a bug in DeviceKit, or maybe in the kernel itelf? Any idea on how to fix it?

Thanks in advance!

---

### Post by polo-78 on 2009-11-03
up!

---

### Post by vikjon0 on 2010-03-18
no takers on this on? I have the same problem with 32bit 9.10

---

