---
title: "kernel crashes with Bluetooth connecting to a bluetooth loudspeaker"
date: 2013-05-12
forum: Hardware
---

### Post by sanderj on 2013-05-12
Hi,

I keep getting kernel crashes when activating Bluetooth with a bluetooth headset / loudspeaker. The crashes occur about 2 second after I switch the connection to the device to On (with the bluetooth app in the upper right corner of Ubuntu)

After a crash, the system is very locked up, and even the 8-second-power-button-press does not work; I have to remove power supply & battery to restart.

Bluetooth dongle lsusb id:

```
Bus 002 Device 003: ID 0c10:0000
```

The loudspeaker device

```
sander@flappie:~$ hcitool scan 
Scanning ...
	00:1D:DF:30:26:C0
```	


System is Ubuntu 13.04, fully updated.

Tips how to proceed?

[IMG]http://uppy.co/i/iL5hLnxirv.jpg[/IMG]

---

### Post by mrskytown11 on 2013-09-14
I have the same issue with my Bluetooth adapter. it always crashes. i got mine from china but supports windows 7 and stuff. so its pretty decent. it works well on my windows 8 machine but on linux it ALWAYS, crashes :(

---

