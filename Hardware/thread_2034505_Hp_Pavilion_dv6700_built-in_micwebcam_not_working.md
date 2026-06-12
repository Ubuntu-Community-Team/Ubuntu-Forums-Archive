---
title: "Hp Pavilion dv6700 built-in mic/webcam not working"
date: 2012-07-28
forum: Hardware
---

### Post by fieraj on 2012-07-28
Hey everyone, I am a relative newbie to Ubuntu and I am having some trouble getting my built-in microphone/webcam to work. I am using a Hp Pavilion dv6700 on Ubuntu 12.04. Any help would be very appreciated. I really want to ditch windows.

---

### Post by mörgæs on 2012-07-30
Hi, welcome to the fora.

Please post the output of ```
lsusb
```.

---

### Post by fieraj on 2012-08-01
Thank you and here you go

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a110 Suyin Corp. HP Webcam
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]

```.

---

### Post by mörgæs on 2012-08-01
Good, so hardware is detected.

Please describe exactly what the problem is when trying (for example) Guvcview and Cheese.

---

### Post by fieraj on 2012-08-01
Ohh weirdly enough, the webcam is working fine now, but the microphone doesn't work, when for example in a call using Skype.

---

### Post by mörgæs on 2012-08-01
Have you tried the settings in **alsamixergui**, including the microphone boost?

---

### Post by fieraj on 2012-08-02
It doesn't have the mic boost, just master and capture, and on the capture one, I cant seem to turn it up for some reason.

---

### Post by mörgæs on 2012-08-02
Then I guess it's best to post in the [multimedia]("http://ubuntuforums.org/forumdisplay.php?f=334") forum.

---

### Post by fieraj on 2012-08-02
ohh then how do i move this thread then

---

### Post by mörgæs on 2012-08-03
It's better to open a new thread (provided you don't find anything of value while searching) stating the problem in all details.

---

