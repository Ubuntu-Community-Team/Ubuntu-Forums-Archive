---
title: "Webcam on HP dv6000"
date: 2009-09-12
forum: Hardware
---

### Post by Pazau on 2009-09-12
Hello everyone.

I have a HP dv6645eo with Ubuntu 9.04, and'm going to start using its built-in webcam with aMSN.

The only problem is that the webcam is not working properly. It is set in aMSN, but when it is used, open the webcam window and the picture immediately freezes.

It works correctly when testing it in aMSN preferences.

I go to Terminal and type lsusb, I get this output:

nicolas@nicolas-laptop:~$ lsusb
Bus 002 Device 002: ID 064e:a110 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
nicolas@nicolas-laptop:~$ 


When "Bus 002 Device 002: ID 064e:a110 Suyin Corp." is the cam.

Any help?

---

### Post by sergiom99 on 2009-09-13
have you tried it with cheese?
```
sudo apt-get install cheese
```

---

