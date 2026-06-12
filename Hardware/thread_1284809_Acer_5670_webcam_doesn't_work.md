---
title: "Acer 5670 webcam doesn't work"
date: 2009-10-07
forum: Hardware
---

### Post by restart on 2009-10-07
Hello there!
There is a little trouble with webcam on my laptop (Acer Aspire 5670). It doesn't detected by both Cheese and Skype. But it is marked as supported on [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) , and:

```
pechenie@pechstation$ lsusb
Bus 001 Device 002: ID 046d:0892 Logitech, Inc. OrbiCam
```

and:

```
pechenie@pechstation$ lsmod | grep gspca
gspca_vc032x           25856  0 
gspca_main             29952  1 gspca_vc032x
videodev               41600  1 gspca_main
```

Any suggestions?

---

### Post by restart on 2009-10-07
up!
any suggestions?

---

### Post by restart on 2009-10-27
upgrade to Karmic (kernel .31) didn't helped me.
```
pechenie@pechstation:~$ uname -r
2.6.31-14-generic

```

Could anyone help me?

---

### Post by restart on 2009-10-28
bump

---

### Post by MadnessRed on 2009-10-28
Is that an external webcam or one that comes with the computer?

---

### Post by restart on 2009-10-28
> **MadnessRed said:**
> Is that an external webcam or one that comes with the computer?
It's "internal" one.

---

### Post by restart on 2009-10-29
Also
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so cheese
```
doesn't work for me.

---

### Post by jayhags on 2009-10-29
I have the same laptop and just upgraded from Jaunty to Karmic.  I had the webcam "working" under Jaunty via Cheese but it was very dim.  I have not tried Karmic yet but expect the same.

---

### Post by MadnessRed on 2009-10-29
I have the Aspire 5536 but my webcam is fine under cheese

---

### Post by ashish25888 on 2010-08-17
mine acer 5536 cam is not working cheese is also crashing.. what to do..device is busy.. skype is also not working

---

### Post by MadnessRed on 2010-08-17
You can only have 1 program using webcam at a time.

Also if 1 program crashes webcam, it won't work in any program until you restart.

---

