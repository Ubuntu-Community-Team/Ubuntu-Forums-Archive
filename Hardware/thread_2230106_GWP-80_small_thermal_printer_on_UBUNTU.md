---
title: "GWP-80 small thermal printer on UBUNTU"
date: 2014-06-17
forum: Hardware
---

### Post by james3 on 2014-06-17
Hello everyone,
I just bought an GWP-80 portable thermal printer and I was  trying to make it works in Ubuntu  14.04 OS (in Windows works perfectly)

when I plug it into usb the system recognize an unknown printer  then I tried to install  through the wizard a generic text only driver but it didn't worked.

So I tried to run  *lsusb* comand here is the output for the printer

```

Bus 003 Device 004: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
```

 Seems that the printer even if it  **ONLY HAS A USB** plug,  has an embedded  usb-to-parallel chip installed.

then I checked and  /dev/usb/lp1  device is present on my system

Anyone has an Idea about how to make this small printer works in UBUNTU ?

---

