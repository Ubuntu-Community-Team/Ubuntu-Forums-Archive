---
title: "Usb FTDI remote controller not working"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by olpe on 2007-06-07
Hi!

I am now getting really tired of trying to get this thing to work. I've tried almost every way to get this multimedia remote controller to work. 

My problem is that when I plug the ir receiver to usb my dmesg looks like this:
```
[ 3089.992000] usb 3-1: new full speed USB device using uhci_hcd and address 7
[ 3090.196000] usb 3-1: configuration #1 chosen from 1 choice
[ 3090.200000] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[ 3090.200000] drivers/usb/serial/ftdi_sio.c: Detected FT232BM
[ 3090.200000] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0
[ 3094.428000] usb 3-1: usbfs: interface 0 claimed by ftdi_sio while 'brltty' sets config #1
[ 3094.432000] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 3094.432000] ftdi_sio 3-1:1.0: device disconnected

```

and my lsusb -v shows: 

```
  iManufacturer           1 FTDI
  iProduct                2 FT232R USB UART
  iSerial                 3 A5001v5M
---

      iInterface              2 FT232R USB UART


```

What do I have to do to make this work? I am hopeless.

---

### Post by olpe on 2007-06-07
Actually I got it fixed by removing brltty from the system. Now the problem is how to configure lirc to use this /dev/ttyUSB0 device ... any help ;) ?

---

