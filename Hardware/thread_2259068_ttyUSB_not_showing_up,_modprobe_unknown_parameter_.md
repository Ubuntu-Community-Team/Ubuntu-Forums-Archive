---
title: "ttyUSB not showing up, modprobe unknown parameter 'vendor' &amp; 'product'"
date: 2015-01-01
forum: Hardware
---

### Post by matej6 on 2015-01-01
Hello,

I have tried this on Ubuntu 12.04.5 and 14.04

I have one evice that I connect with usb adapter. The instruction states that I should do this:

```
rmmod ftdi_sio
modprobe ftdi_sio vendor=0x0403 product=0xf248
```

this should create ttyUSB0, but there is no ttyUSB0 in /dev/

this is step by step for 14.04
so step by step:

1. connect usb
dmesg:
```

[  273.398522] usb 2-2.2: new full-speed USB device number 5 using uhci_hcd
[  273.582354] usb 2-2.2: New USB device found, idVendor=0403, idProduct=f248
[  273.582360] usb 2-2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  273.582364] usb 2-2.2: Product: DA2 Adapter Kit
[  273.582366] usb 2-2.2: Manufacturer: ITL
[  273.582368] usb 2-2.2: SerialNumber: FT5UN01W

```
lsusb:
```
Bus 002 Device 005: ID 0403:f248 Future Technology Devices International, Ltd 

```

2. after I try to remove ftdi_sio
[CODE
Bus 002 Device 005: ID 0403:f248 Future Technology Devices International, Ltd 
][/CODE]

3. when I try to modprobe it I get no error, but there is no ttyUSB in dev
dmesg:
```
[  952.847812] usbcore: registered new interface driver usbserial
[  952.847848] usbcore: registered new interface driver usbserial_generic
[  952.847863] usbserial: USB Serial support registered for generic
[  952.888754] ftdi_sio: unknown parameter 'vendor' ignored
[  952.888762] ftdi_sio: unknown parameter 'product' ignored
[  952.889247] usbcore: registered new interface driver ftdi_sio
[  952.889265] usbserial: USB Serial support registered for FTDI USB Serial Device

```

help please :)

---

### Post by matej6 on 2015-01-01
EDIT: here is something that I fond, but this solution didnt work.

 						From kernel 3.12, the ftdi-sio module no longer accepts the "vendor" and "product" parameters ([commit link]("https://github.com/torvalds/linux/commit/e17c1aa2e1")).  I think it was assumed that this was a debugging feature that should  not be used by end users, and so the change was not at all publicised.
The  new way to add a new VID/PID pair for the ftdi-sio driver is to write  them both, one after the other, to  /sys/bus/usb-serial/drivers/ftdi_sio/new_id:
# modprobe ftdi-sio
# echo 0403 f248 > /sys/bus/usb-serial/drivers/ftdi_sio/new_id
 						EDIT2: I also updated the repo to include lateset repo, and I deleted usb-serial and install the latest

---

### Post by matej6 on 2015-01-01
Ok it worked after all. What I had to do is:

```

sudo chmod 666 /sys/bus/usb-serial/drivers/ftdi_sio/new_id
nano /sys/bus/usb-serial/drivers/ftdi_sio/new_id

```

type my vendor and product id and save file with CTRL+x > yes
```

0304 f248

```

plug and unplug device

---

