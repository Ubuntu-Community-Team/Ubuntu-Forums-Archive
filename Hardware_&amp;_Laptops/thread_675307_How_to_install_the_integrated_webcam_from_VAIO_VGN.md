---
title: "How to install the integrated webcam from VAIO VGN-SZ220"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by TheApe on 2008-01-22
Hi, All!
Can anyone help me installing the webcam for my VAIO VGN-SZ220?
I don't know how to start...
I tried easycam, but the camera wasn't showed on the list.

thank you

---

### Post by linuxwizard on 2008-01-23
Try using Ekiga see if webcam gets detected / works. Also post results from command > lsusb

---

### Post by TheApe on 2008-01-23
Here is lsusb results
But my webcam is integrated to the notebook,not a USB device.
Ekiga did not recognize the cam also.

```

Bus 005 Device 004: ID 05ca:1830 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Thank you

---

### Post by Daelyn on 2008-01-23
> **TheApe said:**
> Here is lsusb results
But my webcam is integrated to the notebook,not a USB device.
Ekiga did not recognize the cam also.

```

Bus 005 Device 004: ID 05ca:1830 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Thank you

I have the same webcam, works brilliant.

Tried compiling drivers etc as descibed in alot of other topics but could not manage to get it working.

[http://ubuntuforums.org/showthread.php?t=289836](http://ubuntuforums.org/showthread.php?t=289836)

In above topic, I found a .deb file for the webcam specific to my kernel (2.6.22). Installed and webcam works brilliant thereafter.

---

