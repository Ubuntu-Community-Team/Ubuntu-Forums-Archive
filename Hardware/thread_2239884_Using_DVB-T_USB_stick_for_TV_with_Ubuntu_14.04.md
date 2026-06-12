---
title: "Using DVB-T USB stick for TV with Ubuntu 14.04"
date: 2014-08-16
forum: Hardware
---

### Post by andrewknight on 2014-08-16
I am trying to get a KWorld DVB-T USB stick TV to work with Ubuntu 14.04 on an HP dv1588 laptop, but the stick is not recognised.

Details:  HP Pavilion dv1588EA laptop (old), Ubuntu 14.04 up to date.
I am fairly new to Ubuntu, but have tried to diagnose the problem.
Using terminal codes I only partly understand, it is clear the device (which works on Windows XP with proprietary, supplied, software) is noticed:

   andrew@andrew-HP-Pavilion-dv1000-EK908EA-ABU:~$ lsusb
 Bus 001 Device 003: ID 1b80:e39b Afatech DVB-T395U [af9015]

is it just that a firmware file is missing, as seems to be implied by:

 using sudo dmesg, part response is:
 [ 1022.960205] usb 1-2: new high-speed USB device number 2 using ehci-pci
 [ 1023.095883] usb 1-2: New USB device found, idVendor=1b80, idProduct=e39b
 [ 1023.095896] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
 [ 1023.095903] usb 1-2: Product: DVB-T 2
 [ 1023.095910] usb 1-2: Manufacturer: Afatech
 [ 1023.712497] usb 1-2: dvb_usb_v2: found a 'KWorld USB DVB-T TV Stick II (VS-DVB-T 395U)' in cold state
 [ 1023.712563] usb 1-2: Direct firmware load failed with error -2
 [ 1023.712567] usb 1-2: Falling back to user helper
 [ 1023.719139] usb 1-2: dvb_usb_v2: Did not find the firmware file 'dvb-usb-af9015.fw'. Please see linux/Documentation/dvb/ for more details on firmware-problems. Status -2

 [ 1023.719159] dvb_usb_af9015: probe of 1-2:1.0 failed with error -2
 [ 1023.719197] usbcore: registered new interface driver dvb_usb_af9015
 [ 1116.762621] usb 1-2: USB disconnect, device number 2
 [ 1189.896200] usb 1-3: new high-speed USB device number 3 using ehci-pci
 [ 1190.031900] usb 1-3: New USB device found, idVendor=1b80, idProduct=e39b
 [ 1190.031911] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0

 [ 1190.031919] usb 1-3: Product: DVB-T 2
 [ 1190.031926] usb 1-3: Manufacturer: Afatech
 [ 1190.035024] usb 1-3: dvb_usb_v2: found a 'KWorld USB DVB-T TV Stick II (VS-DVB-T 395U)' in cold state
 [ 1190.035062] usb 1-3: Direct firmware load failed with error -2
 [ 1190.035069] usb 1-3: Falling back to user helper
 [ 1190.037513] usb 1-3: dvb_usb_v2: Did not find the firmware file 'dvb-usb-af9015.fw'. Please see linux/Documentation/dvb/ for more details on firmware-problems. Status -2
 [ 1190.037533] dvb_usb_af9015: probe of 1-3:1.0 failed with error -2

if so, where can I find the firmware file 'dvb-usb-af9015.fw', and where do I put it when I have it?
Any help appreciated

---

### Post by grahammechanical on 2014-08-16
DVT and similar devices are a special case in Linux. See, if you device has a driver and how to install it.

[http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)

[http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices](http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices)

Regards.

---

### Post by tea for one on 2014-08-16
> **andrewknight said:**
> 

if so, where can I find the firmware file 'dvb-usb-af9015.fw', and where do I put it when I have it?
Any help appreciated

You can find the driver here:-

[http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.65.0/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.65.0/)

You have to place it in /lib/firmware with sudo

I hope that works for you

---

