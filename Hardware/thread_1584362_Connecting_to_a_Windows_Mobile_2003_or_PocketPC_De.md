---
title: "Connecting to a Windows Mobile 2003 or PocketPC Device"
date: 2010-09-29
forum: Hardware
---

### Post by boxcorner on 2010-09-29
Hello

I am using Ubuntu 9.10 Karmic Koala and have a Dell Axim Pocket PC with Windows Mobile 2003 Second Edition, connected via USB.

I would like to be able to transfer files.

Based on the instructions that I found here:
[https://help.ubuntu.com/community/PortableDevices/WindowsMobile](https://help.ubuntu.com/community/PortableDevices/WindowsMobile)

When I type:  
"sudo synce-serial-start"
the result is:
"synce-serial-start is now waiting for your device to connect"
and Windows Mobile displays:
"Status: Connected"

When I type:
"synce-pls"
the result is:
"** Message: Device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0 not fully set in Hal, skipping
No such file or directory"
Clearly something is wrong, but I don't know how to put it right.

When I type:
"synce-pstatus"
the result is:
"** Message: Device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0 not fully set in Hal, skipping
Version
=======
Version:    4.21.1088 (Microsoft Windows Mobile 2003 Pocket PC Phone Edition)
Platform:   3 (Windows CE)
Details:    ""

System
======
Processor architecture: 5 (ARM)
Processor type:         2577 (StrongARM)
Page size:              0x10000

Power
=====
ACLineStatus: 01 (Online)

Status for main battery
=========================
Flag:          8 (Charging)
LifePercent:   99%
LifeTime:      Unknown
FullLifeTime:  Unknown

Status for backup battery
=========================
Flag:          1 (High)
LifePercent:   100%
LifeTime:      Unknown
FullLifeTime:  Unknown

Store
=====
Store size: 33165312 bytes (31 megabytes)
Free space: 28430876 bytes (27 megabytes)

Memory for storage: 33243136 bytes (31 megabytes)
Memory for RAM:     33243136 bytes (31 megabytes)"

So, there is communication of sorts.  Could someone please tell me what I am doing wrong  and how to configure things so I can transfer files?  

Thanks in advance.

Addendum Saturday, 02 October 2010
Upgraded to Ubuntu 10.04 LTS Lucid Lynx

---

### Post by Cas07 on 2010-11-13
I just attempted to get my old iPaq h4150 (WM2003) working and managed to transfer files on Maverick 10.10 by simply doing the following:

```

apt-get install synce-hal librapi2-tools

sudo rmmod ipaq

synce-pls

```


This is all I needed it to do and wasn’t interested in setting up any sync but I hope this may help.

---

### Post by boxcorner on 2011-06-03
> **Cas07 said:**
> I just attempted to get my old iPaq h4150 (WM2003) working and managed to transfer files on Maverick 10.10 by simply doing the following:

```

apt-get install synce-hal librapi2-tools

sudo rmmod ipaq

synce-pls

```


This is all I needed it to do and wasn&#8217;t interested in setting up any sync but I hope this may help.
Thanks.  
I just want Ubuntu to recognise the device, so I can transfer files.  
I am not interested in setting up any sync either.

I am now using Ubuntu 10.10
With this version of Ubuntu, Synaptic Package Manager seems unable to find synce-dccm or librra0-tools
So the instructions located here [https://help.ubuntu.com/community/PortableDevices/WindowsMobile]("https://help.ubuntu.com/community/PortableDevices/WindowsMobile[")
appear to be incorrect for this version.

Using Terminal, sudo synce-serial-start results in the following:

Warning!
You have firewall rules that may prevent SynCE from working properly!
Warning!
synce-serial-start cannot find the dccm process.
Without dccm your PPP connection will soon terminate!
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
LCP: timeout sending Config-Requests
Connection terminated.
Receive serial link is not 8-bit clean:
Problem: all had bit 7 set to 0
Modem hangup
synce-serial-start was unable to start the PPP daemon!

With the firewall disabled, sudo synce-serial-start results in the following:

Warning!
You have firewall rules that may prevent SynCE from working properly!
Warning!
synce-serial-start cannot find the dccm process.
Without dccm your PPP connection will soon terminate!
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
Cannot determine ethernet address for proxy ARP
local  IP address 192.168.131.102
remote IP address 192.168.131.201
synce-serial-start is now waiting for your device to connect

The devices doesn't appear to be listed in Places, nor is there any icon representing it on the desktop. 

However, the device beeped, then displayed:

"Communication Error: Cannot start communications with the desktop computer.  Reconnect your device. If the problem persists, see Microsoft ActiveSync Help."

When I disconnected/reconnected the USB and then ran sudo synce-serial-start again the result was:

Error!
synce-serial-start could not find the serial port /dev/ttyUSB0.
Is your Windows CE device really connected?

I still don't understand what do I need to do to get it connected.  
Any more help would be much appeciated.

---

### Post by boxcorner on 2011-06-08
I have just discovered that OpenOffice.org 3.2 Writer opens .pwi files created on my old Dell Axim PC running Windows Mobile 2003 Second Edition Version 4.21.1088 (Build 14260.2.0.2)... hope this helps someone!

---

### Post by ImConfused on 2012-01-08
It seems with Ubuntu 11.04 there is a support file that has been a problem and removed from the repository.  That has prevented any ability correctly install the software to sync with my Dell Axim x50 Windows 2003CE.  I hope that this gets repaired by 12.04 so I can add files to my PDA.  11.04 has been the most stable of any Ubuntu I have ever used so I don't want to experiment and mess that up.

---

