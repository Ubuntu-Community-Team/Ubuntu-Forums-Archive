---
title: "Sony Vaio Problems"
date: 2008-05-22
forum: Hardware
---

### Post by awchen on 2008-05-22
I am completely new to Ubuntu and I have had issues getting my Bluetooth, FN key, and Webcam to work.  I have found a site which has posted methods to fix these.  However, I am unsure how to execute them.  Any help is appreciated.

[http://www.linux.it/~malattia/wiki/index.php/Sony-laptop](http://www.linux.it/~malattia/wiki/index.php/Sony-laptop)

---

### Post by astadolfo3 on 2008-05-24
Hello,

I have a vaio sz series and my camera works fine. what camera do you have? If you have a similar model I can show you my configuration. you can check your camera model as follows:

```
$ lsusb
**Bus 005 Device 004: ID 05ca:1835 Ricoh Co., Ltd **
Bus 005 Device 002: ID 054c:0281 Sony Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 044e:300d Alps Electric Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

in my case the camera is the first line, Ricoh 1835. What camera do you have?

---

### Post by TheApe on 2008-06-03
Hi!
I have the same cam. But couldn't get it to work.
Either erkiga or camorama recognize it

How did you get it to work?

Thanks

---

### Post by awks on 2008-07-27
Can you tell how you make it works? I have the same cam. 

> **astadolfo3 said:**
> Hello,

I have a vaio sz series and my camera works fine. what camera do you have? If you have a similar model I can show you my configuration. you can check your camera model as follows:

```
$ lsusb
**Bus 005 Device 004: ID 05ca:1835 Ricoh Co., Ltd **
Bus 005 Device 002: ID 054c:0281 Sony Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 044e:300d Alps Electric Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

in my case the camera is the first line, Ricoh 1835. What camera do you have?

---

### Post by bdiamond on 2008-08-23
I also have the 1835 Ricoh camera (Sony Vaio PCG-6Q1L running Hardy Heron) and got it working by following the second post by **astadolfo3** located here:
 [http://ubuntuforums.org/archive/index.php/t-289836.html]("http://ubuntuforums.org/archive/index.php/t-289836.html")
(just do a find for astadolfo3)

The only tricky part for me was figuring out how to enable the "hardy-proposed" repository which I found was in the updates section of synaptic. This had to be enabled to install required dependencies for the Ricoh drivers.

Let me know if this is helpful or if anyone wants a more explicit guide.

---

