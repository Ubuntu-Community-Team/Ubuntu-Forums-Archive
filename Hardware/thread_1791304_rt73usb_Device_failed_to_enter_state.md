---
title: "rt73usb Device failed to enter state"
date: 2011-06-26
forum: Hardware
---

### Post by brown12 on 2011-06-26
I've had some problems since upgrading to Natty with standby/resume, that did not occur in previous releases.

Often at the time of resume, the screen will post an error:

```
Problem with device rt73usb: Device failed to enter state 1 (-16).
```


I'm running a dual-boot Ubuntu 11 x64, Windows Vista machine.

Near as I can tell, the rt73usb driver is for a Gemtek wireless networking card. Gemtek does not appear on the list of compatible 802.11 cards, but I have had no difficulty connecting to wireless networks using the rt73usb driver. The problem has been resuming from standby.

Problems resuming from standby also affect other USB devices: for example, it is necessary to disconnect and reconnect USB keyboards, webcam, and backup drives after rebooting. (This is also new since upgrade to Natty. Whatever the developers did to Natty support for USB and for NTFS drives, it has knocked my system on its butt.)

It appears from several postings that rt73usb may be obsolete, and that I should update to a rt2xxx driver. Could anyone point me to a current how-to?

I've also downloaded a 2011 Ralink rt73 driver from the Linux support page--not sure whether & how to compile or install that.

What's the best way to get rid of the "device failed to enter state" message? and if I do that, will other USB peripherals likely work better on reboot?

Thanks-

---

### Post by rarsa on 2011-08-02
Open a terminal and type 

```
sudo iwconfig wlan0 power off
```

The Wireless performance will improve and the error will stop.

---

