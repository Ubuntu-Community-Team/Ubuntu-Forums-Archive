---
title: "HP1102 printer"
date: 2013-08-22
forum: Hardware
---

### Post by mymoodz on 2013-08-22
I attached it with my computer through usb. I can not make it work. help please.

---

### Post by QIII on 2013-08-22
Hello!

What have you done to try to make it work?

---

### Post by mymoodz on 2013-08-22
I have installed hp lip service status on the top of my desktop. i went to its device manager but it says no hp equipment installed. i dont know what to do with it. the printer works just fine in windows. i just checked it.

---

### Post by mymoodz on 2013-08-22
i also tried the "printers" thing in system settings. i tried to add a printer but it wont recognize the printer

---

### Post by QIII on 2013-08-22
Forgive me for asking the obvious questions here, but I need to cover the basics.

Did you add the printer in System Settings?

Edit:  Bah!  We must have been typing at the same time!

---

### Post by QIII on 2013-08-22
You said it is attached via USB?

Could you post the results of 

```
lsusb
```

---

### Post by mymoodz on 2013-08-22
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 03f0:002a Hewlett-Packard LaserJet P1102
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 002 Device 003: ID 8086:0189 Intel Corp.

---

### Post by mymoodz on 2013-08-22
i also downloaded from this site. however, it is not unpacking after i have downloaded
[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

when i hit the first command it gave me this 

--2013-08-22 12:41:15--  [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
Resolving foo2zjs.rkkda.com (foo2zjs.rkkda.com)... 74.208.41.246
Connecting to foo2zjs.rkkda.com (foo2zjs.rkkda.com)|74.208.41.246|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1680682 (1.6M) [application/x-tar]
Saving to: &#8216;foo2zjs.tar.gz&#8217;

100%[======================================>] 1,680,682    109KB/s   in 26s    

2013-08-22 12:41:41 (64.2 KB/s) - &#8216;foo2zjs.tar.gz&#8217; saved [1680682/1680682]


but does not show any process with the next command. is there another command for unpacking?

---

### Post by mymoodz on 2013-08-22
i searched internet around. tweaked the command around and it is finally working. :) thanks.

---

### Post by mymoodz on 2013-08-22
[http://www.cyberciti.biz/faq/tar-extract-linux/](http://www.cyberciti.biz/faq/tar-extract-linux/)

used the command for extraction from this site

---

