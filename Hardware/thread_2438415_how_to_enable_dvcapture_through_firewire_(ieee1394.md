---
title: "how to enable dvcapture through firewire (ieee1394)"
date: 2020-03-11
forum: Hardware
---

### Post by akg-bruggeman on 2020-03-11
Hello,

Newbie here...
 Ubuntu 19.1 Studio user & installed very recently (multiboot win10)
Can't seem to get dv-capture working via the firewirecard
(i have around a 100 mini-dv-tapes which i would like to capture in the native dv-format)

Kdenlive doesn't seem to suppport the ancient mini-dv-format,
so i installed Kino but kino doesn't recognize any capture device or camera 
Below i posted the Hardware-info-dump, which clearly shows the firewire-card being detected
(Texas Instruments TSB12LV23 IEEE-1394 Controller)

Visited many fora/threads to try and find a solution,
but besides that they are of several years ago,
no one seems to have found a solution...

So how can i get dv-capture working ?
Anyone ?
:confused:



i have done this in terminal:
sudo nano   /etc/modprobe.d/blacklist-firewire.conf


to achieve this:
# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.


#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394


#blacklist firewire-ohci
#blacklist firewire-sbp2

-----------------

also i added this:
[https://ubuntu.pkgs.org/18.04/ubuntu-main-amd64/libraw1394-dev_2.1.2-1_amd64.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-main-amd64/libraw1394-dev_2.1.2-1_amd64.deb.html)
Install Howto
Update the package index:
# sudo apt-get update
Install libraw1394-dev deb package:
# sudo apt-get install libraw1394-dev


----------------

also done in terminal:

hwinfo --short

resulted in:
cpu:                                                            
                       Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz, 2541 MHz
                       Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz, 2566 MHz
keyboard:
  /dev/input/event2    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      ImPS/2 Logitech Wheel Mouse
monitor:
                       IIYAMA ProLiteH430
graphics card:
                       Hightech Information Caicos [Radeon HD 5450]
sound:
                       Intel NM10/ICH7 Family High Definition Audio Controller
                       ATI Cedar HDMI Audio [Radeon HD 5400/6300/7300 Series]
storage:
                       Intel NM10/ICH7 Family SATA Controller [IDE mode]
network:
  enp2s8               Intel NM10/ICH7 Family LAN Controller
network interface:
  enp2s8               Ethernet network interface
  lo                   Loopback network interface
disk:
  /dev/sdf             Generic SD/MMC
  /dev/sdd             Generic Compact Flash
  /dev/sdb             ST3250310AS
  /dev/sdg             Generic MS/MS-Pro
  /dev/sde             Generic SM/xD-Picture
  /dev/sdc             TOSHIBA MQ01ABF0
  /dev/sda             M4-CT064M4SSD2
partition:
  /dev/sdb1            Partition
  /dev/sdb2            Partition
  /dev/sdb5            Partition
  /dev/sdc1            Partition
  /dev/sda1            Partition
  /dev/sda2            Partition
cdrom:
  /dev/sr0             HL-DT-ST DVD-RAM GSA-H60L
usb controller:
                       Intel NM10/ICH7 Family USB UHCI Controller #4
                       Intel NM10/ICH7 Family USB UHCI Controller #2
                       Intel NM10/ICH7 Family USB UHCI Controller #3
                       Intel NM10/ICH7 Family USB UHCI Controller #1
                       Intel NM10/ICH7 Family USB2 EHCI Controller
bios:
                       BIOS
bridge:
                       Intel 82801GB/GR (ICH7 Family) LPC Interface Bridge
                       Intel 82946GZ/PL/GL PCI Express Root Port
                       Intel 82801 PCI Bridge
                       Intel 82946GZ/PL/GL Memory Controller Hub
hub:
                       Linux Foundation 1.1 root hub
                       Linux Foundation 1.1 root hub
                       Linux Foundation 2.0 root hub
                       Linux Foundation 1.1 root hub
                       Linux Foundation 1.1 root hub
memory:
                       Main Memory
firewire controller:
                       Texas Instruments TSB12LV23 IEEE-1394 Controller
unknown:
                       FPU
                       DMA controller
                       PIC
                       Keyboard controller
                       Intel NM10/ICH7 Family SMBus Controller

---

