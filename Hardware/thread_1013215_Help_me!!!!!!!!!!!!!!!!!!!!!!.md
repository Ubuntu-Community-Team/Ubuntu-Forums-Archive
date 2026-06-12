---
title: "Help me!!!!!!!!!!!!!!!!!!!!!!"
date: 2008-12-16
forum: Hardware
---

### Post by Nitrozzy7 on 2008-12-16
help!!! I have an acer 5715z and my wifi doesn't work. I have the suspicion that it's not a driver problem so is there a way to activate my wifi through the terminal? And how can I convert flv to any other format that can be read by a PlayStation3 like mp4 mpeg ect. And one more how can I install .bin files?:confused:

---

### Post by SuperSonic4 on 2008-12-16
Descriptive topic titles = more efficient help

wifi = Not sure, what card do you have?
Video Conversion = Avidemux  + Codecs

```
sudo apt-get install avidemux
```

Is there not a readme with the bin file? Just .bin could mean any binary

---

### Post by Nitrozzy7 on 2008-12-18
How can I learn what's my wifi card?! I'm Just a rookie and I PANIC easily. Try to be patient with me. OR I will return to Windows XP (...HA-HA-HA):guitar:

---

### Post by Nico-dk on 2008-12-18
Yup, descriptive topic titles is always a good idea.

When connecting to wifi it's always a good idead to disable all security for starters. If you can connect to that, then it's not the card that causing problems.

Post out from
```
sudo lshw -C network
```
This will return ao. card brand and driver info

and
```
iwconfig
```

---

### Post by |{urse on 2008-12-18
if you look through the system menu for the "Restricted drivers manager" chances are your wifi driver is there and you need to enable it.

---

### Post by |{urse on 2008-12-18
wo0 post #500

---

### Post by theamber on 2008-12-18
Check system>admi.>hardware controllers to see if is there.

---

### Post by Nitrozzy7 on 2008-12-18
*-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:42:fe:5b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.6 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
This is what came up...:confused:

---

### Post by Nitrozzy7 on 2008-12-18
How to uninstall Google Earth? It's installed in usr/googleearth:lolflag:

---

### Post by Nico-dk on 2008-12-18
> **Nitrozzy7 said:**
> I have the suspicion that it's not a driver problem
I have a suspicion it is, since I can't see you driver in the output you mentioned.

Since you haven't posted what flavour of Ubuntu you're running, I can only point you in the direction of a general guide, that seems to have helped others with your brand of wlan.

[http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

---

### Post by Nitrozzy7 on 2008-12-18
This is what came up...

nitrozzy7@Zapatista:~$ wget [http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh](http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh) -O madwifi.sh
--05:47:57--  [http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh](http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh)
           => `madwifi.sh'
Resolving kolmoskone.homelinux.org... 81.175.201.149
Connecting to kolmoskone.homelinux.org|81.175.201.149|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,804 (8.6K) [text/x-sh]

100%[====================================>] 8,804         32.27K/s             

05:47:58 (32.20 KB/s) - `madwifi.sh' saved [8804/8804]

nitrozzy7@Zapatista:~$ chmod +x madwifi.sh
nitrozzy7@Zapatista:~$ sudo ./madwifi.sh
[sudo] password for nitrozzy7: 
Found at least one Atheros device.
Checking build dependencies...
No packages found matching subversion.
Installing subversion...Selecting previously deselected package libapr1.
(Reading database ... 138087 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.2.11-1_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.12+dfsg-3_i386.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Setting up libapr1 (1.2.11-1) ...

Setting up libaprutil1 (1.2.12+dfsg-3) ...

Setting up libsvn1 (1.4.6dfsg1-2ubuntu1) ...

Setting up subversion (1.4.6dfsg1-2ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
OK
Installing libc6-dev...Selecting previously deselected package linux-libc-dev.
(Reading database ... 138161 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-22.45_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu4_i386.deb) ...
Setting up linux-libc-dev (2.6.24-22.45) ...
Setting up libc6-dev (2.7-10ubuntu4) ...
OK
...build dependencies OK
Fetching sources from SVN...OK
Removing previous MadWifi installations...OK
Building MadWifi...OK
Installing MadWifi...OK
Loading kernel module...OK
Adding ath_pci to /etc/modules...OK
It seems that the driver did not detect compatible hardware.
Please try to connect to an AP and post the output of
sudo ./madwifi.sh --info to the forum.

Is this helping you?
My ubuntu is 8.04.... and updated!!!!!!!!!
And how I'm I gona upgrade to the 8.10 version? I tried download it and burn it to a dvd, when I booted my pc it didn't do a thing! I checked the boot order through BIOS and it was ok. !!!!!!!!!!!lol.lol.lol.!!!!!!!!!!!!! 
:lolflag:

---

### Post by bdoe on 2008-12-20
> **Nitrozzy7 said:**
> And how I'm I gona upgrade to the 8.10 version? I tried download it and burn it to a dvd, when I booted my pc it didn't do a thing! I checked the boot order through BIOS and it was ok.
Try burning it to CD instead. Although there are exceptions, DVDs are generally not bootable media.

---

### Post by skern03 on 2008-12-20
I had a laptop with a very nice Linksys wireless g adapter. Had the same problem you have - and it was definitely the card. There is a new proprietary driver available for Broadcom chipsets. Unfortunately, the laptop (which was ancient) died a couple of weeks ago, so I can't recover the actual driver settings or name. 

Try looking through this thread and see if it helps. 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Also, re running 8.10, I had no end of hassles with it, and went back to 8.04. If that's heresy on the forum, so be it. But it flat-out doesn't run on my system. The thread above suggests rather than reverting to an earlier build, that you fix it. I didn't read through it, but it might solve your issues.


> **Nitrozzy7 said:**
> *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:42:fe:5b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.6 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
This is what came up...:confused:

---

