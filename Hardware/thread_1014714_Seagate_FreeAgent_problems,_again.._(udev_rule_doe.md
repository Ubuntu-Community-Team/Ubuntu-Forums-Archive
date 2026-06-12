---
title: "Seagate FreeAgent problems, again.. (udev rule doesn't seem to work)"
date: 2008-12-18
forum: Hardware
---

### Post by mh114 on 2008-12-18
Hi, I've just switched to Linux (still have a small XP installation as a dual boot) after having dual boot with Windows as the primary OS for years. :) I have Ubuntu 8.10 installed, and now I'm having problems with my Seagate FreeAgent external USB HDD.

It worked fine yesterday, but today I have been unable to get Ubuntu recognise the drive.. I've tried the tricks described in [this thread](http://ubuntuforums.org/showthread.php?t=750105&highlight=freeagent), to no avail. It seems that the udev rule isn't matching anything, since I added a echo command to the fixer script that should create a file to my home directory, but the script gets never executed.

Here is the udev rule (**/etc/udev/rules.d/85-usb-hd-fix.rules**):
```

BUS=="scsi", SYSFS{vendor}=="Seagate*", RUN+="/usr/bin/usbhdfix %k"
```
I've also tried this one:
```
SUBSYSTEM=="block",KERNEL=="sd?",ATTRS{vendor}=="Seagate*",ATTRS{product}=="FreeAgent*",RUN+="/usr/bin/usbhdfix %k"

```

Here is script I'm using (**/usr/bin/usbhdfix**):
```
#!/bin/bash
echo Testing > /home/mika/test.txt
echo 1024 > /sys/block/$1/device/max_sectors
echo 1 > /sys/block/$1/device/scsi_disk:*/allow_restart
echo 1 > /sys/class/scsi_disk/$1/allow_restart
```

If the script was executed, I would have test.txt in my home, but nope. :(

Here is some dmesg output, it's those infamous read errors:
```
 [2666.384025] usb 3-2: reset high speed USB device using ehci_hcd and address 2
[ 2666.796246] usb 3-2.4: new high speed USB device using ehci_hcd and address 25
[ 2681.868313] usb 3-2.4: device descriptor read/64, error -110
[ 2697.044364] usb 3-2.4: device descriptor read/64, error -110
[ 2697.220833] usb 3-2.4: new high speed USB device using ehci_hcd and address 26
[ 2712.292294] usb 3-2.4: device descriptor read/64, error -110
[ 2727.468357] usb 3-2.4: device descriptor read/64, error -110
[ 2727.644357] usb 3-2.4: new high speed USB device using ehci_hcd and address 27
[ 2732.664407] usb 3-2.4: device descriptor read/8, error -110
[ 2737.784088] usb 3-2.4: device descriptor read/8, error -110
[ 2737.960356] usb 3-2.4: new high speed USB device using ehci_hcd and address 28
[ 2742.980147] usb 3-2.4: device descriptor read/8, error -110
[ 2748.100218] usb 3-2.4: device descriptor read/8, error -110
[ 2748.204484] hub 3-2:1.0: unable to enumerate USB device on port 4
```
Sometimes it tries ohci_hcd instead of ehci_hcd, but they both result to the same read/# errors..

Any ideas? Anybody having Seagate FreeAgent, and the udev-rule in place? Does it work if you add that kind of test echo to the script? Why is my rule not matching the HDD?

All help is appreciated! :) I have my music on the HDD so I'd really like to get it working.. I should have bought another USB drive, though.. :P

---

### Post by kgr132 on 2009-01-12
Not related to your problem, but another problem you'll likely have with the FreeAgent Go drive is that after it's mounted, it will spin down and Ubuntu won't be able to get it to spin back up. To fix that, I disabled the drive's standby mode with this:

make sure you have the sdparm package installed.

Usage: sdparm [--all] [--clear=STR] [--command=CMD] [--dbd] [--defaults]
              [--dummy] [--flexible] [--get=STR] [--help] [--hex] [--inquiry]
              [--long] [--page=PG[,SPG]] [--quiet] [--save] [--set=STR]
              [--six] [--transport=TN] [--vendor=VN] [--verbose] [--version]
              DEVICE

       sdparm --enumerate [--all] [--inquiry] [--long] [--page=PG[,SPG]]
              [--transport=TN] [--vendor=VN]
  where:
    --all | -a            list all known attributes for given device
    --clear=STR | -c STR    clear (zero) attribute value(s)
    --command=CMD | -C CMD    perform CMD (e.g. 'eject')
    --dbd | -B            set DBD bit in mode sense cdb
    --defaults | -D       set a mode page to its default values
    --dummy | -d          don't write back modified mode page
    --enumerate | -e      list known pages and attributes (ignore device)
    --flexible | -f       compensate for common errors, relax some checks
    --get=STR | -g STR    get (fetch) attribute value(s)
    --help | -h           print out usage message
    --hex | -H            output in hex rather than name/value pairs
    --inquiry | -i        output INQUIRY VPD page(s) (def: mode page(s))
    --long | -l           add description to attribute output
    --page=PG[,SPG] | -p PG[,SPG]    page (and optionally subpage) number
                          [or abbrev] to output, change or enumerate
    --quiet | -q          suppress device vendor/product/revision string line
    --save | -S           place mode changes in saved page as well
    --set=STR | -s STR    set attribute value(s)
    --six | -6            use 6 byte SCSI mode cdbs (def: 10 byte)
    --transport=TN | -t TN    transport protocol number [or abbrev]
    --vendor=VN | -M VN    vendor (manufacturer) number [or abbrev]
    --verbose | -v        increase verbosity
    --version | -V        print version string and exit

CODE:
# sudo sdparm -al /dev/sdb 
    /dev/sdb: Seagate   FreeAgent Go  100F
    Direct access device specific parameters: WP=0  DPOFUA=0
Power condition [po] mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]  Idle timer active
  STANDBY     1  [cha: y, def:  1, sav:  1]  Standby timer active
  ICT         0  [cha: n, def:  0, sav:  0]  Idle condition timer (100 ms)
  SCT       2400  [cha: y, def:2400, sav:2400]  Standby condition timer (100 ms)

