---
title: "Wifi USB adapter and USB camera interfering"
date: 2013-09-29
forum: Hardware
---

### Post by subhendu2 on 2013-09-29
I have Ubuntu 12.04 with the latest kernel . in my desktop
In my USB drive , I have 4 USB attached , webcam , mouse, usb wifi adapter and a micro controller - arduino.
```
 lsusb
```
Bus 001 Device 004: ID 18ec:3399 Arkmicro Technologies Inc. 
Bus 001 Device 016: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 002 Device 004: ID 2341:0001  
Bus 002 Device 003: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

My netgear USB Wifi is working fine after some tweaks

But suprisingly the moment  i start my VLC player with the following
```
  vlc v4l2:///dev/video0
```

the wifi stops. The blue light is off. And the wifi gets dissaperard from the network menu. 
Although ```
lsusb
``` shows the presence of netgear. 

The same thing is hapening if i start the webcam with opencv program .

cheese fails to start with the following error
```
 cheese
(cheese:6633): Gdk-WARNING **: The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadContext'.
  (Details: serial 153 error_code 169 request_code 153 minor_code 6)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
``` 

I am at a loss. please help

---

### Post by subhendu2 on 2013-09-30
Help required

---

### Post by varunendra on 2013-09-30
> **subhendu2 said:**
> Bus **[COLOR="#FF0000"]001[/COLOR]** Device 004: ID 18ec:3399 Arkmicro Technologies Inc. 
Bus **[COLOR="#FF0000"]001[/COLOR]** Device 016: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 002 Device 004: ID 2341:0001  
Bus 002 Device 003: ID 046d:c05a Logitech, Inc. Optical Mouse M90
**Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
From your above output it seems you are sharing the same hub between your webcam and wifi dongle.

It is a known fact that not only the speed is shared, but polling interval is also directly proportional to the number of devices attached to the same hub. Try connecting one of the webcam or WiFi adapter to another port, although I doubt if any of them can work properly at USB 1.1 speeds.

As you can see yourself in the output of lsusb, you have only one USB2.0 hub (480 Mb/s or 60 MB/s speed) and rest 3 are USB 1.1 hubs (12 Mb/s or 1.5 MB/s). These speeds are theoretical and practically, it gets even lesser due to protocol overheads. ([more info]("http://en.wikipedia.org/wiki/Host_controller_interface_(USB,_Firewire)#Universal_Host_Controller_Interface"))

If all the ports on your computer are rated as USB2.0, then they are clearly sharing the same hub, thus affecting the performance of each other. Those devices which can work on low speed and high polling interval would keep working, but devices like a high speed Wifi adapter won't.

In such motherboards, the USB1.1 hubs appear just because they are part of the [south-bridge]("http://en.wikipedia.org/wiki/Southbridge_(computing)#Overview") chip (mostly Intel or VIA).

The picture will become more clearer if you also post the output of -
```
usb-devices
```
..while all the devices are connected.

Oh, and please the code box not only for commands, but for their outputs too. Anything that is code, not a sentence of conversation or speech, should be in the code box :P

---

### Post by subhendu2 on 2013-09-30
What is the solution ? 
Will a PCI to USB card solve the problem ? Or will I connect it to front panel usb ?
This is a old motherboard + processor (celeron 2.4 GHZ) i am planning to make a small robot

---

### Post by gordintoronto on 2013-10-01
If you unplug the Wi-Fi adapter, does Cheese work?

---

### Post by subhendu2 on 2013-10-01
No cheese do not work even then.

But VLC is working even with wifi adapter plugged in. But Wifi is getting disabled

---

### Post by varunendra on 2013-10-02
> **subhendu2 said:**
> What is the solution ? 
Will a PCI to USB card solve the problem ? Or will I connect it to front panel usb ?

A PCI card should solve the wifi interference problem, but of course I can't guarantee, as it maybe more than speed sharing.

I don't think the front USB will make any difference. Because unless the motherboard belongs to the days when USB2 was a new thing, I don't think any of the USB1.1 hubs would be in use at all. Like I said earlier, they appear in lsusb just because they are part of the SouthBridge chip. Chance are - all your USB ports (internal and external) are sharing the same USB2 HUB.

You can check this yourself by connecting any of the devices to different ports, then look at the output of -
```
lsusb -t
```
If at any port the devices seems to be connected to a hub using the "uhci" driver, it means your USB1.1 hub(s) is/are in use, otherwise all ports are sharing the same USB2 hub and you should definitely try your luck with the PCI-USB card

---

### Post by RT236 on 2014-05-31
> **varunendra said:**
> From your above output it seems you are sharing the same hub between your webcam and wifi dongle.

It is a known fact that not only the speed is shared, but polling interval is also directly proportional to the number of devices attached to the same hub. Try connecting one of the webcam or WiFi adapter to another port, although I doubt if any of them can work properly at USB 1.1 speeds.

As you can see yourself in the output of lsusb, you have only one USB2.0 hub (480 Mb/s or 60 MB/s speed) and rest 3 are USB 1.1 hubs (12 Mb/s or 1.5 MB/s). These speeds are theoretical and practically, it gets even lesser due to protocol overheads. ([more info]("http://en.wikipedia.org/wiki/Host_controller_interface_(USB,_Firewire)#Universal_Host_Controller_Interface"))

If all the ports on your computer are rated as USB2.0, then they are clearly sharing the same hub, thus affecting the performance of each other. Those devices which can work on low speed and high polling interval would keep working, but devices like a high speed Wifi adapter won't.

In such motherboards, the USB1.1 hubs appear just because they are part of the [south-bridge]("http://en.wikipedia.org/wiki/Southbridge_(computing)#Overview") chip (mostly Intel or VIA).

The picture will become more clearer if you also post the output of -
```
usb-devices
```
..while all the devices are connected.

Oh, and please the code box not only for commands, but for their outputs too. Anything that is code, not a sentence of conversation or speech, should be in the code box :P

Thank you for having posted this! I was having exactly this problem! My camera suddenly developed conflicts with my USB wifi adapter ... and after having read what you posted I realized I had recently plugged the camera into one of the 2 USB ports on the front of my tower. I have 8 ports on the back of the tower. After I moved around the camera trying a couple of other USB ports the conflict with USB wifi cleared. Thanks! I was chasing around on this one!

---

### Post by varunendra on 2014-05-31
> **RT236 said:**
> Thanks! I was chasing around on this one!

You're welcome! Glad it could be helpful even after so many days.. :)

---

