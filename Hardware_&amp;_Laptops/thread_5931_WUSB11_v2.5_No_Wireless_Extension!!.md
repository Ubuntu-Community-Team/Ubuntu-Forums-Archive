---
title: "WUSB11 v2.5 No Wireless Extension!?!?"
date: 2004-11-23
forum: Hardware &amp; Laptops
---

### Post by arostami on 2004-11-23
I am running the newest stable release of Ubuntu called warty and have been trying to get my WUSB11 v2.5 wireless USB card to work with it. I understand that version 2.5 uses a prism2 chipset which uses a linux compatable chipset which made me happy.

I get messages indicating that the usb device is found and that the drivers are loaded:


from dmesg:
```

usb 1-1: new full speed USB device using address 2
usb 1-1: config 1 has an invalid interface number: 1 but max is 0
usb 1-1: config 1 has no interface number 0
prism2usb_init: prism2_usb.o: 0.2.1-pre21 Loaded
prism2usb_init: dev_info is: prism2_usb
usbcore: registered new driver prism2_usb

```


from lsusb:
```

Bus 001 Device 002: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
Bus 001 Device 001: ID 0000:000

```

from lsmod | grep prism2:
```

prism2_usb             69892  0
p80211                 30736  1 prism2_usb
usbcore               104292  4 prism2_usb,uhci_hcd

```


However, when I do iwconfig I am sorely dissapointed:
```

lo        no wireless extensions.

wlan0     no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extension

```


Also, wlan0 doesn't show up when I use ifconfig (although maybe that's expected).

The only thing that be of some concern are the two lines from dmesg:

```

usb 1-1: config 1 has an invalid interface number: 1 but max is 0
usb 1-1: config 1 has no interface number 0

```

I'm not sure what these errors or warnings mean and if they could be cuasing the problem.


Any help is appreciated.

---

### Post by az on 2004-11-23
You need the linux-wlan-ng package from universe. 

There are two commands you need to enter to turn on the radio in your device for it to work.  I still cannot figure out how to use wep, though.

It should also work with ndiswrapper (mine needs version 0.11, though)  Ndiswrapper uses your windows drivers for the device.  I had to remove the prism2_usb modules first, though.

Copy the windows driver files to your home drive and then open a terminal

sudo rmmod prism2_usb
sudo rmmod p80211
sudo ndiswrapper -i NETPRISM.inf (WHatever your inf file is named...)
sudo modprobe ndiswrapper
sudo ndiswrapper -l

Then configure your device though the regular network interface.  Ndiswrapper uses wireless extensions and so the common way to configure wireless devices will work (wep works).  linux-wlan-ng uses its own command line utilities and are not part of the gnome graphical interface (yet)

---

### Post by arostami on 2004-11-23
So I tried using ndiswrapper 10.1 which is what synaptic (apt-get) downloads however I had no luck detecting the device.  So I decided to try and the newest version (11.0), however to my dismay apparently I don't have the files needed to build modules and I haven't been able to find the correct version on synaptic.

I am running kernel 2.6.8.1-3 i686 smp, which may be why finding the proper build environment is a bit of a challenge for me, does anyone know how I can get support to build this ndispackage or know of a .deb package made for Ubuntu?

---

### Post by az on 2004-11-24
I built them for the 386 kernel:

[http://ubuntuforums.org/showthread.php?t=5648](http://ubuntuforums.org/showthread.php?t=5648)

[http://www.vif.com/users/mzajac/ndiswrapper-modules_0.11-2.6.8.1-3-386_i386.deb](http://www.vif.com/users/mzajac/ndiswrapper-modules_0.11-2.6.8.1-3-386_i386.deb)
[http://www.vif.com/users/mzajac/ndiswrapper-utils_0.11_i386.deb](http://www.vif.com/users/mzajac/ndiswrapper-utils_0.11_i386.deb)


To build them yourself, you need the source from thendiswrapper site and you need to install the build-essential and linux-headers packages.  The linux-headers package should match your kernel (smp)

Good luck!

---

### Post by joshchernoff on 2005-06-05
[QUOTE=azz]You need the linux-wlan-ng package from universe. 

There are two commands you need to enter to turn on the radio in your device for it to work.  I still cannot figure out how to use wep, though.

It should also work with ndiswrapper (mine needs version 0.11, though)  Ndiswrapper uses your windows drivers for the device.  I had to remove the prism2_usb modules first, though.

Copy the windows driver files to your home drive and then open a terminal

sudo rmmod prism2_usb
sudo rmmod p80211
sudo ndiswrapper -i NETPRISM.inf (WHatever your inf file is named...)
sudo modprobe ndiswrapper
sudo ndiswrapper -l

Then configure your device though the regular network interface.  Ndiswrapper uses wireless extensions and so the common way to configure wireless devices will work (wep works).  linux-wlan-ng uses its own command line utilities and are not part of the gnome graphical interface (yet)[/QUOTE]


i get  a inval driver with the .inf i got from linksys.com it's for the wusb11 v2.5
I get this from ndiswrapper -l

---

