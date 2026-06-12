---
title: "Webcam stopped working but appears in lsusb, works fine in windows"
date: 2012-08-19
forum: Hardware
---

### Post by far on 2012-08-19
I posted this question in askubuntu.com a couple of weeks ago but to no avail, so far. I hope I will have better luck in this forum!

My System: Laptop Lenovo Thinkpad T420, Ubuntu 12.04 Precise

When I installed Precise, I could use my webcam without any issue (Cheese, Skype...) However, all of a sudden (I suppose after an update) it stopped working, Cheese showing me "no device found", but stll shows up in lsusb:

```
lsusb
Bus 001 Device 004: ID 04f2:b221 Chicony Electronics Co., Ltd integrated camera
```

However /dev/video0 does not exist...

I don't see how to debug this, I assume it must be easy since it used to work perfectly on this same machine and installation.

It is worth mentioning that the webcam is not damaged or disconnected as it is working flawlessly in my dual-boot windows partition. The only reason I boot on Windows now is to use Skype, since Ubuntu doesn’t allow me thus luxury...Any help would be greatly appreciated. Please let me know if you need more details.

Thank you!

---

### Post by unevenflow on 2012-08-19
Hey, try this for skype

```
echo -e '#!/bin/bash \n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype' | sudo tee /usr/local/bin/skype

sudo chmod a+x /usr/local/bin/skype
```

---

### Post by far on 2012-08-19
Hi 'unevenflow'. 

I tried what you suggest and Skype keeps showing "No video Device" in the options page.

I think the problem is more general than that since there is no /dev/video0. Any application that use the webcam as a capture device do not find video0, messages looking like "Unable to open file /dev/video0
No such file or directory"

I have poor knowledge in hardware issues, so any advice on how to debug this is welcome!

---

### Post by far on 2012-09-06
Please, anyone?

It works when I use the Live CD, so it must be something that has gone wrong after some update...

ANd I just thought about something: would rebuilding my kernel help?

---

