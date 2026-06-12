---
title: "Wireless forum didn't help. Anywhere else I can go?"
date: 2008-11-09
forum: General Help
---

### Post by kingleer on 2008-11-09
The wireless forum didn't help much in setting up my bcm4311 rev 1 card in ubuntu 8.10 (it's a broadcom card). Is there anything else I can do or anywhere else I can go for help?

---

### Post by adult swim on 2008-11-09
do you have access to internet via ethernet?

---

### Post by kingleer on 2008-11-09
Yes. I'm on my ubuntu install right now. 

But I blacklisted a lot of stuff following previous guides.

---

### Post by adult swim on 2008-11-09
post the output of ```
cat /etc/modprobe.d/blacklist
```

---

### Post by kingleer on 2008-11-09
> 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
 

I actually unblacklisted the stuff I blacklisted myself.

---

### Post by adult swim on 2008-11-09
now run ```
sudo apt-get install b43-fwcutter
```

---

### Post by kingleer on 2008-11-09
okay, done

> 
k@ubuntu:~$ sudo apt-get install b43-fwcutter
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/16.9kB of archives.
After this operation, 106kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 100078 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a011-4ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:011-4ubuntu1) ...



---

### Post by adult swim on 2008-11-09
did it pop up a blue screen and say something about extracting firmware?

---

### Post by kingleer on 2008-11-09
> 
did it pop up a blue screen and say something about extracting firmware? 


Nope.

---

### Post by kingleer on 2008-11-09
But I think I already tried doing this, and when i first installed b43-fwcutter I do remember a dialogue box about fetching firmware. But that might have been on another install...

---

### Post by Metaleks on 2008-11-09
Don't want to hijack this thread or anything from the person helping him, but try this on a clean install (or on your current install, but we won't know if it'll work since you already messed around with a bunch of stuff). Run this in order:

```
sudo rmmod b44
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo /etc/init.d/networking restart
```

---

### Post by adult swim on 2008-11-09
paste the results of ```
sudo iwlist scanning
``` and ```
sudo lshw -C network
```

---

### Post by kingleer on 2008-11-09
Okay, I'll try adultswim's advice first. A clean install would take a while to set up. 

> 
k@ubuntu:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

k@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:15:c5:82:fe:fb
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.129 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1e:4c:3b:e7:bb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:d7:01:15:0f:6b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


---

### Post by adult swim on 2008-11-09
now try ```
sudo modprobe -r b43 wl
sudo modprobe b43
```

---

### Post by kingleer on 2008-11-09
Okay, done.

---

### Post by kingleer on 2008-11-09
It's getting late. I'm going to try and do a fresh install and use bfw-cutter. 

Thanks anyway. :(

---

### Post by kingleer on 2008-11-09
Okay, I did a fresh install. Am now downloading updates. 

After the 8.10 updates are done, where should I begin?

---

