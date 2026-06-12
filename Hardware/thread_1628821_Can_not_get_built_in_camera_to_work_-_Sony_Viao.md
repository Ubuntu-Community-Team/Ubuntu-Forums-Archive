---
title: "Can not get built in camera to work - Sony Viao"
date: 2010-11-23
forum: Hardware
---

### Post by Jonners59 on 2010-11-23
My wife has a Sony Vaio PCG 5J1T, laptop with a built in camera.  It is about 3 years old.  I have installed Ubuntu 10.10, but the camera will not start.  I am not even sure that there are installed drivers.

i686 Intel(R) Core(TM) 2 Duo CPU T7250 "2.00GHz
Gnome 2.32.0 (Ubuntu 2010-09-27), Linux 2.6.35-22-generic
 
PS:  It did not work on release 9.10 or 10.4 either
 
Can anyone help, please?

---

### Post by Jonners59 on 2010-11-25
Any help please!!!!

---

### Post by CharlesA on 2010-12-02
Bumped over to **Hardware & Laptops**.

I've got no idea how to figure out if it's being seen or not.

Is it enabled in the BIOS?

---

### Post by davidmohammed on 2010-12-02
first things first - need to know how ubuntu is seeing the webcam - is it a usb device or a pci device

in a terminal session type

lsusb

copy and paste the contents here in a reply

similarly

lspci

copy and paste the contents here in a reply

---

### Post by Jonners59 on 2010-12-02
The camera is built in.  She has been using a USB camera since we can not get the built in working.

> **davidmohammed said:**
> first things first - need to know how ubuntu is seeing the webcam - is it a usb device or a pci device

in a terminal session type

lsusb

copy and paste the contents here in a reply

[HTML]chiara@chiara-Pinkviao:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0471:1201 Philips (or NXP) Arima Bluetooth Device
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 044e:300d Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/HTML]

> **davidmohammed said:**
> 

similarly

lspci

copy and paste the contents here in a reply

[HTML]chiara@chiara-Pinkviao:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon X2300
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
08:07.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
chiara@chiara-Pinkviao:~$ [/HTML]

Also found that it will not play Windows install CDs, does DVD videos, etc....  would this be shown in the above too?

---

### Post by Jonners59 on 2010-12-02
> **CharlesA said:**
> Bumped over to **Hardware & Laptops**.

I've got no idea how to figure out if it's being seen or not.

Is it enabled in the BIOS?

How's that Charles?

---

### Post by CharlesA on 2010-12-02
> **Jonners59 said:**
> How's that Charles?
Just boot into setup and see if it's listed there. I know my Asus netbook has a setting to enable/disable onboard devices in there.

---

### Post by davidmohammed on 2010-12-03
hi there,
  this [thread]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=821343&page=4") relates to your webcam.  It looks like you have to compile and install some code into your kernel to get it to work - at least upto ubuntu 10.04.

see post #36 and onwards - they claim to have got the webcam working for 10.04.

---

### Post by Jonners59 on 2010-12-04
Cheers
my wife's machine is 10.10, but it still does not work.

Have looked ta that thread and tried everything out, but does not work either...  Seems there are replies there too about 10.10 and 10.04

I have left a reply there too.

---

### Post by Jonners59 on 2010-12-22
The solution:

First of all install mercurial and some other project dependencies


 [HTML]sudo apt-get install mercurial libglib2.0-dev libusb-dev[/HTML] Now you can download the source


 [HTML]hg clone http://bitbucket.org/ahixon/r5u87x/[/HTML] Change into the source directory and issue the following three commands.


 [HTML]cd r5u87x
make
make rules
sudo make install[/HTML] If your user isn’t part of the video group you will probably have to  modify /etc/group and make yourself a member of that group otherwise you  might experience Permission Denied errors.


 Also make sure you can record because uploading the wrong firmware will in some cases allow you to see output but not record it.


 [HTML]mencoder tv:// -tv driver=v4l2:device=/dev/video0 -nosound -ovc lavc -o test.avi[/HTML] If you want to clean things up afterwards you can run the following commands
[HTML]sudo apt-get --purge remove mercurial libglib2.0-dev libusb-dev
sudo apt-get --purge autoremove
rm -r r5u87x[/HTML]

This solution was found here:[http://www.gilesbathgate.com/tag/linux/](http://www.gilesbathgate.com/tag/linux/)


[:p:p]("http://www.gilesbathgate.com/tag/linux/")

---

### Post by Jonners59 on 2012-02-03
Simpler

[HTML]Ubuntu 	$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial 	$ hg clone http://bitbucket.org/ahixon/r5u87x/ 	$ cd r5u87x 	$ make 	$ sudo make install 	$ sudo r5u87x-loader --reload[/HTML]

---

