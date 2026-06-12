---
title: "usb_modeswitch help"
date: 2009-12-18
forum: Hardware
---

### Post by pythonsyntax on 2009-12-18
here the link where i try to understand how to work usb_modeswitch [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

here what i get:

No default vendor/product ID given. Aborting.


I useing a mc760 modem for virgin modile wireless2go

---

### Post by IcarusR on 2009-12-18
At a guess you need to give the program some info.

You will also have to give us more info to be able to do any thing.

---

### Post by IcarusR on 2009-12-18
I googled 'usb_modeswitch' & found this for you

[http://www.greenhughes.com/content/using-huawei-e169g-usb-mobile-internet-modem-eee]("http://www.greenhughes.com/content/using-huawei-e169g-usb-mobile-internet-modem-eee")

I suggest you try [www.google.com](www.google.com) next time.

---

### Post by pythonsyntax on 2009-12-19
I want to get my mc760 to work that my point.

---

### Post by IcarusR on 2009-12-19
Have you tried reading on the usb_modeswitch forum & posting your situation there ??

---

### Post by pythonsyntax on 2009-12-19
I try sign up there on the forum but it won't let me and yes i read the doc still don't understand it.

---

### Post by OfNoNation on 2009-12-19
Run lsusb in a terminal and see if you can identify your device in the list.
```
lsusb
```Mine looks like this
> Bus 001 Device 003: ID 5986:0102 Acer, Inc Crystal Eye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 1dbc:0005  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 1c4f:0002 SiGma Micro 
Bus 003 Device 003: ID 1b1a:0000  
Bus 003 Device 002: ID 03eb:0902 Atmel Corp. 4-Port Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
If you can't determine which is the device in question, disconnect it, run lsusb, reconnect it, run lsusb and compare the two outputs.
Note the ID of your device, e.g., ID 1dbc:0005 (above).  They are the Default Vendor ID (1dbc) and the Default Product ID (0005).
Open /etc/usb_modeswitch.conf and scroll down the page looking for those numbers (or do a search for one of them).  If you find them, uncomment (remove the ';' from the start of the line) all the lines in that section.

If your device isn't there, get back here and we'll go a little further

Questions: 
Does your device appear as a storage volume (CD) in Nautilus when you hot-plug it?
If so, does it switch to modem mode when you 'eject' (as opposed to unmount) the volume?

Also, the developers at USB Modeswitch tell me that the new release is due out this weekend and can handle many more devices than 1.05.

I've just been through this, with a very happy ending.

---

### Post by pythonsyntax on 2009-12-19
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 1410:5031 Novatel Wireless 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by OfNoNation on 2009-12-19
Okay.  can you.... disconnect the device, run lsusb, reconnect the device, wait a few seconds, run lsusb, and post both outputs here.

Also, could you answer the questions I asked before.

Edit:

Sorry... Just woke up.

Just the answers to the questions will do.

---

### Post by OfNoNation on 2009-12-19
Your device's DefaultVendor ID is 0x1410 and the DefaultProduct ID is 0x5031
/etc/usb_modeswitch.conf has entries for that Vendor, but not the device.

I suggest you find an instance of ';DefaultVendor=  0x1410', change the 'DefaultProduct=' value to '0x5031'
Remove the ';' at the beginning of every line in that section that has one. > save > run usb_modeswitch at the prompt.
Post the text from the terminal after usb_m has said 'Bye!'.

Questions:
Does the device appear as a storage volume (CD) in Nautilus when you connect it?
If so, does it switch to being a modem when you 'eject' the storage device?

---

### Post by pythonsyntax on 2009-12-19
I remove this ;  on the /etc/usb_modeswitch.conf  by my modem that supported here the output:smile:

 usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 No default device found. Is it connected? Bye.

Well i do get a icon on my desktop said wireless2go a icon like a cd.

---

### Post by pythonsyntax on 2009-12-19
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

this is without the modem in my usb ports output.

---

### Post by pythonsyntax on 2009-12-19
I got it connected but it is very slow on linux on windows it fast.odd

---

### Post by OfNoNation on 2009-12-23
USB Modeswitch 1.0.6 has been released - [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch) and I see your device is now supported. 

######################################################## 
# Novatel MC760 3G
#
# Contributor: Matt Roberds 

DefaultVendor=  0x1410
DefaultProduct= 0x5031

TargetVendor=   0x1410
TargetProduct=  0x6002

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"

Either copy this and overwrite the uncommented entries in /etc/usb_modeswitch.conf, or download the updated version here > [http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf) and save it to /etc .

I would recommend downloading the complete new release and starting from scratch because the developers have made other changes.  You shouldn't have to do anything to get your modem switching manually; just run 'usb_modeswitch' at the prompt.

> New in 1.0.6:
[LIST]
[*]new "GCTMode" to switch the Sagem F@ST
[*]loads of new devices (contains all Option models now)
[*]fixed problem with multiple Huawei devices
[*]workaround for quirky "Dragonfly" devices
[/LIST]
 **Note**: the all-in-one config file **usb_modeswitch.conf** will shift its meaning to become a kind of reference. 
The preferred way for configuration is the **integrated** installation. For known devices there should be no further editing necessary. 

---

### Post by pythonsyntax on 2009-12-23
How do i install it?

---

### Post by pdc on 2009-12-23
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by pythonsyntax on 2009-12-24
that  don't help me out.

---

