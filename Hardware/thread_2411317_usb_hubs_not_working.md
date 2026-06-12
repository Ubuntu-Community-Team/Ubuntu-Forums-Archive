---
title: "usb hubs not working"
date: 2019-01-28
forum: Hardware
---

### Post by jgw on 2019-01-28
I have 2 'ports' usb hubs (4 and 7 ports each - 'ports' is the brand).  Neither of these hubs will recognize anything plugged into them.  I have, for instance, a 16gb memory stick.  When I plug it into any of the usb ports I have, on my computer (2.0 and 3.0) the memory stick appears.  When plugged into the hubs, however, they are not recognized.  both hubs have a place to plug in power so I have done that (output 5.0v+-0.5v  1000mA+- 50mA) which, as far as I know, came with the hubs.  

I have seen suggestions to use:
modprobe -l utility.                              no utility
sudo hwls |more                                 no hwls

I also ran lsusb
first time, I had: Bus 011 Device 002: ID 05e3:0612 Genesys Logic, Inc. - 4 port
second time, it was gone
This, I think, is almost good although it didn't recognize the memory stick that was recognized on computer usb port
just checked the 4 port again - I think the first 3 ports are working - no sure about the 4th

7 port just doesn't get recognized or work  (usb 3.0)

I just connected a 7 port usb2.0 hub.  Here are some results:
```
greg@gregdown:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 013 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 012 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 003: ID 2d42:5200  
Bus 011 Device 002: ID 05e3:0612 Genesys Logic, Inc. 
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 004: ID 0922:001a Dymo-CoStar Corp. LabelWriter 400 Turbo
Bus 010 Device 003: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
Bus 010 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The one above was before I added the 7port, usb 2.0 hub

```
greg@gregdown:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 0a05:7211 Unknown Manufacturer hub
Bus 003 Device 006: ID 0a05:7211 Unknown Manufacturer hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 013 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 012 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 003: ID 2d42:5200  
Bus 011 Device 002: ID 05e3:0612 Genesys Logic, Inc. 
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 004: ID 0922:001a Dymo-CoStar Corp. LabelWriter 400 Turbo
Bus 010 Device 003: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
Bus 010 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
greg@gregdown:~$ Bus 011 Device 002: ID 05e3:0612 Genesys Logic, Inc.
``` 

This is what I got after I plugged in the 7port hub. 

Then I added a usb 2.0 thumb drive and got (still will not recognize usb 3.0 thumb drive):
```
greg@gregdown:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 008: ID 1221:3234 Unknown manufacturer Disk (Thumb drive)
Bus 003 Device 007: ID 0a05:7211 Unknown Manufacturer hub
Bus 003 Device 006: ID 0a05:7211 Unknown Manufacturer hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 013 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 012 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 003: ID 2d42:5200  
Bus 011 Device 002: ID 05e3:0612 Genesys Logic, Inc. 
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 004: ID 0922:001a Dymo-CoStar Corp. LabelWriter 400 Turbo
Bus 010 Device 003: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
Bus 010 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


Would appreciate any thoughts on this one.

---

### Post by jgw on 2019-01-30
After constant futzing around I have found that my usb hubs will not allow 3.0 in 2.0 hubs and 2.0 in 3.0 hubs.  Sometimes they might work but, for the most part they will not.  The hubs in question are branded 'ports' 

I have been under the impression that all versions of usb were compatible.  I guess this is wrong too?

I am going to mark this one as solved.

---

