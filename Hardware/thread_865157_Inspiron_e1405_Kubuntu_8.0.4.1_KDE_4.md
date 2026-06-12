---
title: "Inspiron e1405 Kubuntu 8.0.4.1 KDE 4"
date: 2008-07-20
forum: Hardware
---

### Post by antilog on 2008-07-20
I installed the latest Kubuntu with KDE 4 on my Dell Inspiron e1405 in an effort to migrate away from MS.  The following is a list of problems I am having, for those who may be thinking about doing the same:

- kwallet - unknown password, unable to follow community instructions to reset
- kdrc - unable to rdp into known working machines
- logmein - displays the screen, but no interaction (no rdp, no logmein = no remote admin, which I do all day....)
- wifi - unable to use security (wep or wpa)

This is after spending around 6 hours of following guides and recommendations.

I am trying to resist the urge to move to Mac, where everything seems to just work (design OS for the hardware), because they are closed and proprietary.  Really trying to go open-source, but it's a nightmare so far on laptop.  Desktop and server environment has been quite a pleasure - I am running an Ubuntu Server 8.0.4.1 running VMWare Server 2 RC1 which hosts a Ubuntu Server webserver serving 4 sites, and I got that up and running remarkably quickly.  In fact, when a Vista update killed the host>guest networking, I was able to build an Ubuntu Server host quickly and move the guest over to it, and was online relatively quickly.

I guess I am tired of hacking wifi drivers...

---

### Post by antilog on 2008-07-20
RE: the wifi problem
I followed this tut: [http://ge.ubuntuforums.com/showthread.php?t=769990](http://ge.ubuntuforums.com/showthread.php?t=769990)
But it doesn't say how to manage the wifi networks.  

```
lshw -C network
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:5b:cd:6e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

```
ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586
```

```
ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: ssb)
```

```
lsmod |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx
ssb                    34308  1 b44
ndiswrapper           192920  0
usbcore               146028  7 ndiswrapper,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
```

Could someone please help with this?  I spent about 6 hours on this last night and 3 1/2 hours so far today.  I just want to be able to use my laptop in a cafe...

---

### Post by antilog on 2008-07-20
More wifi:

```
root@host:~# modprobe -r b43 b44 ssb ndiswrapper bcm43xx
root@host:~# depmod -ae
root@host:~# modprobe ndiswrapper
root@host:~# modprobe b44
root@host:~# ifconfig wlan0 up
root@host:~# iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.
```

---

### Post by antilog on 2008-07-20
So I wipe-out all the work I've done over the last 2 days, installing Ubuntu 8.04.1 insteaad of Kubuntu 8.04.1 KDE4, since all of the tutorials referenced menus that are nowhere to be found in Kubuntu KDE4.

I followed this tutorial [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff), following the Hardy instructions.

No joy.

Please help me get off the Windows-crack without having to be a driver programmer - I've got a life outside hacking wifi drivers.

Thanks!!

---

### Post by antilog on 2008-07-20
Awesome.  I followed the steps to compile ndiswrapper on [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

And screwed up my home directory chmod'ing it to complete on of the steps.

So now I'm thinking - get a wifi card that works better with Ubuntu ro try another distro.  I'd rather stick to the Debian line though, which I am most familiar with...

---

