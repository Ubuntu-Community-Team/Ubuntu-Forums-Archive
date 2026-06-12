---
title: "USB error and how to repair it error -71"
date: 2018-08-28
forum: Hardware
---

### Post by tt007-real on 2018-08-28
Hello
I'm trying to understand how the Ubuntu handle error related to usb driver.

I have a device that sometime causes to 
> [ 6309.880439] usb 1-2.4: device descriptor read/64, error -71[ 6310.107174] usb 1-2.4: New USB device found, idVendor=1bc7, idProduct=0021
[ 6310.107201] usb 1-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3 
The only way to re-stable the pc is to turn it off, pull out the power cord. Let it rest for 10 minutes, then turn it on and plug the usb again.
If I'll turn it on after a short time, let say a minute, it will continue to disconnect and reconnect repeatedly.

My questions are:
1. Why Ubuntu needs the 10 minutes rest in order to return to a stable state?
2. What might be the reason for this error?

The board is a custom made board with 4 telit modems connected via usb hub chip USB2514Bi.

I'm using Ubuntu 16.04 LTS

Thanks in advance.

---

