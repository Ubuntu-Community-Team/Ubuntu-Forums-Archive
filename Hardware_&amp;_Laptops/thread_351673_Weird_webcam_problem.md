---
title: "Weird webcam problem"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by Jad on 2007-02-02
I'm trying to get my webcam running, when I do 
```
lsusb I get Bus 003 Device 002: ID 041e:401a Creative Technology, Ltd , 
```

so the system can see it (sort 0f) but all other applications that uses webcam cannot see it, 
```

jad@syntux:~$ xawtv
This is xawtv-3.95, running on Linux/i686 (2.6.17-10-generic)
can't open /dev/video0: No such device
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such device
v4l2: open /dev/video0: No such device
v4l: open /dev/video0: No such device
no video grabber device available

```

---

### Post by Stemp on 2007-02-02
According to [Spca5xx]("http://mxhaard.free.fr/spca5xx.html") site, your card will be recognized soon. I guess you have to be patient ;)

---

