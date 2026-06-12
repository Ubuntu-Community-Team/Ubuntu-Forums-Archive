---
title: "USB serial port (FTDI chip) hangs after a short burst of transmitting or receiving"
date: 2011-06-07
forum: Hardware
---

### Post by piggoy on 2011-06-07
Hi,

I am trying to use a USB serial port to communicate with my car's diagnostic connector. I know this is purely an issue of the USB seriel interface (/dev/ttyUSB0) since I have no problems with using the built in serial port (/dev/ttyS0) for the task. My USB serial adaptor is based on the FTDI chip (FT232)
```

samwise@Triton:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 002 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 002: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The problem is that the port hangs and does not respond after a short burst of sending or transmitting data. This is manifested in my application as the program kicking back an error after a few seconds of data transmit/recieve by saying the port does not exist or is not responding. The only way to make the port work again is to open gtkterm and initialise the port with fresh configuration parameters (baud rate etc). Rebooting the computer also works.

Here is dmesg on plugging in the USB-serial adaptor
```

samwise@Triton:~$ dmesg
-----------------------------------
[31388.360021] usb 2-6: new high speed USB device using ehci_hcd and address 4
[31388.510612] hub 2-6:1.0: USB hub found
[31388.510683] hub 2-6:1.0: 4 ports detected
[31744.140091] usb 2-6.4: new full speed USB device using ehci_hcd and address 5
[31744.323838] usbcore: registered new interface driver usbserial
[31744.323859] USB Serial support registered for generic
[31744.323898] usbcore: registered new interface driver usbserial_generic
[31744.323900] usbserial: USB Serial Driver core
[31744.336753] USB Serial support registered for FTDI USB Serial Device
[31744.337022] ftdi_sio 2-6.4:1.0: FTDI USB Serial Device converter detected
[31744.337081] usb 2-6.4: Detected FT232RL
[31744.337083] usb 2-6.4: Number of endpoints 2
[31744.337085] usb 2-6.4: Endpoint 1 MaxPacketSize 64
[31744.337087] usb 2-6.4: Endpoint 2 MaxPacketSize 64
[31744.337089] usb 2-6.4: Setting MaxPacketSize 64
[31744.337439] usb 2-6.4: FTDI USB Serial Device converter now attached to ttyUSB0
[31744.337472] usbcore: registered new interface driver ftdi_sio
[31744.337475] ftdi_sio: v1.6.0:USB FTDI Serial Converters Driver
```

Here is stty just after plugging in the adaptor
```

samwise@Triton:~$ stty -F /dev/ttyUSB0
speed 115200 baud; line = 0;
eof = ^A; min = 1; time = 0;
-brkint -icrnl -imaxbel
-opost -onlcr
-isig -icanon -iexten -echo -echoe -echok -echoctl -echoke

```

And here is stty while the port is hanging
```

samwise@Triton:~$ stty -F /dev/ttyUSB0
speed 0 baud; line = 0;
eof = ^A; min = 0; time = 0;
ignbrk -brkint -icrnl -imaxbel
-opost -onlcr
-isig -icanon -iexten -echo -echoe -echok noflsh -echoctl -echoke

```
You will notice that the baud rate reads 0 - very confusing. By providing the port a fresh baud rate using gtkterm the port is able to work again.

Does anyone know what the issue here may be? This is really annoying and if anyone has any ideas it would be much appreciated. Thanks in advance :)

Regards,
Sam

---

### Post by piggoy on 2011-06-08
bump ;)

---

