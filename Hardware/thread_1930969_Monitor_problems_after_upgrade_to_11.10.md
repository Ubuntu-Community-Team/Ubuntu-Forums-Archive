---
title: "Monitor problems after upgrade to 11.10"
date: 2012-02-24
forum: Hardware
---

### Post by hodad on 2012-02-24
My screen gets hosed a couple of times a day (sometimes scrambled, sometimes goes blank).

Would it help to try and install a new driver for the specific monitor, or just some generic driver?

Princeton LCD 19D (around 6 years old?)
New Biostar N68S Mobo
GeForce 6150SE/nForce 430 chipset
AMD Quad Core processor

Thanks

---

### Post by roelforg on 2012-02-24
If it's a nvidia card:
```

sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-updates

```

---

### Post by grahammechanical on 2012-02-24
The drivers that we install in Linux are for the video card not for the monitor. Something called X Server passes the video signal to the monitor through the video card. Every time we boot the X Server reads a configuration file on the monitor to get the monitor settings.

You should have a Nvidia X Server Settings Utility. Try using that to see if you are using the optimum settings for the monitor.

Also make sure that the video card is not over heating. From experience I know that an overheating video card can mess up the monitor settings and in the end fail to read the monitor settings file. That Nvidia utility should give you a temperature for the video card.

Also check the video cable for wear or damage.

Regards.

---

### Post by hodad on 2012-02-28
Thanks to both of you for your replies.  Good explanation. I will do some more digging into NVidia.  Settings don't appear to be optimal. Can't seem to change anything thru the program, but did see that it's looking for an "EDID" file.  I'll look into that.

---

