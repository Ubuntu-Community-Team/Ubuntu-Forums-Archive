---
title: "APCUPSD - Terminating due to configuration file errors"
date: 2011-09-11
forum: Hardware
---

### Post by ub-newbie on 2011-09-11
Problem: Can’t get APCUPSD working.
System: Ubuntu 10.04 LTS (Lucid)
APC – XS 1300

Symptoms:  When running “apcupsd”, system returns “Terminating due to configuration file errors.”

/etc/apcupsd/APCUPSD.conf – changes made/common settings:
	#UPSNAME XS1300
	UPSCABLE usb
	UPSTYPE usb
	DEVICE
	#POLLTIME 60
	UPSCLASS standalone
	UPSMODE disabled

/etc/default/apcupsd – changes made:
	ISCONFIGURED=yes

“lsusb” shows:
 Bus 004 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply

"usb-devices" shows:
T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=051d ProdID=0002 Rev=00.90
S:  Manufacturer=American Power Conversion
S:  Product=Back-UPS BX1300G FW:864.L5 .D USB FW:L5 
S:  SerialNumber=4B1121P34802  
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid


“ls -l /sys/bus/usb/drivers” shows:
drwxr-xr-x 2 root root 0 2011-09-11 12:59 btusb
drwxr-xr-x 2 root root 0 2011-09-11 13:19 hiddev
drwxr-xr-x 2 root root 0 2011-09-11 12:59 hub
drwxr-xr-x 2 root root 0 2011-09-11 12:59 usb
drwxr-xr-x 2 root root 0 2011-09-11 13:19 usbfs
drwxr-xr-x 2 root root 0 2011-09-11 12:59 usbhid

When I unplug/re-plug APC, logs show:
Sep 11 13:38:13 tv kernel: [ 2367.415538] usb 4-1: USB disconnect, address 2
Sep 11 13:38:27 tv kernel: [ 2381.540090] usb 4-1: new full speed USB device using ohci_hcd and address 4
Sep 11 13:38:28 tv kernel: [ 2381.779844] usb 4-1: configuration #1 chosen from 1 choice
Sep 11 13:38:28 tv kernel: [ 2381.874580] generic-usb 0003:051D:0002.0003: hiddev96,hidraw0: USB HID v1.00 Device [American Power Conversion Back-UPS BX1300G FW:864.L5 .D USB FW:L5 ] on usb-0000:00:04.0-1/input0

---------------------------
I’m stumped.. I assume USB is the correct cable type (cable is USB on PC end, and RJ-?? on the APC end.

I’ve rebooted, and plugged/un-plugged many times, still same results.

I’m using APCUSPD from the repositories, 3.14.6.

Anyone know how to get this working?

10-29- Bump??
--------------------
10-29:  Turns out it was that /etc/apcupsd/apcupsd.conf had:
```
LOCKFILE /var/lock/apcupsd/apcupsd
```
when it should have been-
```
LOCKFILE /var/lock
```

---

