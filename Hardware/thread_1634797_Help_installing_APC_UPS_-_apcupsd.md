---
title: "Help installing APC UPS - apcupsd"
date: 2010-12-01
forum: Hardware
---

### Post by horseatingweeds on 2010-12-01
I'm confused and not sure where to go with this. I'm new to Ubuntu. So far everything has been simple and straight forward, until trying to install my UPS (APC ES 550) It came with a USB cord, with an Ethernet connection on one end.

Here's what I've done, following this guide: [https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)

Used Synaptic to load apcupsd.

Configured apcupsd.conf by making the following changes:
UPSNAME UPSsys
UPSCABLE usb
UPSTYPE ups
#DEVICE

In /etc/default/apcupsd I set ISCONFIGURED=yes

When I run** sudo apcaccess** I get this error: Error contacting apcupsd @ localhost:3551: Connection refused

Rebooted, error remains. Does this mean I need to open a port?

Under System>Preferences>Power Management I do have On UPS Power settings - but I'm not sure if they were there to begin with or not. 

There are no apcups files in /var/log

I ran ls **-l /sys/bus/usb/drivers** and got this:
```
drwxr-xr-x 2 root root 0 2010-12-01 01:03 hiddev
drwxr-xr-x 2 root root 0 2010-12-01 00:32 hub
drwxr-xr-x 2 root root 0 2010-12-01 00:32 usb
drwxr-xr-x 2 root root 0 2010-12-01 01:03 usbfs
drwxr-xr-x 2 root root 0 2010-12-01 00:32 usbhid
```I also stuck a USB drive into a port just to see what the USB ports are doing. It came to life after about 2 seconds and popped up on Nautilus. 

I've read through the apcupsd manual - [http://www.apcupsd.com/manual/manual.html](http://www.apcupsd.com/manual/manual.html)  But to be honest, it left me a little more confused than before reading it. 

Like I said, I'm just starting to understand operating systems, I'm eager to learn, but in this case I'm not sure what to do or where to look. Any advice would be appreciated.

**Edit:** I found /var/log/messages I unplugged the USB and plugged it back in to get a fresh log for the USB port:
```
Dec  1 02:02:09 ubu-compaq kernel: [ 5412.520048] usb 3-2: USB disconnect, address 3
Dec  1 02:02:18 ubu-compaq kernel: [ 5422.352027] usb 3-2: new low speed USB device using uhci_hcd and address 4
Dec  1 02:02:19 ubu-compaq kernel: [ 5422.551185] usb 3-2: configuration #1 chosen from 1 choice
Dec  1 02:02:19 ubu-compaq kernel: [ 5422.927577] generic-usb 0003:051D:0002.0006: hiddev96,hidraw1: USB HID v1.10 Device [APC Back-UPS ES 550 FW:843.K2 .D USB FW:K2 ] on usb-0000:00:1d.1-2/input0
```

Does this mean the USB port isn't the issue?

Also, I added **apcupsd: 127.0.0.1** to the /etc/host.allow file. Still, running **sudo apcacces**s gives the same Connection Refused error, as does running **/etc/init.d/apcupsd status**. 

*DING*

I ran **/etc/init.d/apcupsd start** and got this: (*invalid-ups-type*)
So I checked the apcupsd.cong file and I had UPSTYPE *ups*, rather than UPSTYPE **usb**. I'm such a ninny. Now **sudo apcaccess** gives a list of variables. 

So now what? Hold my breath and pull the cord out of the wall?

---

