---
title: "Not able to switch Huawei E173 to modem mode"
date: 2011-03-10
forum: Hardware
---

### Post by miskho on 2011-03-10
Hello, it seems I'm able to switch the mode of my Huawei E173 device from one mode to another:

```

root@sleepy:~# lsusb|grep Hua
Bus 002 Device 009: ID 12d1:1c0b Huawei Technologies Co., Ltd. 
root@sleepy:~# usb_modeswitch -c /etc/usb_modeswitch.conf

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 009 on bus 002 ...
Using endpoints 0x0f (out) and 0x8f (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: HUAWEI  
   Model String: Mass Storage    
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x0f ...
 OK, message successfully sent
 Device is gone, skipping any further commands

Checking for mode switch (max. 20 times, once per second) ...
 Original device is gone already, not checking
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Found correct target device

Mode switch succeeded. Bye.

```But it is still detected as mass storage device:
```

root@sleepy:~# tail /var/log/messages
Mar 10 18:09:50 sleepy kernel: [  782.416297] usb 2-2: new high speed USB device using ehci_hcd and address 10
Mar 10 18:09:50 sleepy kernel: [  782.550927] usb 2-2: configuration #1 chosen from 1 choice
Mar 10 18:09:50 sleepy kernel: [  782.552130] usb 2-2: bad CDC descriptors
Mar 10 18:09:50 sleepy kernel: [  782.552226] usb 2-2: bad CDC descriptors
Mar 10 18:09:50 sleepy kernel: [  782.552432] usb 2-2: bad CDC descriptors
Mar 10 18:09:50 sleepy kernel: [  782.552602] usb 2-2: bad CDC descriptors
Mar 10 18:09:50 sleepy kernel: [  782.552957] scsi15 : SCSI emulation for USB Mass Storage devices
Mar 10 18:09:55 sleepy kernel: [  787.553592] scsi 15:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Mar 10 18:09:55 sleepy kernel: [  787.555434] sd 15:0:0:0: Attached scsi generic sg2 type 0
Mar 10 18:09:55 sleepy kernel: [  787.564537] sd 15:0:0:0: [sdb] Attached SCSI removable disk

```I'm using 
```
usb_modeswitch -c /etc/usb_modeswitch.conf
``` to switch the modes, my
config file is as follows:
```

root@sleepy:~# cat /etc/usb_modeswitch.conf
DisableSwitching=0

EnableLogging=0
# Huawei E270+ (HSPA+ modem)
# Huawei E1762
# Huawei E1820
#
# Contributor: Paranoid Paranoia

DefaultVendor= 0x12d1
DefaultProduct= 0x1c0b

TargetVendor= 0x12d1
TargetProduct= 0x1c08

CheckSuccess=20

MessageEndpoint= 0x0f
MessageContent="55534243123456780000000000000011060000000000000000000000000000" 

```Most likely I'm not using a correct TargetProduct number, because the Network Manager does not recognize the device. I'm using Ubuntu Lucyd (10.04) 
I also tried 0x1c05 (as suggested in one of the forums) but with that I was unable to switch.
Please help!!

Miso

---

### Post by nitrogendream on 2011-04-11
The correct target product number for the Huawei E173 is the following one.
 
TargetProduct= 0x1c23

---

