---
title: "Acer Aspire 5735-4774"
date: 2009-01-06
forum: Hardware
---

### Post by Tdonohue on 2009-01-06
I don't know if this is the correct place for this, but...

Just purchased this laptop, installed Ubuntu 8.10.  Everything works great out of the box.  Wireless, Desktop effects.  This is a great laptop for a beginner Ubuntu user.

Best part is, Best Buy (at least the one near me) is selling this for $399.  

I'm very excited to be part a Linux user again...my last laptop had that AR242x wireless chipset, I got it working for 1 minute once.  The AR9821 (AR5B91)  chipset here has drivers built into Ubuntu.

Tim

---

### Post by markab0572 on 2009-01-27
Hi Tdonohue

sounds great, is it possible to post a hwinfo or cfg2html report?

thx mike

---

### Post by jfalco on 2009-03-13
Not the OP, but running the same machine here is my hwinfo --short
```

cpu:
                       Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz, 1200 MHz
                       Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz, 1200 MHz
keyboard:
  /dev/input/event1    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       Intel Cantiga Integrated Graphics Controller
                       Intel Cantiga Integrated Graphics Controller
sound:
                       Intel 82801I (ICH9 Family) HD Audio Controller
storage:
                       Intel ICH9M/M-E SATA AHCI Controller
network:
  wlan0                Intel WLAN controller
  eth0                 Marvell 88E8071 PCI-E Gigabit Ethernet Controller
network interface:
  pan0                 Ethernet network interface
  wlan0                WLAN network interface
  wmaster0             Network Interface
  eth0                 Ethernet network interface
  lo                   Loopback network interface
disk:
  /dev/sdb             Generic Multi-Card
  /dev/sda             Hitachi HTS54322
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda4            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
cdrom:
  /dev/sr0             HL-DT-ST DVDRAM GT10N
usb controller:
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #1
                       Intel 82801I (ICH9 Family) USB UHCI Controller #3
                       Intel 82801I (ICH9 Family) USB UHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #1
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #6
                       Intel 82801I (ICH9 Family) USB UHCI Controller #5
                       Intel 82801I (ICH9 Family) USB UHCI Controller #4
bios:
                       BIOS
bridge:
                       Intel ICH9M LPC Interface Controller
                       Intel 82801 Mobile PCI Bridge
                       Intel 82801I (ICH9 Family) PCI Express Port 5
                       Intel 82801I (ICH9 Family) PCI Express Port 4
                       Intel 82801I (ICH9 Family) PCI Express Port 3
                       Intel 82801I (ICH9 Family) PCI Express Port 2
                       Intel 82801I (ICH9 Family) PCI Express Port 1
                       Intel Cantiga PCI Express Graphics Port
                       Intel Cantiga Memory Controller Hub
hub:
                       Linux 2.6.27-11-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-11-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Intel 82801I (ICH9 Family) SMBus Controller
                       Suyin Acer Crystal Eye webcam
```

Everything works pretty good. Just switched from OpenSUSE 11.1 and I have noticed a considerable increase in performance w/ Ubuntu. I've only been using Linux for about 2 weeks and I'm pretty impressed!! I'm sure I'll be buggin people with a lot of ?s on here. Later..

---

### Post by manolomanolo on 2009-03-19
I have got Acer Aspire 5730z and have a lot of problems with ubuntu 8.10:
[LIST]
[*]audio problems with Ubuntu start-up music (the sound "jumps")
[*]audio is very low even if alsamixer levels ar at top
[*]sometimes it's not possible to start the system after suspending/hybernating
[*]sometimes ubuntu doesn't start at all
[/LIST]

manolo@manolo-acer:~$ hwinfo --short
cpu:                                                            
                       Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz, 2000 MHz
                       Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz, 2000 MHz
keyboard:
  /dev/input/event1    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Acrox USB & PS/2 Mouse
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       Intel Cantiga Integrated Graphics Controller
                       Intel Cantiga Integrated Graphics Controller
sound:
                       Intel 82801I (ICH9 Family) HD Audio Controller
storage:
                       Intel ICH9M/M-E 2 port SATA IDE Controller
                       Intel ICH9M/M-E 2 port SATA IDE Controller
