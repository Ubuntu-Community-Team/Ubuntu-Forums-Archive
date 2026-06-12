---
title: "apcusbd Help"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by no_klu on 2007-11-08
I am trying to get my APC Back-UPS NS working. I downloaded apcusbd, apcusbd-cgi via synaptic. I read in the forums that I need to insure ubuntu has found the usb connection to the UPS. I did this " cat /proc/bus/usb/devices" and got back the response "cat: /proc/bus/usb/devices: No such file or directory" I'm very new to linux and don't know what I should do next. Thanks for your help.

---

### Post by MrFSL on 2007-11-08
Try perhaps:

```
sudo lsusb
```
or```
sudo lsusb -v
```

---

### Post by no_klu on 2007-11-12
I tried "sudo lsusb" and got back "Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500" which means that ubuntu knows that the UPS is attached. I think the next step would be to see if a driver is installed for the UPS. But how?

---

### Post by no_klu on 2007-11-12
I checked under system -> preferences -> hardware information and found listed under UHCI Host Controller an entry for the UPS. I can't tell if the driver is installed but it looks like it to me. The device type says "hiddev","battery". I tried to start the daemon using "~$ /etc/init.d/apcupsd start and got back "Please check your configuration ISCONFIGURED in /etc/default/apcupsd" 
I'm not sure what to do now.

---

