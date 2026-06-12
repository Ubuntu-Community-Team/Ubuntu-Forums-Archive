---
title: "USB modem"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by davidgutu on 2007-09-11
Can anyone please tell me how to install an LG USB modem so that I can connect to the net using Ubuntu? :)


Thanks Geraldm. I have solved it. It was easier to connect using Kubuntu's KPPP

---

### Post by geraldm on 2007-09-11
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Using ubuntu, try plugging the USB modem in. Locate the device in /proc/bus/usb/devices
and see if there is a driver named for it, such as cdc_acm
Look in the logs for the name of the device.  
Log:
usb 2-1: new full speed USB device using uhci_hcd and address 2
usb 2-1: configuration #2 chosen from 2 choices
usb 2-2: new low speed USB device using uhci_hcd and address 3
usb 2-2: configuration #1 chosen from 1 choice
cdc_acm 2-1:2.0: ttyACM0: USB ACM device

This log shows that the device name is ttyACM0.  
Then use YOUR device name when the configuration scripts call for the device: /dev/ttyACM0

Normally a configuration script is used to set up the files in /etc/ppp/*.
That program can probably be found in /usr/sbin/

Try using a HOWTO if you can, and if you cannot continue, post.

Gerald

---

