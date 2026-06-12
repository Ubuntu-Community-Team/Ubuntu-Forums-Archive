---
title: "apc 500 and apcupsd hell"
date: 2019-05-02
forum: Hardware
---

### Post by faustf on 2019-05-02
hi guys i try to run the  apcupsd  with my apc 500, it have  a standard usbcable (to connect at pc,and rj45 to plug in to ups ) i installed all by this  wiki [https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd) , i have a last version of linux

when i test a apc i have comlost  see the log: 

```
 apcaccess status
APC      : 001,018,0448
DATE     : 2019-05-02 12:29:42 +0200  
HOSTNAME : stefano-desktop
VERSION  : 3.14.14 (31 May 2016) debian
UPSNAME  : APC500
CABLE    : USB Cable
DRIVER   : USB UPS Driver
UPSMODE  : Stand Alone
STARTTIME: 2019-05-02 12:29:32 +0200  
STATUS   : COMMLOST 
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
NUMXFERS : 0
TONBATT  : 0 Seconds
CUMONBATT: 0 Seconds
XOFFBATT : N/A
STATFLAG : 0x05000100
END APC  : 2019-05-02 12:29:42 +0200  

```

if  i run apctest (before i stop a service apcupsd)
i have this 

```
sudo apctest


2019-05-02 12:27:16 apctest 3.14.14 (31 May 2016) debian
Checking configuration ...
sharenet.type = Network & ShareUPS Disabled
cable.type = USB Cable
mode.type = USB UPS Driver
Setting up the port ...
apctest FATAL ERROR in apctest.c at line 321
Unable to open UPS device.
  If apcupsd or apctest is already running,
  please stop it and run this program again.
apctest error termination completed


```

with dmesg  return me  

```
[  825.803495] hid-generic 0003:051D:0002.0005: hiddev0,hidraw3: USB HID v1.10 Device [American Power Conversion Back-UPS CS 500 FW:808.q8.I USB FW:q8] on usb-0000:00:1a.0-1.6/input0


```

with lsusb  return me 

```
lsusb
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 004: ID c0f3:02a1  
Bus 001 Device 003: ID 1c4f:0034 SiGma Micro 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

anyone  can help me  ?? or  can suggest me a ups  (also different brand )  surely worked ???

thanks so much

---

### Post by rbmorse on 2019-05-02
I get the same error here, fwiw.

---

### Post by him610 on 2019-05-02
> apctest FATAL ERROR in apctest.c at line 321
This is the cause of your issue. It's in the source code. It probably has not been updated recently. The vendor shows the test suite last released in 2012.
Why not test it by connecting your system to the APC 500 unit then pulling the plug at the power source to determine if and how long it will keep your system operating?

---

### Post by faustf on 2019-05-03
> **him610 said:**
>  
Why not test it by connecting your system to the APC 500 unit then pulling the plug at the power source to determine if and how long it will keep your system operating?

ithink is  not a good solution , becuase the  time is determined to age of  battery , i think s  much better if  i will not resolve a problem , chenge UPS  with SURE compatible  linux

---

### Post by him610 on 2019-05-03
I have a couple of UPS units, but I install mine to provide backup power to my network devices. Unless one buys a large capacity UPS, it won't provide more than a few minutes of standby power anyway which will probably allow you time to shut your system (desktop) down. If you have a good battery in a laptop then the need for a UPS should not be a priority.
You might need to shop around some to find what you want. Here is one I found on Amazon, [https://www.amazon.com/CyberPower-EC650LCD-Ecologic-Outlets-Compact/dp/B00DBAA696?ref_=bl_dp_s_web_2529224011&th=1]("https://www.amazon.com/CyberPower-EC650LCD-Ecologic-Outlets-Compact/dp/B00DBAA696?ref_=bl_dp_s_web_2529224011&th=1")
On the Cyberpower website, I found this page on its Linux downloads for a similar unit [https://www.cyberpowersystems.com/product/software/powerpanel-for-linux/]("https://www.cyberpowersystems.com/product/software/powerpanel-for-linux/")
Cyberpower has both 32bit and 64bit downloads; latest update was version: 1.3.2 Release Date: 02/03/2015
If I were in the market for a UPS unit I would seriously consider what Cyberpower offers.

---

