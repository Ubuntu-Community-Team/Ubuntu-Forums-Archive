---
title: "HP Pavillion dv9000 built in webcam not working"
date: 2008-11-22
forum: Hardware
---

### Post by parakeets11 on 2008-11-22
I've searched for hours on end to find a thread that solves my dilemma, but have been unfortunate.  Can someone send me a thread or tell me how to get it working?  It says that my webcam is not found.

---

### Post by Yezinki on 2008-11-23
Try ```
lsusb
```

Regards,

Yezinki.

---

### Post by parakeets11 on 2008-11-23
Ok when I do that I get:
```
daniel@daniel-laptop:~$ lsusb
Bus 002 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
daniel@daniel-laptop:~$ 

```

Is there something else I need to do?

---

### Post by JimmyBEng on 2008-11-23
This tells you that you have the Ricoh 1810 webcam.  If this isn't working for you, you may need to work with the R5u870 driver.

The website for it is here: [http://wiki.mediati.org/R5u870]("http://wiki.mediati.org/R5u870")

I'm having trouble reaching it right now, so you may need to use google to help you find it.

I have a slightly different webcam, so I don't know the details of working with the 1810.

---

### Post by Yezinki on 2008-11-23
> **parakeets11 said:**
> Ok when I do that I get:
```
daniel@daniel-laptop:~$ lsusb
Bus 002 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
daniel@daniel-laptop:~$ 

```

Is there something else I need to do?

Since am not using 8.10 any more, what you need to do is contact/ PM linux23dragon for assistance in compiling a driver for your Ricoh webcam.

Hope this model is Linux compatible....

Regards,

Yezinki.

---

### Post by parakeets11 on 2008-11-23
Ok, I found the driver and installed the .deb, but no programs detect it.  I'll PM linux23dragon when I get the chance, but if its not compatible, then I guess I'm force to get a new webcam D:.

---

### Post by aquamammal on 2008-11-24
Yeah, in the same boat as you.

But I got a:

1870 Ricoh Co., Ltd

---

### Post by Yezinki on 2008-11-24
My suggestion would be to buy a quality cam like Logitech Quick Cam Pro 9000, that works with aMSN, Skype etc,hassle free, no requirements of driver compilation/ Ubuntu 8.10 compatibility....

Regards,

Yezinki.

---

