---
title: "Built-in Webcam"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by rosiny on 2007-04-28
I'm using a sony vaio sz-390 laptop with a built-in webcam, and when I try to use camorama or easycam2, no devices are detected... how can I fix this?

---

### Post by rosiny on 2007-04-30
Hmm. Does anyone have any suggestions?

---

### Post by rosiny on 2007-04-30
Okaaay. Should I take this as a no? :P

---

### Post by loell on 2007-05-01
in the terminal , type
```
lsusb
```

post the results here,
so that we'll know the device id

---

### Post by thoman on 2008-05-04
Hello there
Iam using Twinhead with 8.04 and cannot detect my built in web cam


lsusb

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05e3:0503 Genesys Logic, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000

---

### Post by loell on 2008-05-06
you might have to wait a little while, as the linux driver for that webcam is not yet ready for prime time as of this writing.


[http://www.reactivated.net/weblog/archives/2008/04/gl860-more-devices-colour-images/#comments]("http://www.reactivated.net/weblog/archives/2008/04/gl860-more-devices-colour-images/#comments")

---

### Post by theZoid on 2008-05-13
> **loell said:**
> you might have to wait a little while, as the linux driver for that webcam is not yet ready for prime time as of this writing.


[http://www.reactivated.net/weblog/archives/2008/04/gl860-more-devices-colour-images/#comments]("http://www.reactivated.net/weblog/archives/2008/04/gl860-more-devices-colour-images/#comments")

I guess I'll be waiting also for the genesys driver...

---