network:
  wlan0                Atheros WLAN controller
  eth0                 Marvell 88E8071 PCI-E Gigabit Ethernet Controller
network interface:
  pan0                 Ethernet network interface
  vnet0                Ethernet network interface
  wlan0                WLAN network interface
  wmaster0             Network Interface
  eth0                 Ethernet network interface
  lo                   Loopback network interface
disk:
  /dev/sdb             Generic Multi-Card
  /dev/sda             WDC WD1600BEVT-2
partition:
  /dev/sdb1            Partition
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda4            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
  /dev/sda7            Partition
cdrom:
  /dev/sr0             HL-DT-ST DVDRAM GSA-T50N
usb controller:
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #1
                       Intel 82801I (ICH9 Family) USB UHCI Controller #3
                       Intel 82801I (ICH9 Family) USB UHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #1
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #6
                       Intel 82801I (ICH9 Family) USB UHCI Controller #5
                       Intel 82801I (ICH9 Family) USB UHCI Controller #4
bios:
                       BIOS
bridge:
                       Intel ICH9M LPC Interface Controller
                       Intel 82801 Mobile PCI Bridge
                       Intel 82801I (ICH9 Family) PCI Express Port 5
                       Intel 82801I (ICH9 Family) PCI Express Port 4
                       Intel 82801I (ICH9 Family) PCI Express Port 3
                       Intel 82801I (ICH9 Family) PCI Express Port 2
                       Intel 82801I (ICH9 Family) PCI Express Port 1
                       Intel Cantiga Memory Controller Hub
hub:
                       Linux 2.6.27-11-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-11-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-11-generic uhci_hcd UHCI Host Controller
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Intel 82801I (ICH9 Family) SMBus Controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Suyin Acer Crystal Eye webcam
manolo@manolo-acer:~$

---

### Post by jfalco on 2009-03-19
> audio is very low even if alsamixer levels ar at top

Make sure the PCM slider is all the way up, that fixed it for me. 

Also this may sound weird but, Alpha 6 of Jaunty seems to work better for me than Intrepid.

---

### Post by gleble on 2009-04-13
I am running Intrepid on a 5735. Stupid question maybe but how do I access the Crystal Eye  webcam

---

### Post by jfalco on 2009-04-13
> **gleble said:**
> I am running Intrepid on a 5735. Stupid question maybe but how do I access the Crystal Eye  webcam

Install Cheese Webcam Booth I think it's

```
sudo apt-get install cheese
```

---

### Post by gleble on 2009-04-13
Installed Cheese rebooted and Hey Presto! Thanks

---

### Post by RayArdia on 2009-08-05
> **gleble said:**
> Installed Cheese rebooted and Hey Presto! Thanks
Aspire 5735, Jaunty dual-booted with the preinstalled Vista. Generally OK but following problems need attention.
1. Inbuilt Suyin Webcam doesn't seem to work on (eg) Skype. How do I test it?
2. Vista sits in a shrunken partition but it doesn't start.

Terminal results fro hwinfo --short, both before trying cheese and after are:-
ray@RayLaptop:~$ hwinfo --short
cpu:                                                            
                       Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz, 1600 MHz
                       Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz, 2000 MHz
keyboard:
  /dev/input/event7    IBM USB NetVista Full Width Keyboard.
  /dev/input/event4    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Pixart Imaging USB OPTICAL MOUSE
  /dev/input/mice      Colorado HP Wireless Laser Mini Mouse
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       Intel Cantiga Integrated Graphics Controller
                       Intel Cantiga Integrated Graphics Controller
sound:
                       Intel 82801I (ICH9 Family) HD Audio Controller
storage:
                       Intel ICH9M/M-E SATA AHCI Controller
network:
  wlan0                Intel WLAN controller
  eth0                 Marvell 88E8071 PCI-E Gigabit Ethernet Controller
network interface:
  pan0                 Ethernet network interface
  wlan0                WLAN network interface
  wmaster0             Network Interface
  eth0                 Ethernet network interface
  lo                   Loopback network interface
disk:
  /dev/sdc             Generic Multi-Card
  /dev/sdb             Freecom Mobile Drive XXS
  /dev/sda             WDC WD2500BEVT-2
