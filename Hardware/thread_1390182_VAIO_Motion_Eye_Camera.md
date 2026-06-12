---
title: "VAIO Motion Eye Camera"
date: 2010-01-25
forum: Hardware
---

### Post by twisterplus on 2010-01-25
I've got a sony VAIO FE890
I've been looking all around the net for the solutions to get my built-in camera working.
Here's the output of my '**lsusb**':

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:1836 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

The weird thing about the camera is that when I first start my Windows and then restart to UBUNTU the camera is working fine, but when I directly login to my UBUNTU on startup I get the following error:

```
[   25.338105] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1836)
[   25.348282] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   25.371524] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26)
``` 

Anyone has a clue what is wrong?
BTW I am on karmic.

---

