---
title: "web cam"
date: 2009-08-30
forum: Hardware
---

### Post by dhaniljithkk on 2009-08-30
someone pls help me..i hav prblm with web cam..i installed cheese..but always shws 'camera not found' error..it works very well in win xp..

---

### Post by cos85 on 2009-08-30
If you don't give us more details, we can't help you!

Does your webcam come up when you run the lsusb command?

---

### Post by dhaniljithkk on 2009-08-31
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:6270 Microdia U-CAM PC Camera NE878
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

this is what i see when lsusb command runs..i tried dmesg command also..i can see my usb detected..but still i get camera not found error

---

### Post by BitJunkie on 2009-08-31
In a terminal, type ```
sudo gstreamer-properties
``` On the video tab, what is the value set to? Do you get an error when you click on Test?

---

