---
title: "FTDI serial converter does not work the first time"
date: 2011-09-28
forum: Hardware
---

### Post by estratos on 2011-09-28
On Ubuntu 10.04 LTS 32-bits

I have a FTDI-based USB/serial adapter that I want to use from Python code. The first time I plug the interface the following dmesg mesages are displayed:

```

[  943.808036] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  944.010209] usb 3-1: configuration #1 chosen from 1 choice
[  944.172154] usbcore: registered new interface driver usbserial
[  944.173108] USB Serial support registered for generic
[  944.174184] usbcore: registered new interface driver usbserial_generic
[  944.174189] usbserial: USB Serial Driver core
[  944.187019] USB Serial support registered for FTDI USB Serial Device
[  944.188272] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[  944.188570] usb 3-1: Detected FT232RL
[  944.188574] usb 3-1: Number of endpoints 2
[  944.188577] usb 3-1: Endpoint 1 MaxPacketSize 64
[  944.188580] usb 3-1: Endpoint 2 MaxPacketSize 64
[  944.188582] usb 3-1: Setting MaxPacketSize 64
[  944.190218] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0
[  944.190244] usbcore: registered new interface driver ftdi_sio
[  944.190247] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver

```

Indeed, /dev/ttyUSB0 is listed but then my program is unable to open the port.

Then, if I unplug and then plug the interface again, the following dmesg output appears:

```

[ 1001.864022] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 1002.062207] usb 3-1: configuration #1 chosen from 1 choice
[ 1002.070155] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[ 1002.070193] usb 3-1: Detected FT232RL
[ 1002.070197] usb 3-1: Number of endpoints 2
[ 1002.070200] usb 3-1: Endpoint 1 MaxPacketSize 64
[ 1002.070202] usb 3-1: Endpoint 2 MaxPacketSize 64
[ 1002.070204] usb 3-1: Setting MaxPacketSize 64
[ 1002.071171] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0

```

It's very similar to the above except for the registration of the usbserial_generic and dtdi_sio drivers. However, this time my program is able to open the port and communicate without problems.

I've tested this from other custom programs written in Java and also from the Arduino IDE. In all cases this problem appears. The first time I plug the serial converter it never works. then it works smoothly.

Has anyone seen this problem before? Is there any way to solve this issue? Otherwise, how could I simulate an unplug-replug when I plug the converter?

Thanks in advance,

Daniel.

---

### Post by estratos on 2011-09-29
Just a little update, the error code raised when trying to open de serial port is:

```

could not open port /dev/ttyUSB0: [Errno 16] Device or resource busy: '/dev/ttyUSB0'

```

It seems like some process is before the serial port before I do. I've verified that britty is not installed.

---

### Post by estratos on 2011-09-29
Still a new update:

Running my application as superuser solves the problem! However, I still want to open the serial port as normal user...

Thanks.

---

### Post by pjd99 on 2011-09-29
Not an answer, my dmesg when I plug in my ftdi for reference:
```

[18828.010124] usb 3-1: new full speed USB device using uhci_hcd and address 2
[18828.247546] usbcore: registered new interface driver usbserial
[18828.247573] USB Serial support registered for generic
[18828.312259] usbcore: registered new interface driver usbserial_generic
[18828.312268] usbserial: USB Serial Driver core
[18828.319480] USB Serial support registered for FTDI USB Serial Device
[18828.320880] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[18828.321063] usb 3-1: Detected FT232RL
[18828.321070] usb 3-1: Number of endpoints 2
[18828.321076] usb 3-1: Endpoint 1 MaxPacketSize 64
[18828.321081] usb 3-1: Endpoint 2 MaxPacketSize 64
[18828.321086] usb 3-1: Setting MaxPacketSize 64
[18828.324260] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0
[18828.324338] usbcore: registered new interface driver ftdi_sio
[18828.324344] ftdi_sio: v1.6.0:USB FTDI Serial Converters Driver

```That's on the first time being plugged in, and Arduino IDE has no problems accessing the port. I notice that my driver version is 1.6, and yours is 1.5. I'm wondering if it's a bug in the driver... Probably not too useful as I'm running 11.04 64-bit, guessing you cant get the later driver for your LTS version.
I just tried to find the source for the 1.6 driver - the ftdi site has 1.5 as the latest. Also, people are reporting problems with 1.6 (not being able to flash using Arduino IDE being one of them). Another reported the 1.4.3 was the last working version. 
I'll stop here, because I don't know too much about using serial on Linux, I just pass the USB to my VM's when I need to connect to legacy PLC's and HMI's.

dmesg output for the second time plugging in
```

[19368.040168] usb 3-1: USB disconnect, address 2
[19368.040519] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[19368.040554] ftdi_sio 3-1:1.0: device disconnected
[19370.980104] usb 3-1: new full speed USB device using uhci_hcd and address 3
[19371.182169] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[19371.182249] usb 3-1: Detected FT232RL
[19371.182255] usb 3-1: Number of endpoints 2
[19371.182261] usb 3-1: Endpoint 1 MaxPacketSize 64
[19371.182266] usb 3-1: Endpoint 2 MaxPacketSize 64
[19371.182271] usb 3-1: Setting MaxPacketSize 64
[19371.184201] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0

```

---

### Post by estratos on 2011-09-30
Thanks pjd,

Yes, maybe this problem has to do with the driver. I've too read lots of posts complaining about different problems with USB/serial converter IC's (FTDI and Prolific most of the times).

---

