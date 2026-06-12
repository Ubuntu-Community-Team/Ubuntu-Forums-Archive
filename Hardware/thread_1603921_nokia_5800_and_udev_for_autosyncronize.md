---
title: "nokia 5800 and udev for autosyncronize"
date: 2010-10-23
forum: Hardware
---

### Post by nowardev on 2010-10-23
well  i have nokia 5800 and i was creating a script to syncronize it  with my pc.
i tried to use udev  using a testscript very simple that should create a file on /tmp folder but  i can't get it work ...(echo hi >>/tmp/nokiaattached.txt)


have this informations for udev to run a script everytime this device is attached to my computer ....  
```
lsusb

Bus 001 Device 023: ID 0421:0156 Nokia Mobile Phones 

```

```
lsscsi 
[0:0:0:0]    disk    ATA      Hitachi HTS54161 SBDO  /dev/sda
[1:0:0:0]    cd/dvd  MATSHITA DVD-RAM UJ-850S  1.10  /dev/sr0
[22:0:0:0]   disk    Nokia    S60              1.0   /dev/sdd

```

i have tried with saved on file /etc/udev/rules.d/80-nokia.rules
but nothing happend 



SUBSYSTEMS=="usb", ATTRS{idVendor}=="0421", ATTRS{idProduct}=="0156", OWNER="root", GROUP="peace", MODE="0660", RUN+="echo fia>>/tmp/aresyn-qt-bash" 

 


SUBSYSTEMS=="usb",DRIVERS=="usb",ATTRS{idVendor}=="0421", ATTRS{idProduct}=="0156", OWNER="root", GROUP="disk", RUN+="/tmp/aresyn-qt-bash"

KERNELS=="1-3:1.0", SUBSYSTEMS=="usb",DRIVERS=="usb-storage",ATTRS{vendor}=="Nokia   ",    ATTRS{model}=="S60             " ,OWNER="root", GROUP="disk", RUN+="/tmp/aresyn-qt-bash"

    

```
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/host14/target14:0:0/14:0:0:0/block/sdb':
    KERNEL=="sdb"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="1"
    ATTR{ro}=="0"
    ATTR{size}=="15564800"
    ATTR{alignment_offset}=="0"
    ATTR{capability}=="53"
    ATTR{stat}=="     190      632     6576     1028        0        0        0        0        0     1028     1028"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/host14/target14:0:0/14:0:0:0':
    KERNELS=="14:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="0"
    ATTRS{vendor}=="Nokia   "
    ATTRS{model}=="S60             "
    ATTRS{rev}=="1.0 "
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x241"
    ATTRS{iodone_cnt}=="0x241"
    ATTRS{ioerr_cnt}=="0x1"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/host14/target14:0:0':
    KERNELS=="target14:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/host14':
    KERNELS=="host14"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0':
    KERNELS=="1-3:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v0421p0156d0100dc00dsc00dp00ic08isc06ip50"
    ATTRS{supports_autosuspend}=="0"
    ATTRS{interface}=="USB Mass Storage Interface"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-3':
    KERNELS=="1-3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}=="Bulk transfer method configuration"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="1669"
    ATTRS{idVendor}=="0421"
    ATTRS{idProduct}=="0156"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="15"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Nokia"
    ATTRS{product}=="Nokia 5800 XpressMusic"
    ATTRS{serial}=="358279034921039"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="324"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.32-25-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x27cc"
    ATTRS{subsystem_vendor}=="0x1179"
    ATTRS{subsystem_device}=="0xff10"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d000027CCsv00001179sd0000FF10bc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

UDEV_LOG=3
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/host14/target14:0:0/14:0:0:0/block/sdb
MAJOR=8
MINOR=16
DEVNAME=/dev/sdb
DEVTYPE=disk
SUBSYSTEM=block
ID_VENDOR=Nokia
ID_VENDOR_ENC=Nokia\x20\x20\x20
ID_VENDOR_ID=0421
ID_MODEL=S60
ID_MODEL_ENC=S60\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
ID_MODEL_ID=0156
ID_REVISION=1.0
ID_SERIAL=Nokia_S60_358279034921039-0:0
ID_SERIAL_SHORT=358279034921039
ID_TYPE=disk
ID_INSTANCE=0:0
ID_BUS=usb
ID_USB_INTERFACES=:080650:
ID_USB_INTERFACE_NUM=00
ID_USB_DRIVER=usb-storage
ID_PATH=pci-0000:00:1d.7-usb-0:3:1.0-scsi-0:0:0:0
ID_FS_LABEL=_b_2_$____
ID_FS_LABEL_ENC=\xb7b\x2a2\x8a\x24\xd0\xd7\xfb\x05
ID_FS_UUID=CDF2-6BE2
ID_FS_UUID_ENC=CDF2-6BE2
ID_FS_VERSION=FAT32
ID_FS_TYPE=vfat
ID_FS_USAGE=filesystem
UDISKS_PRESENTATION_NOPOLICY=0
DEVLINKS=/dev/block/8:16 /dev/disk/by-id/usb-Nokia_S60_358279034921039-0:0 /dev/disk/by-path/pci-0000:00:1d.7-usb-0:3:1.0-scsi-0:0:0:0 /dev/disk/by-uuid/CDF2-6BE2 /dev/disk/by-label/\xb7b\x2a2\x8a\x24\xd0\xd7\xfb\x05

```

---

### Post by nowardev on 2010-10-23
fixed 
this works 

kdesudo kate /etc/udev/rules.d/80-nokiaphone.rules

save the file with :


#nokia 5800
SUBSYSTEMS=="usb",ATTRS{idVendor}== "0421", ATTRS{idProduct}=="0156",GROUP="disk", RUN+="/tmp/resyn-qt-bash"

where /tmp/resyn-qt-bash is the script ...

now... this script is only bash no graphical apps like kdialog ...or other stuff... for that there is some work to do like

xhost + 
export DISPLAY=:0 
 kdialog --textinputbox  "Continue or cancel?" 
for syncronization i have to complete the script

---

### Post by nowardev on 2010-10-26
here it's 

this script syncronize 2 folders
and of course there is the udev file :) to automount nokia 5800
i have to automatize automount and then run the script ... i have some issue about launching the script , as normal user via udev and running graphical application via udev but i am working on it :P

[http://kde-apps.org/content/show.php/resyn-qt-bash?content=134053](http://kde-apps.org/content/show.php/resyn-qt-bash?content=134053)

---

