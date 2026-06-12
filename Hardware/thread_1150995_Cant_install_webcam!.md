---
title: "Cant install webcam!"
date: 2009-05-06
forum: Hardware
---

### Post by B4RR13N705 on 2009-05-06
Hi, i have a Delux webcam, im not sure about the model. When i type lsusb i get:
```

dropedrobarri@ubuntudesktop:~$ lsusb
Bus 008 Device 006: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 008 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 006: ID 03f0:0a01 Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 002 Device 002: ID 093a:2620 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 0000:0000

```
It has a microphone in it. I thinks that is the Pixart one, one for the camera and other for the micro. In win XP it works erfectly, but nothing in ubuntu. Any idea??

---

### Post by Infinity-al on 2009-05-12
I had the same problem myself... Upgrading kernel to 2.6.29 fixed the video part, cam works perfectly. Sound is another story, haven't gotten it to work yet.

Here's how to:
[http://karuppuswamy.com/wordpress/2009/03/01/howto-gear-head-web-cam-093a2620-in-linux/](http://karuppuswamy.com/wordpress/2009/03/01/howto-gear-head-web-cam-093a2620-in-linux/)

Check that and particularly the note for ubuntu users, it'll save you a lot of trouble. It'll be as easy as installing couple of debs.

---

### Post by B4RR13N705 on 2009-05-12
Ill try that tutorial and then i tel you. Anyway, i will keep looking for the Webcam's Mic.

---

### Post by Infinity-al on 2009-05-12
> **B4RR13N705 said:**
> Ill try that tutorial and then i tel you. Anyway, i will keep looking for the Webcam's Mic.

Ok... Keep me updated

---

### Post by B4RR13N705 on 2009-05-13
I didn get anything. It still doesnt work. Anyway, the priority is the "mic". :popcorn:

---

### Post by Infinity-al on 2009-05-13
> **B4RR13N705 said:**
> I didn get anything. It still doesnt work. Anyway, the priority is the "mic". :popcorn:

Frome [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/")

Install the linux image and headers respective to your architecture. It'll install the new kernel version. Just get the debs and install them.

---

### Post by B4RR13N705 on 2009-05-14
i'll try.

---

