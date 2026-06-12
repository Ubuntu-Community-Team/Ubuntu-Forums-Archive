---
title: "usb to serial converter"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by snowsquirrel on 2007-01-23
I am contemplating installing xubuntu on my laptop.  I am just trying to forsee headaches... already I know that my broadcom wifi will be an issue, though I have already found posts talking about the fix for that...

My laptop has not serial port, only USB.  So I have a USB to serial converter which I use to connect to the tty on my Sun Ultra 10.  Does anyone know how well a usb2serial device would work in linux?  I am not even sure what program I would use to connect to the Sun.  In windows I used HyperTerm, or TeraTerm.  In Solaris I used a program called tip (does linux have tip?).

And no, ssh/telnet are not always options, because if I need to do anything in single user mode, or reinstall the OS, I need to communicate with the Ultra 10.  ( I am not even sure I still have a keyboard for it).

Anyone used a usb2serial device under linux?

~S

---

### Post by ihristov on 2007-01-24
USB to serial converters are widely used and in general very well supported.
I have used without any problems several different models.

[LIST]
[*]A Deluo USB adapter - uses prolific chipset - uses pl2303 kernel module
[*]One that uses an FTDI chipset - don't remember where I got it - uses ftdi_sio module
[*]One obsure one I purchased somewhere on the net had a ark3116 chipset and had to compile the kernel module from source for Ubunutu 6.06.1. Not difficult at all. Acording to their web site their module is included in the official kernel tree from version 2.6.17
[/LIST]

Both the prolific and FTDI use the usbserial module and both are recognized automatically with every version of Linux I have used (not only Ubuntu) from quite some time back.

As far as a terminal application there are plenty of these of course. I have used minicom.
```

$ sudo apt-get install minicom

```

---

### Post by danbyte on 2007-02-20
have a look at the keyspan products. I use minicom with keyspan USA-19HS to connect to a number of HP servers without any problems.

---

### Post by PokerFacePenguin on 2008-06-07
ihristov,

  Are you using a deluo usb universal model?  I am having trouble with my new deluo.  Any pointers would be appreciated. 
Thanks

---

### Post by ihristov on 2008-06-09
> **PokerFacePenguin said:**
> ihristov,

  Are you using a deluo usb universal model?  I am having trouble with my new deluo.  Any pointers would be appreciated. 
Thanks

They might have changed the chipset they use. Mine is 3-4 years old. You probably want to check which chipset yours has and then search for that, not Deluo in general.

You can dig for it in System/Preferences/Hardware Information. I prefer to use the shell
```
$ lsusb
Bus 002 Device 002: ID 2222:3040 MacAlly 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000 
``` 

Then plug the adapter
```
$ lsusb
Bus 002 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 002: ID 2222:3040 MacAlly 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000 
```

As you can see a new device showed up. In this case the PL2303, which is the Prolific chipset I was referring to previously

You can also get more details by running
```
$ sudo lsusb -v
Bus 002 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2303 PL2303 Serial Port
  bcdDevice            2.02
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
...
```

---

### Post by cszikszoy on 2008-06-09
If you want advice on which USB -> RS232 cable to use, DON'T use one of the cheap-o $5 on ebay.  Get yourself one of the ones with a well known chip.  I have had much success with the cables with the FTDI chip.

I can't quite remember which one I bought, exactly, but here's a similar one:
[http://compusb.stores.yahoo.net/6fusb20rsusb.html](http://compusb.stores.yahoo.net/6fusb20rsusb.html)

I used to have a chinese knock-off from Ebay, and could never get it to work.

Also - if you're looking for something like a hyperterminal equivalent, look into GKterm.

---

