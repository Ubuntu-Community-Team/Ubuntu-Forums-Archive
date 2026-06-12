---
title: "Modprobe hdaps_ec"
date: 2008-08-27
forum: Hardware
---

### Post by philgenius on 2008-08-27
I ran the following command to get use out of the accelerometer on my Thinkpad T60 with Hardy on it:

```
~$ sudo modprobe hdaps_ec
```

and it outputs this:

```
~$ WARNING: Error inserting thinkpad_ec (/lib/modules/2.6.24-19-generic/ubuntu/misc/thinkpad_ec.ko): No such device or address
~$ FATAL: Error inserting hdaps_ec (/lib/modules/2.6.24-19-generic/ubuntu/hwmon/hdaps_ec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Why is this?

---