partition:
  /dev/sdb1            Partition
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
cdrom:
  /dev/sr0             HL-DT-ST DVDRAM GT10N
usb controller:
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #1
                       Intel 82801I (ICH9 Family) USB UHCI Controller #3
                       Intel 82801I (ICH9 Family) USB UHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #1
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #6
                       Intel 82801I (ICH9 Family) USB UHCI Controller #5
                       Intel 82801I (ICH9 Family) USB UHCI Controller #4
bios:
                       BIOS
bridge:
                       Intel ICH9M LPC Interface Controller
                       Intel 82801 Mobile PCI Bridge
                       Intel 82801I (ICH9 Family) PCI Express Port 5
                       Intel 82801I (ICH9 Family) PCI Express Port 4
                       Intel 82801I (ICH9 Family) PCI Express Port 3
                       Intel 82801I (ICH9 Family) PCI Express Port 2
                       Intel 82801I (ICH9 Family) PCI Express Port 1
                       Intel Cantiga Memory Controller Hub
hub:
                       Philips Semiconductors USB 2.0 Hub
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.28-14-generic ehci_hcd EHCI Host Controller
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Intel 82801I (ICH9 Family) SMBus Controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Suyin Acer Crystal Eye webcam
ray@RayLaptop:~$ sudo apt-get install cheese
[sudo] password for ray: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cheese
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2808kB of archives.
After this operation, 5206kB of additional disk space will be used.
Get:1 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe cheese 2.26.0-0ubuntu1 [2808kB]
Fetched 2808kB in 3s (715kB/s)   
Selecting previously deselected package cheese.
(Reading database ... 137271 files and directories currently installed.)
Unpacking cheese (from .../cheese_2.26.0-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up cheese (2.26.0-0ubuntu1) ...

ray@RayLaptop:~$ hwinfo --short
cpu:                                                            
                       Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz, 1600 MHz
                       Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz, 2000 MHz
keyboard:
  /dev/input/event7    IBM USB NetVista Full Width Keyboard.
  /dev/input/event4    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Pixart Imaging USB OPTICAL MOUSE
  /dev/input/mice      Colorado HP Wireless Laser Mini Mouse
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       Intel Cantiga Integrated Graphics Controller
                       Intel Cantiga Integrated Graphics Controller
sound:
                       Intel 82801I (ICH9 Family) HD Audio Controller
storage:
                       Intel ICH9M/M-E SATA AHCI Controller
network:
  wlan0                Intel WLAN controller
  eth0                 Marvell 88E8071 PCI-E Gigabit Ethernet Controller
network interface:
  pan0                 Ethernet network interface
  wlan0                WLAN network interface
  wmaster0             Network Interface
  eth0                 Ethernet network interface
  lo                   Loopback network interface
disk:
  /dev/sdc             Generic Multi-Card
  /dev/sdb             Freecom Mobile Drive XXS
  /dev/sda             WDC WD2500BEVT-2
partition:
  /dev/sdb1            Partition
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
cdrom:
  /dev/sr0             HL-DT-ST DVDRAM GT10N
usb controller:
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #1
                       Intel 82801I (ICH9 Family) USB UHCI Controller #3
                       Intel 82801I (ICH9 Family) USB UHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #1
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #6
                       Intel 82801I (ICH9 Family) USB UHCI Controller #5
                       Intel 82801I (ICH9 Family) USB UHCI Controller #4
bios:
                       BIOS
bridge:
                       Intel ICH9M LPC Interface Controller
                       Intel 82801 Mobile PCI Bridge
                       Intel 82801I (ICH9 Family) PCI Express Port 5
                       Intel 82801I (ICH9 Family) PCI Express Port 4
                       Intel 82801I (ICH9 Family) PCI Express Port 3
                       Intel 82801I (ICH9 Family) PCI Express Port 2
                       Intel 82801I (ICH9 Family) PCI Express Port 1
                       Intel Cantiga Memory Controller Hub
hub:
                       Philips Semiconductors USB 2.0 Hub
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-14-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.28-14-generic ehci_hcd EHCI Host Controller
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Intel 82801I (ICH9 Family) SMBus Controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Suyin Acer Crystal Eye webcam
ray@RayLaptop:~$

---

