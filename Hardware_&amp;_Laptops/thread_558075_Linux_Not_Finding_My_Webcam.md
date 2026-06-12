---
title: "Linux Not Finding My Webcam"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by amneziac on 2007-09-23
For some reason when i try ti install my Linux Logitech Quickcam driver, it says it could not find my webcam, why not? I am running on dual boot with windows XP and my webcam used to work perfectly fine but then i had to reinstall windows and i had the webcam in before i installed the software and ever since then it hasnt been working as well as it should which is probably why linux wont recognize it. I tried reinstalling the driver in windows but it still gets errors like "the webcam is not connected" eventhough it is. Any way i can fix all of this?

---

### Post by w4ett on 2007-09-23
to check if it is being recognized, in the terminal type:

```
lsusb
```

---

### Post by amneziac on 2007-09-23
Bus 002 Device 005: ID 046d:08ca Logitech, Inc. 

yeah it sees it but on the actual driver installation it cant find it :confused:

---

### Post by w4ett on 2007-09-23
There was a discussion about that card here:

[http://ubuntuforums.org/showthread.php?t=529271](http://ubuntuforums.org/showthread.php?t=529271)

---

