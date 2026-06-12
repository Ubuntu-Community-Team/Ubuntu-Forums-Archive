---
title: "Having problems getting my built-in webcam on my HP DV6000T to work..."
date: 2008-09-11
forum: Hardware
---

### Post by stropyboy11 on 2008-09-11
Pretty self explanatory...I've tried finding and installing drivers to no avail...I'm willing to provide any information you want, I just want to get this running! Any help is appreciated.

-Stropko

---

### Post by linuxwizard on 2008-09-11
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by stropyboy11 on 2008-09-11
Here's lspci and lsusb

> stropko@stropko-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
stropko@stropko-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 002: ID 05ca:1810 Ricoh Co., Ltd
Bus 005 Device 001: ID 0000:0000 

---

### Post by linuxwizard on 2008-09-11
Your webcam > Bus 005 Device 002: ID 05ca:1810 Ricoh Co., Ltd. > your webcam is supported by this driver > [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870) or look here > [http://www.arakhne.org/ricoh/index.html](http://www.arakhne.org/ricoh/index.html) > Not sure if it will work for Hardy if that is the version of Ubuntu you are using. Good Luck

---

### Post by bobyy on 2008-09-12
Hy 
It must work ...i have the same machine with the same camera chip (ricoh..stuff) and y have no problem..

---

### Post by stropyboy11 on 2008-09-12
It's funny...I followed the directions, and it still doesn't work. I know the camera is funcional because it works in my windows partition (which, thankfully, I never use anymore =) but yeah..puzzling. Maybe a previous install attempt mucked it up? Anything I can do to check?

---

### Post by rrbarbosa on 2008-09-17
If you installed from the deb packages (from [http://www.arakhne.org/ricoh/index.html](http://www.arakhne.org/ricoh/index.html)). The package should appear in Synaptic list. So, just mark the package ricoh-webcam-r5u870 to complete removal (I am not so sure about the name).

If you installed from the source ([http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)), this should remove the driver. I never tried myself, but this was a suggestion from "r5u870-list" to my question on "Uninstalling the driver":

> 
if there is a make uninstall, just cd to the directory source and type:
make uninstall

if there is not you can do:
find /lib/modules -type f -name r5u870.ko -exec rm {} \; && depmod -a

this should remove the module from your whole system.


I had trouble with using the package from arakhne, but after installing from the source my webcam works perfectly.

---

