---
title: "Built-in webcam does not work in Lucid."
date: 2011-11-01
forum: Hardware
---

### Post by PP_Bnn on 2011-11-01
Hi, one day the webcam of my laptop stopped working.
Few days before, sometimes worked and sometimes not.

Also, the device video0 disappeared:

```
pp@lima:~$ ll /dev/video*
ls: cannot access /dev/video*: No such file or directory
```

ideas?

Thank's!

---

### Post by matt_symes on 2011-11-01
Hi

Is the device being regconised ?

```
lsusb
```

Kind regards

---

### Post by PP_Bnn on 2011-11-01
it returns:

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

it seems don't recognize the webcam, really?

---

### Post by matt_symes on 2011-11-01
Hi

> Few days before, sometimes worked and sometimes not.

> it seems don't recognize the webcam, really?

From these two comments i would first check for a hardware issue such as a loose cable or other problem.

I would also suggest running a LiveCD/USB and see if the webcam is recognised then.

But my initial thoughts would be hardware.

Kind regards

---

### Post by PP_Bnn on 2011-11-01
ok, the webcam are broken =(

thank you very much!

---

