---
title: "Unable to switch mode on Huawei E173s"
date: 2014-02-03
forum: Hardware
---

### Post by aquanauta on 2014-02-03
Hi, I tried everything I found on this forum, but seems that I can not find a clear solution. Any help?

```
root@ASUS-1015E-DS03:~# usb_modeswitch -c/etc/usb_modeswitch.d/E173s

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 004 on bus 003 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x0f (out) and 0x8f (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached


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
Setting up communication with interface 0
Using endpoint 0x0f for message sending ...
Trying to send message 1 to endpoint 0x0f ...
 OK, message successfully sent
Resetting response endpoint 0x8f
Resetting message endpoint 0x0f


Checking for mode switch (max. 5 times, once per second) ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 No new devices in target mode or class found


Mode switch has failed. Bye.
```

---

### Post by aquanauta on 2014-02-03
A little update. It guess I found a solution but I am not very happy with it.
First of all. I have a new ASUS 1015E-DS03 Netbook with a fresh 12.04 LTS on it.
My intention was to connect to internet with a HUAWEI E173s-6 USB modem while on holidays to peep out what was going on at the office.
Well, that was not a go and as I did not have wifi at the hotel, everything became a little...complicated.

That being said, I should continue saying that I created a file in /etc/usb_modeswitch.d with the switching parameters:

```
# Huawei E173s

DefaultVendor=0x12d1
DefaultProduct=0x1c0b

TargetVendor=0x12d1
TargetProduct=0x1c05

CheckSuccess=5

MessageContent="55534243123456780000000000000011062000000100000000000000000000"
```

(Message content was extracted from usr/share/usb_modeswitch Huawei E173s pack), then

Created an automated rule in 40-usb_modeswitch.rules

```
# Huawei E173s
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c0b", RUN+="/usr/sbin/usb_modeswitch -c/etc/usb_modeswitch.d/E173s"
```

Restarted the machine 1.10E12 times, but I was unable to make it work. In fact, sometimes it did connect but I do not like aleatory events so I continued searching.
Ok, the modem was always on USB03, sometimes on USB01, but never on USB02. Why? Because my Logitech M525 is connected there.
When I connected it to USB02 it started working and mouse is now on a high-speed USB03 port :(
Why is that? Is this a usb_modeswitch issue, a hardware issue or Odin just abandoned me?
Please, let me know what do you think. Thanks!

---

