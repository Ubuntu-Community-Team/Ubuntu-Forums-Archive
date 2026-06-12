---
title: "Acer TravelMate ATI x600 driver"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by Sirron on 2006-10-01
This is kind of deeply annoying me now.

I've tried everything in my power, but my laptop's graphics on Linux are still terrible. I mean, I can't even use any GL screensavers because they run so slow.

It seems obvious to me that I haven't got the manufacturer's driver installed right, but I have got an ATI Control Panel installed. When I run it, it says "Driver does not provide the FireGL X11 extensions! Panel components will only operate partially." and in reality, all the panel shows is the version number.

So... who does supply the FireGL X11 extensions? And would getting them help?

thanks

---

### Post by ThaRabbit on 2006-10-02
I assume you're now using the distribution provided "ati" drivers ?

You can check by grabbing an editor and open /etc/X11/xorg.conf and look for something like this:
```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCI$
        Driver          "fglrx" (this entry)
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

```

I have a laptop with the X700 mobillity chip, there is a lot of information availble to install the ati created "fglrx" drivers which do support openGL and such. It's a common misunderstanding to think that the ubuntu release default installed "ati" drivers support 3d acceleration. You need the fglrx drivers.

Check here:
[http://www.ubuntuforums.org/forumdisplay.php?f=138](http://www.ubuntuforums.org/forumdisplay.php?f=138)

Or, more specific:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25)

---

### Post by Sirron on 2006-10-02
:o thanks very much! It's all working now!

The tutorial I originally followed didn't say anything about editing the xorg.conf file, although I followed this one from the beginning, I think just changing "ati" to "fglrx" might have solved the problem.

Now to revisit compiz...

---

