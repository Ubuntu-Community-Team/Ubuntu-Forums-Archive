---
title: "Nuforce uDAC5 driver"
date: 2021-07-11
forum: Hardware
---

### Post by lemoniron on 2021-07-11
Helppppp me pleaseee
Does anyone have driver for Nuforce uDAC5
I tried to search on GG but no result
The download link on theie website has been died due to the nuforce company has been bought by Optoma

---

### Post by coffeecat on 2021-07-11
*Thread moved to **Hardware** sub-forum.*

Welcome to the forum.

Why do you think you need a driver? Perhaps if you tell us which version and flavour of Ubuntu you are using, details of your computer hardware, how you are connecting the DAC to the computer, and what problems you are experiencing, forum members may be able to help.

---

### Post by cryptearth on 2021-07-11
Looks like a simple usb-dac to me - it shouldn't require any additional driver using any Linux distro.
Have a look if it shows up using
```
lsusb
```
Here's an example from my system using a Roland Tri-Capture:
```
main@main:~$ lsusbBus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 1b1c:0c08 Corsair H80i v2
Bus 005 Device 003: ID 0582:0132 Roland Corp. TRI-CAPTURE
Bus 005 Device 002: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 1ea7:1006 SHARKOON Technologies GmbH Gaming Mouse
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by lemoniron on 2021-07-12
> **coffeecat said:**
> *Thread moved to **Hardware** sub-forum.*

Welcome to the forum.

Why do you think you need a driver? Perhaps if you tell us which version and flavour of Ubuntu you are using, details of your computer hardware, how you are connecting the DAC to the computer, and what problems you are experiencing, forum members may be able to help.
Thanks for your reply
[COLOR=#050505][FONT=&quot]Without driver I cant run aiso in foobar2000 & cant decode dsd. Just abke to decode [/FONT][/COLOR][COLOR=#050505][FONT=&quot]384kbps
[/FONT][/COLOR][COLOR=#050505][FONT=&quot]I can use it without driver but I cant use full function


[/FONT][/COLOR]

---

### Post by lemoniron on 2021-07-12
> **cryptearth said:**
> Looks like a simple usb-dac to me - it shouldn't require any additional driver using any Linux distro.
Have a look if it shows up using
```
lsusb
```
Here's an example from my system using a Roland Tri-Capture:
```
main@main:~$ lsusbBus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 1b1c:0c08 Corsair H80i v2
Bus 005 Device 003: ID 0582:0132 Roland Corp. TRI-CAPTURE
Bus 005 Device 002: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 1ea7:1006 SHARKOON Technologies GmbH Gaming Mouse
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
I am noob, Idk what these codes mean T__T

---

### Post by cryptearth on 2021-07-12
Ah, so it's not like you can't use it at all but rather you can't use it's extended features.
Well, from what I was able to gather it seems you're out of luck on a Linux system, as the driver's only for windows and mac seem to fully support it out of the box. It's unlikely you'll find a linux driver to enjoy the full feature set of this device.

---

### Post by lemoniron on 2021-07-13
Poor me :(
anyway, thanks for your reply

---

