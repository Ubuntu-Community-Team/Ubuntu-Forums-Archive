---
title: "external hard drive"
date: 2009-04-08
forum: Hardware
---

### Post by hadjimurad on 2009-04-08
When accessing data on my external hard drive, after about four minutes or so I get an error message saying "internal data stream error" and whatever I'm using cuts out, e.g. if I'm playing music it will stop in the middle of it. What's going wrong here and how can I fix it? If I had to guess I'd say that the machine is assuming the hard disk is idle and turns it off.

---

### Post by agds on 2009-04-08
That's happened to me before.  How are you mounting it?  If you're using the built-in automounter in Nautilus/GNOME, that may be the problem.  Try mounting it manually from the command line:

```
sudo mount /dev/sdc1 /mnt
```

Of course, adjust the arguments to match your device path and mount point.  I'm not sure this works 100% of the time, but it seems to help.

---

