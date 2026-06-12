---
title: "USB-RS232 adapter doesn't work!"
date: 2016-06-15
forum: Hardware
---

### Post by antares5 on 2016-06-15
Dear all,  
 
I would like to connect my telescope (Celestron Nexstar 5) and my Lubuntu computer using an USB-serial adapter (USB-RS232 adapter) in order to control the telescope with the astronomy software Stellarium. According to the descriptions at the corresponding websides (e.g.: [http://www.stellarium.org/wiki/index.php/Telescope_Control](http://www.stellarium.org/wiki/index.php/Telescope_Control)) that shouldn't be a problem. Unfortunately I couldn't manage it so far...:(
 After connecting the USB-serial adapter with the computer the device will be identified properly and the lubuntu driver is activated without any problem:
  
 *dmesg* output:
 ```
[ 3143.604052] usb 7-1: new full-speed USB
device number 2 using uhci_hcd [ 3143.973130] usb 7-1: New USB device found,
idVendor=1a86, idProduct=7523 [ 3143.973141] usb 7-1: New USB device strings:
Mfr=0, Product=2, SerialNumber=0 [ 3143.973148] usb 7-1: Product: USB2.0-Ser! [ 3144.077782] usbcore: registered new interface
driver usbserial 
[ 3144.077798] usbcore: registered new interface
driver usbserial_generic 
[ 3144.077810] usbserial: USB Serial support
registered for generic 
[ 3144.085995] usbcore: registered new interface
driver ch341 
[ 3144.086014] usbserial: USB Serial support
registered for ch341-uart 
[ 3144.086038] ch341 7-1:1.0: ch341-uart
converter detected 
[ 3144.098217] usb
7-1: ch341-uart converter now attached to ttyUSB0

``` *lsusb* output:
 ```
Bus 002 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub 
Bus 008 Device 002: ID 0a5c:2101 Broadcom Corp.
BCM2045 Bluetooth 
Bus 008 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub 
Bus 007 Device 002:
ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter 

```

It seems that everthing is fine. When I start Stellarium and activate the telescope control plug-in the telescope is even indicated as „connected“. But if I select an object and instruct the telescope to move nothing happens.
 In order to exclude possible errors with the cable connection and with the telescope control itself I tried the same under Windows and it worked directly. That means it has to be a problem with the Lubuntu settings.
 
 Some further details:
 ```
antares@antares-R510-P510:~$ uname -r 3.19.0-37-generic 

antares@antares-R510-P510:~$ id uid=1000(antares) gid=1000(antares)
Gruppen=1000(antares),4(adm),20(dialout),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),118(sambashare) 

antares@antares-R510-P510:~$ sudo udevadm
monitor monitor will print the received events for: UDEV - the event which udev sends out after rule
processing KERNEL - the kernel uevent 

KERNEL[1082.450488] add     
/devices/pci0000:00/0000:00:1d.1/usb7/7-1 (usb) KERNEL[1082.452486] add     
/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0 (usb) KERNEL[1082.452547] add     
/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/ttyUSB0
(usb-serial) KERNEL[1082.465170] add     
/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/ttyUSB0/tty/ttyUSB0
(tty) UDEV  [1082.474034] add     
/devices/pci0000:00/0000:00:1d.1/usb7/7-1 (usb) UDEV  [1082.476953] add     
/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0 (usb) UDEV  [1082.477965] add     
/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/ttyUSB0
(usb-serial) UDEV  [1082.483420] add     
/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/ttyUSB0/tty/ttyUSB0
(tty) 

^Cantares@antares-R510-P510:~$ ls -al /dev |
grep ttyUSB crw-rw----   1 root
dialout 188,   0 Jun 13 17:36 ttyUSB0 
```

Now I don't have any idea how to solve that problem and even on the internet I couldn't find a solution. 
Is someone out there who can help me?
 Thank you in advance!

---

### Post by antares5 on 2016-06-17
Short update:
In the meantime I tried to get it work with three different computers (running with Lubuntu) but it doesn't work. Furthermore I tried it with the Raspberry Pi 2 as well but without any success.

Is there anyone who has an idea to solve that issue?

Best regards,
Antares

---

### Post by robertoque on 2016-07-15
Did you find the solution? I have a similar use for self-guided lin_guider (libnexstar library) problem through a similar adapter.

---

### Post by giga+bytes on 2016-07-17
I asked about these adapters in a popular astronomy forum, and was told telescopes are picky about what adapter is used, especially with cheaper and off-brands. The top recommendation is the Tripp Lite model USA-19HS. I've had no trouble at all using this Tripp Lite with my iOptron ZEQ25 and Windows 8.1 computer, but have yet to try it with an Ubuntu computer (I don't dual-boot).

---

### Post by gordintoronto on 2016-07-17
Have a look at this:
[https://forums.linuxmint.com/viewtopic.php?t=135914](https://forums.linuxmint.com/viewtopic.php?t=135914)

---

### Post by him610 on 2016-07-18
Other USB-Serial adapters are made/sold by Belkin and Prolific. They are relatively inexpensive. We had both makes where I used to work. I always had more success with the Prolific make while some of my workmates had success with the Belkin. 

One more thing, make sure you use a USB2 port.

---