# sudo sdparm --clear STANDBY -6 /dev/sdb 
    /dev/sdb: Seagate   FreeAgent Go  100F

# sudo sdparm -al /dev/sdb 
    /dev/sdb: Seagate   FreeAgent Go  100F
    Direct access device specific parameters: WP=0  DPOFUA=0
Power condition [po] mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]  Idle timer active
  STANDBY     0  [cha: n, def:  1, sav:  0]  Standby timer active
  ICT         0  [cha: n, def:  0, sav:  0]  Idle condition timer (100 ms)
  SCT         0  [cha: n, def:2400, sav:  0]  Standby condition timer (100 ms)

# sudo sdparm --save -6 /dev/sdb
    /dev/sdb: Seagate   FreeAgent Go  100F

---

### Post by sarang on 2009-01-12
I am not sure what exactly is wrong, but the following might be helpful:

1. Playing with the priority of the udev rule. Specifically, try the non-standard priority of 93. This way the rule will be executed after all standard auto-mounting actions. 

2. Try to figure out the attributes that udev is still able to 'see' using the 
```
udevinfo -a -p /sys/block/NODENAME
```

command, replacing [FONT="Courier New"]NODENAME[/FONT] by [FONT="Courier New"]sda[/FONT], [FONT="Courier New"]sdb[/FONT] etc as appropriate for your disk. See [http://www.reactivated.net/writing_udev_rules.html]("http://www.reactivated.net/writing_udev_rules.html") for more details. I think that the subsystem matcher in your rule could be replaced by [FONT="Courier New"]SUBSYSTEMS=="usb", SUBSYSTEMS=="scsi"[/FONT].

3. Also consider the 
```
sudo udevadm monitor
```
command.

Specifically, posting the outputs of the udevinfo -a -p... and udevadm monitor commands will probably aid other people in trying to figure out what the problem is.

---

### Post by mh114 on 2009-01-14
I tried to plug the drive in, and it worked for a change! I guess it's because I've "mounted/unmounted" it in Windows, I've seen that happen before. I guess when I now shutdown the system with the drive plugged, it no longer works - until I try it in Windows. Perhaps it doesn't get unmounted properly on shutdown?

I think I'll try manually unmounting it next, and then plugging it back in to see if it still works.

Thanks for the help so far, below is the output of the commands you gave. My current udev rule worked as well, as it wrote test.txt to my home as intended.

> **sarang said:**
> 1. Playing with the priority of the udev rule. Specifically, try the non-standard priority of 93. This way the rule will be executed after all standard auto-mounting actions.
I have yet to try this, but I guess I will.

> 2. Try to figure out the attributes that udev is still able to 'see' using the 
```
udevinfo -a -p /sys/block/NODENAME
```
Here's the output. Based on it, my current udev rule should be valid (and it is, since it has now worked)..
```

udevinfo -a -p /sys/block/sdb

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/block/sdb':
    KERNEL=="sdb"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="488397168"
    ATTR{capability}=="12"
    ATTR{stat}=="     278    15726    16894     4048        7        3       80       84        0     2004     4132"

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/block':
    KERNELS=="block"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0':
    KERNELS=="2:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="Seagate "
    ATTRS{model}=="FreeAgentDesktop"
    ATTRS{rev}=="100D"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x12c"
    ATTRS{iodone_cnt}=="0x12c"
    ATTRS{ioerr_cnt}=="0x1"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="1024"

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0':
    KERNELS=="target2:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2':
    KERNELS=="host2"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0':
    KERNELS=="3-2.1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v0BC2p3000d0000dc00dsc00dp00ic08isc06ip50"
    ATTRS{interface}=="Interface0"

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1':
    KERNELS=="3-2.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}=="Config0"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="2780"
    ATTRS{idVendor}=="0bc2"
    ATTRS{idProduct}=="3000"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"

    ATTRS{busnum}=="3"
    ATTRS{devnum}=="4"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Seagate"
    ATTRS{product}=="FreeAgentDesktop"
    ATTRS{serial}=="            6RY04CP0"

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3/3-2':
    KERNELS=="3-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="83"
    ATTRS{idVendor}=="05e3"
    ATTRS{idProduct}=="0608"
    ATTRS{bcdDevice}=="0702"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="3"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="4"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{product}=="USB2.0 Hub"

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="87"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.27-9-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:02.2"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.2':
    KERNELS=="0000:00:02.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x0068"
    ATTRS{subsystem_vendor}=="0x1695"
    ATTRS{subsystem_device}=="0x1000"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="22"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v000010DEd00000068sv00001695sd00001000bc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

> 3. Also consider the 
```
sudo udevadm monitor
```
command.
..and here's the monitor output:
```

udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent

UDEV  [1231926133.132349] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1 (usb)
UEVENT[1231926133.139941] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0 (usb)
UEVENT[1231926133.172735] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/usb_endpoint/usbdev3.4_ep01 (usb_endpoint)
UEVENT[1231926133.173053] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/usb_endpoint/usbdev3.4_ep81 (usb_endpoint)
UEVENT[1231926133.173591] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/usb_endpoint/usbdev3.4_ep00 (usb_endpoint)
UDEV  [1231926133.175274] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/usb_endpoint/usbdev3.4_ep00 (usb_endpoint)
UDEV  [1231926133.282877] add      /module/libusual (module)
UEVENT[1231926133.283878] add      /bus/usb/drivers/libusual (drivers)
UDEV  [1231926133.286866] add      /bus/usb/drivers/libusual (drivers)
UDEV  [1231926133.287394] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0 (usb)
UDEV  [1231926133.305803] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/usb_endpoint/usbdev3.4_ep01 (usb_endpoint)
UDEV  [1231926133.310638] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/usb_endpoint/usbdev3.4_ep81 (usb_endpoint)
UEVENT[1231926133.341140] add      /module/usb_storage (module)
UDEV  [1231926133.342551] add      /module/usb_storage (module)
UEVENT[1231926133.354050] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2 (scsi)
UEVENT[1231926133.354096] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/scsi_host/host2 (scsi_host)
UEVENT[1231926133.367553] add      /bus/usb/drivers/usb-storage (drivers)
UDEV  [1231926133.379232] add      /bus/usb/drivers/usb-storage (drivers)
UDEV  [1231926133.383571] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2 (scsi)
UDEV  [1231926133.410435] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/scsi_host/host2 (scsi_host)
UEVENT[1231926138.368598] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0 (scsi)
UDEV  [1231926138.382476] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0 (scsi)
UEVENT[1231926138.386653] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0 (scsi)
UEVENT[1231926138.388354] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/scsi_disk/2:0:0:0 (scsi_disk)
UDEV  [1231926138.551010] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0 (scsi)
UDEV  [1231926138.556645] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/scsi_disk/2:0:0:0 (scsi_disk)
UEVENT[1231926141.965800] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/block/sdb (block)
UEVENT[1231926141.965844] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/block/sdb/sdb1 (block)
UEVENT[1231926141.965857] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/block/sdb/sdb2 (block)
UEVENT[1231926141.970809] add      /devices/virtual/bdi/8:16 (bdi)
UDEV  [1231926141.971732] add      /devices/virtual/bdi/8:16 (bdi)
UEVENT[1231926141.973927] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/scsi_device/2:0:0:0 (scsi_device)
UEVENT[1231926141.978437] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/scsi_generic/sg3 (scsi_generic)
UDEV  [1231926141.990013] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/scsi_device/2:0:0:0 (scsi_device)
UDEV  [1231926142.013799] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/scsi_generic/sg3 (scsi_generic)
UDEV  [1231926142.293806] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/block/sdb (block)
UDEV  [1231926142.455929] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/block/sdb/sdb1 (block)
UDEV  [1231926142.619137] add      /devices/pci0000:00/0000:00:02.2/usb3/3-2/3-2.1/3-2.1:1.0/host2/target2:0:0/2:0:0:0/block/sdb/sdb2 (block)
UDEV  [1231926143.560816] add      /devices/virtual/bdi/8:17-fuseblk (bdi)

```

---

### Post by sarang on 2009-01-14
Yes, I also think that the

```

SUBSYSTEM=="block",KERNEL=="sd?",ATTRS{vendor}=="Seagate*",ATTRS{product}=="FreeAgent*",RUN+="/usr/bin/usbhdfix %k"

```
 rule should work.

I am stumped by the 'okay after mounting in windows' issue... perhaps the following might help:

1. Compare the outputs of 
```

sudo mount

```
and
```

sudo cat /media/.hal-mtab

```
after the disk has been successfully automounted by ubuntu. .hal-mtab should show the automounted drive with its mount options. Perhaps the mount options could be useful in investigating the problem.

2. Unless you have a customised mount arrangement for some volumes, make sure that /media does not contain mountpoints for devices that are not connected. The automounter should ideally remove the mountpoint after those devices have been unmounted/ejected, but sometimes it does not... In the past, I have had that mess up automounting.

---

