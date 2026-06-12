---
title: "Firewire expresscard"
date: 2010-02-04
forum: Hardware
---

### Post by aib007 on 2010-02-04
Hi, I would like to ask for a little help. I have a TC desktop konnect 6 firewire interface that is connected through an expresscard to my Toshiba Satellite. I am have tried all the possible commands but unfortunately ubuntu studio doesn't see it. I am quite new and unexperienced so this turned out into a really painful and traumatizing experience. The expresscard however is detected, but I cannot figure out how to make ubuntu see my soundcard. Here is what I copied from the system report: 

XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge
Property    Value
info.subsystem    pci
info.product    XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge
info.udi    /org/freedesktop/Hal/devices/pci_104c_8231
info.vendor    Texas Instruments
info.parent    /org/freedesktop/Hal/devices/pci_8086_2843
pci.product    XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge
pci.vendor_id    4172
pci.vendor    Texas Instruments
pci.product_id    33329
pci.device_protocol    0
pci.device_subclass    4
pci.subsys_vendor_id    0
pci.device_class    6
pci.subsys_product_id    0
pci.linux.sysfs_path    /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0
linux.hotplug_type    2
linux.subsystem    pci
linux.sysfs_path    /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0
XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link)
Property    Value
info.subsystem    pci
info.product    XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link)
info.vendor    Texas Instruments
info.parent    /org/freedesktop/Hal/devices/pci_104c_8231
info.linux.driver    ohci1394
info.udi    /org/freedesktop/Hal/devices/pci_104c_8235
pci.product    XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link)
pci.vendor_id    4172
pci.vendor    Texas Instruments
pci.product_id    33333
pci.device_protocol    16
pci.device_subclass    0
pci.subsys_vendor_id    22136
pci.device_class    12
pci.subsys_product_id    4660
pci.linux.sysfs_path    /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/0000:04:00.0
linux.hotplug_type    2
linux.subsystem    pci
linux.sysfs_path    /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/0000:04:00.0 
 

Please if anybody knows what I could do, give me some advice. 
I already tried to use the sudo modprobe pciehp command, and it says module not detected, also CONFIG_HOTPLUG_PCI_PCIE=y means the module should be in the kernel. I would realy like to focus on making some music, so please give any sugestions. Thank you.

---

### Post by cchhrriiss121212 on 2010-02-04
Firewire audio devices are supported only through jack sound server using ffado, so look that up in your list of installed sound applications, it is very useful for music production on linux.
According to the ffado database, your device has "planned support status" [http://www.ffado.org/?q=node/504](http://www.ffado.org/?q=node/504). So it may not be functional just yet. 
Not all hardware is supported on linux because it requires co-operation from the manufaturers. There are plenty of supported devices available, so you may have to trade yours in for something already supported.
I would give jack a go and see whether it recognizes the interface in the interface selection box.

---

### Post by aib007 on 2010-02-09
Hi. Thank you for your suggestion. However it is planned to get Ffado support for over a year now, so I'm not so sure this will change anytime soon. I am new to linux, and unfortunately I realized that a sound card should be supported after I acquired this one. I'm very happy with it, the only problem is that in Windows I get the system overloded very fast, this didn't happen with an Edirol fa-101 that I borrowed from a friend. However, the Edirol soundcard was supported by Ffado and still didn't work in Ubuntu. That is why I presumed it is a problem coming from the Firewire Expresscard. Another idea I had, was about introducing the windows or mac driver into ubuntu. It is possible with network adapters, isn't it also possible for other drivers? Does anyone know a program to convert mac drivers for ubuntu?

---

### Post by iponeverything on 2010-02-09
> It is possible with network adapters, isn't it also possible for other drivers? Does anyone know a program to convert mac drivers for ubuntu?

Unfortunately not. ndiswrapper is a NDIS API implementation for linux -- which is specific to network drivers.

---

### Post by cchhrriiss121212 on 2010-02-09
It's a possibility that the express card is the problem from what you have posted. You could post another thread in the Multimedia Production category as I know a lot of people there have firewire devices working with Ubuntu Studio.
What happened with the Edirol device specifically? There are a few tweaks you need to do to get firewire devices functional (like adding yourself to audio and video groups).
This is also important if you haven't seen it already: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by aib007 on 2010-02-10
Well thanks a lot for your help. I will post in the Multimedia Production category. I think there are a few things that might not work. I have installed Ubuntu Studio 8.04, 9.04, also 64 Studio. The same problem. I don't how I could see if the problem is the Expresscard, it's TI so it should work (it works fine in Windows) or the firewire soundcard. Under /dev there is no /raw1394... i don't have anymore the edirol fa101, but I can tell you it didn't show up in Jack control. Well maybe i will buy another laptop in the future, I saw that quite a few people mention the lenovo t61 works well with ubuntu, and it has a firewire slot. Or a Mac Powerbook, Ardour works on OSx and also my soundcard has drivers for it.

---

