---
title: "BCM4312 is the Devil"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by DreamClown on 2008-02-16
Wow. Getting wireless to work on my HPdv9000 (Gutsy 7.10) has been a hassle! I'm so frustrated atm. I have a Broadcom 4312 card and I've spent HOURS trying various How-To's and nothing has worked. I've tried ndiswrapper, WCID, using the restricted drivers, etc. and yet still no wireless. I'm either really missing something or my laptop is possessed. One thing I love about Ubuntu is the community. So, I'm hoping someone can help me work through this issue. Thanks in advance for your replies!

~DC~

---

### Post by yoeedzz on 2008-02-16
Hello, I have the same problem as you...
I installed ubuntu 7.10 on my Compaq Presario v3639au.
Using the native driver (from the restricted driver) make my system unstable, while using ndiswrapper make my modem undetected.
I also have to disable wireless on my network manager or else. my keyboard will hang after some time..
Anyone have the solutions?

---

### Post by DreamClown on 2008-02-18
Never mind. I got my wireless up by spending $35 on a Linksys wusb54gc and following this link: [http://ubuntuforums.org/showthread.php?t=516649&highlight=linksys+wusb54gc](http://ubuntuforums.org/showthread.php?t=516649&highlight=linksys+wusb54gc)

It had me up and surfin' in 10 minutes!

Peace,
~DC~

---

### Post by DreamClown on 2008-03-05
Update:

After two weeks of trying, I finally got my bcm4312 working also by following the instructions found here:
[http://ubuntuforums.org/showthread.php?t=701966](http://ubuntuforums.org/showthread.php?t=701966)

I hope this helps others too!

Peace,
~DC~

---

### Post by andrew.46 on 2008-04-21
Hi,

 I have just managed to get my BCM4312 up and going with Hardy RC1. Just to be clear the device is:

```
 Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
```

and I used the information on this page:

[http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old)

and so far so good.

    Andrew

---

