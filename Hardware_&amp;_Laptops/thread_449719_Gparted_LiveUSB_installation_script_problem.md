---
title: "Gparted LiveUSB installation script problem"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by ryu kun on 2007-05-20
I have followed instructions [here]("http://gparted.sourceforge.net/liveusb.php") but the script "set_usb.sh" gives this output:

```
 ----------------------------------------------------------------------
$                This script is to be run to copy files from GParted-livecd ISO file to usb stick. Run this script from the directory where you downloaded the GParted-livecd ISO file. I assume you have a usb stick formatted as FAT (or FAT32), with at least 55 MO free. You are now going to be asked the path where your usb stick is mounted.
-----------------------------------------------------------------------$

set_usb.sh: 27: function: not found
-en 

```

Then I tried to follow [this]("http://gparted-forum.surf4.info/viewtopic.php?pid=1725#p1725") but it fails in step 4 with this error: ```
mount: special device /dev/sdc1 does not exist
```

Any ideas?

---

### Post by ryu kun on 2007-05-20
Solved [here]("http://ubuntuforums.org/showthread.php?t=449741").

---

