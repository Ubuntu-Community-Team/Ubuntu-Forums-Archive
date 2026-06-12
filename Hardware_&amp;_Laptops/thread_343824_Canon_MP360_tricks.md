---
title: "Canon MP360 tricks"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by tdatu on 2007-01-22
hello devoted linux users! 
for anyone having difficulties of making Canon MP360 to work, including printing and scanning, here is some tricks that I found just my trial and error and of course with some sheer luck!
I'm running:
AMD64 3000+
1GB RAM
Ubuntu Dapper Drake

For Printer Settings:
I use canon s600 driver - it prints the right scale.

For Scanner Settings:
Download Version 0.12.2 [here.]("http://home.arcor.de/wittawat/pixma/") and follow the installation instruction.
Unfortunately, xsane gui cannot detect the scanner(due to permission on the devise (USB), so I control the scanner using the terminal command like this:
"your_id@ubuntu$ sudo pixmascan"
this command should show you a lot of option such as colors, dimensions, and where to put the scanned image, but typically I just type:
"your_id@ubuntu$ sudo pixmascan /folder location/scanimage.tif -1"
option -1 should tell the scanner to scan the whole page in raw format.

peace out!
-tdatu

---

### Post by hawkwing3141 on 2007-03-31
Thanks for the tips.  I also had to do the following (running Kubuntu 6.10): 

```
sudo cp /usr/src/linux-headers-2.6.17-10/include/linux/compiler.h /usr/include/linux
```

because it wouldn't compile.

Also I have the scanner freezing problem mentioned at the PIXMA site, but to save wear and tear on the USB cable from the unplugging/plugging needed to restart it, I found I could do the following:

```

sudo modprobe -r uhci_hcd
sudo modprobe uhci_hcd

```

which resets the USB connection and allows more scanning.  

I've also implemented this as a shell script to make it easier for me.  The following script scans a 4x6 print at 600dpi (about 30mb per file), saves it as a tif by the date and time, and resets the USB port (which requires sudo access -- the first time you use it you will need to enter your password but then if you don't take too long between scans it shouldn't ask you for it every time).

```

#!/bin/bash
SAVEDATE=$(date +%F-%H-%M-%S)
pixmascan -w 120 -h 150 scan${SAVEDATE}.tif -r 600 -1
sudo modprobe -r uhci_hcd
sudo modprobe uhci_hcd

```

---

### Post by oleanderkiro on 2008-02-04
Hello,

I'm Joachim and I'm new in the forum.
I've the same problems with my mp360 scanner.
But I want to work with xsane and I think there is something to do with the access rights after
installing, but I don't no what.
The reset like descripted doesn't work on my system.
Can anybody help me to complete the function of my scanner.
I find the advise from you is not the best way to scan.


mfg

Joachiim

---

### Post by oleanderkiro on 2008-02-25
Hello,

I've found a solution.

I've add a line into the file /etc/fstab:

usbfs /proc/bus/usb usbfs auto,devmode=0666 0 0 

and now I can work as normal user with xsane.



mfg


Joachim

---

