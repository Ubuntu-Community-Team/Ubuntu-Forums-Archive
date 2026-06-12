---
title: "Huawei E5832S dongle not switching mode"
date: 2011-07-29
forum: Hardware
---

### Post by bhalash on 2011-07-29
I've been rolling my face on the keyboard over this for about a month. There actually seems to be a fair body of woes, workarounds and HOWTOS out there involving this class of Huawei device, but none regarding my specific model. 

I own an Huawei E5832S 3G/WIFI dongle, marketed in Ireland by O2 as the O2 Hotshot. As in common with a many other owners of Huawei dongles, I'm having problems with the dongle being detected as mass storage instead of as a 3G modem. Unfortunately I so far have been unable to make any headway in switching it to the correct mode under Linux. My system/distro info:

```
Linux tehsmallpwn 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux
```

Detailed lsusb output can be found [here](http://pastebin.com/FEk8iHxG) and firmware/hardware versions [here](http://pastebin.com/hXM2Uq0u).

lsusb shows the dongle connected in USB mode:

```
Bus 001 Device 005: ID 12d1:142d Huawei Technologies Co., Ltd.
```

Before I dive into the steps I've followed, I need to recount something strange: Windows 7 reports the correct device ID for 3G mode (0x1401) when I connect the dongle. This correct ID persists when I boot back into Linux, but the dongle still shows up as a USB mass storage device.

So here I go. My usb_modeswitch.conf is set up as follows:

```

DefaultVendor	= 	0x12d1 
DefaultProduct	= 	0x142d 

TargetVendor	=	0x12d1
TargetProduct	=	0x1401

HuaweiMode	=	1

```

When I run usb_modeswitch, a success is reported, but the mode doesn't change:

```
[root][mark] # usb_modeswitch -v 0x12d1 -p 0x142d -V 0x12d1 -P 0x1401 -c /etc/usb_modeswitch.conf 

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode, class or configuration (1)
Accessing device 021 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using endpoints 0x01 (out) and 0x81 (in)
Using endpoints 0x01 (out) and 0x81 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: Huawei Incorporated
     Product: HUAWEI Mobile Connect
  Serial No.: 1234567890ABCDEF
-------------------------
Sending Huawei control message ...
 OK, Huawei control message sent
-> Run lsusb to note any changes. Bye.

```
```

[root][mark] # lsusb | grep Huawei
Bus 001 Device 021: ID 12d1:142d Huawei Technologies Co., Ltd. 

```

Help me before I try to throw this modem through the window, only to watch it bounce off the glass with a *tink* and land on the window sill.

---

### Post by drpjkurian on 2011-07-31
Please give a try as mentioned in this thread
[http://ubuntuforums.org/showthread.php?p=11100832](http://ubuntuforums.org/showthread.php?p=11100832)

---

### Post by bhalash on 2011-07-31
Dr Kurian,

Thanks for the help, but while the problem still persists, I do have a little bit more information. Following the steps you gave, I've seen the device successfully switch modes to a HPSA modem, but it then apparently gets disconnected and reconnects as a mass storage device. Odd. 

```
[root][mark] # cat /etc/usb_modeswitch.d/12d1\:142d 
DefaultVendor	=	0x12d1 
DefaultProduct	=	0x142d 

TargetVendor	=	0x12d1
TargetProduct	=	0x1401

MessageContent="55534243123456780000000000000011062000000100000000000000000000"
```

Here is the full output from usb_modeswitch showing a successful switch of mode:

[http://pastebin.com/EnurgyAC](http://pastebin.com/EnurgyAC)

(DefaultProduct and TargetProduct were changed to reflect my own modem)

Dmesg reports that the modem is disconnected after I run the command:

```
[ 8754.737326] usb 1-3: USB disconnect, address 20
[ 8754.745376] option: option_instat_callback: error -108
[ 8754.745560] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 8754.745611] option 1-3:1.2: device disconnected
[ 8756.216120] usb 1-3: new high speed USB device using ehci_hcd and address 21
[ 8756.373358] option 1-3:1.0: GSM modem (1-port) converter detected
[ 8756.374033] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
[ 8756.375010] scsi6 : usb-storage 1-3:1.1
[ 8756.376338] option 1-3:1.2: GSM modem (1-port) converter detected
[ 8756.377175] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
[ 8756.386303] cdc_ether: probe of 1-3:1.3 failed with error -32
[ 8757.376348] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass storage     ffff PQ: 0 ANSI: 2
[ 8757.378337] scsi 6:0:0:1: Direct-Access     HUAWEI   Mass storage     ffff PQ: 0 ANSI: 2
[ 8757.391591] sr0: scsi-1 drive
[ 8757.392598] sr 6:0:0:0: Attached scsi CD-ROM sr0
[ 8757.393266] sr 6:0:0:0: Attached scsi generic sg1 type 5
[ 8757.394750] sd 6:0:0:1: Attached scsi generic sg2 type 0
[ 8757.408579] sd 6:0:0:1: [sdb] Attached SCSI removable disk
[ 9961.220110] usb 1-4: new high speed USB device using ehci_hcd and address 22
[10466.907149] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[10466.907229] option 1-3:1.0: device disconnected
```

I discovered last night that if I connect the device before I boot my laptop, it is detected correctly as a modem, but *only* then. However, Network Manager still does not see it. 

I will keep chipping away at this, thank you!

---

### Post by drpjkurian on 2011-08-02
Sorry to hear that!!

---

### Post by bhalash on 2011-08-04
NP sir!

---

