---
title: "Chicony Webcam not working"
date: 2008-04-28
forum: Hardware
---

### Post by spraveenitpro on 2008-04-28
Hi 

I have a Compaq C768TU [Hardy Heron] with integrated Chicony Webcam :

[COLOR="Red"]home@home-laptop:~$ lsusb | grep Chi
Bus 004 Device 004: ID 04f2:b057 Chicony Electronics Co., Ltd [/COLOR]

I installed Linux+UVC  , but when I start Camorama Webcam viewer ,
it says :  

[COLOR="Red"]Could not connect to video Device [/dev/video0].Please check connection.[/COLOR]

Pls let me know what can be done to get this working.

Thank you . Praveen.

---

### Post by starcannon on 2008-06-27
I have gotten as far as getting the camera to work for 10-30 seconds, then it seg faults out.

I'm using the UVC driver from here: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

The table lists this camera as fully functional, but with Cheese and Skype I get the same result, camera locks up, seg faults, then turns off.

Anyone gotten this bug figured out yet?

---

### Post by starcannon on 2008-06-27
Heres the output of lsusb:

```

Bus 007 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd 

```

Using the latest svn from berlios the camera still locks up, sometimes it crashes, sometimes it just sits there locked up.

---

