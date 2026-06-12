---
title: "bad formatted pen drive"
date: 2010-05-08
forum: Hardware
---

### Post by it-RobyC on 2010-05-08
hi all
first of all sorry for my english: i'll try to explain better if some parts are not understandable
I'm in trouble with my pen drive 
I did use gparted to format my 8Gb philips pen drive. the problem is that I did format the pen drive as an extended partition and logical partition that cover all the space of the firts one

now the pen drive doesn't  work at all!! :(
simply I can't use it becouse it doesn't appear in the list of external drive.

**I cannot FORMAT the drive!**
It doesn't work properly now, so both windows and linux (ubuntu) don't let me format the pen drive;
a lot of software i've tryied tell me to *"insert a medium"* (but...i cannot insert a medium into a pen drive!!)


Helped by the italian ubuntu community ([http://forum.ubuntu-it.org/index.php/topic,366836.60.html](http://forum.ubuntu-it.org/index.php/topic,366836.60.html)) i tryed a lot of test (listed below) and we think udev isn't able to understand what to do with the pen drive.

pheraps a solution is to write a udev rule to have access to MBR of the pen drive and erase it.

Can you help me, please?

tnx

TEST
Now I list software and command tryed.
I'm using Lucid Lynx

gparted doesn't show the pen drive so i can't reformat it
a lot of software or command aren't able to show the pen drive (sdc); in other case the software ask me to "insert a medium".

software i did try
sudo parted -l, dd, cfdisk, sudo hd -v -n 512 /dev/sdc, testdisk,  gnome-format, gparted live, hp formatting tool, iBored, philps softwares ([http://www.storageupdates.philips.com/it/faq_ufd.html](http://www.storageupdates.philips.com/it/faq_ufd.html))

this is a screenshot of palimsest
<img>http://forum.ubuntu-it.org/index.php?action=dlattach;topic=366836.0;attach=76131;image</img>


```

lsusb
Bus 001 Device 003: ID 1307:0163 Transcend Information, Inc. 512MB/1GB Flash Drive

```

```

dmesg
[ 7628.908035] usb 1-8: new high speed USB device using ehci_hcd and address 5
[ 7629.041122] usb 1-8: configuration #1 chosen from 1 choice
[ 7629.053358] scsi8 : SCSI emulation for USB Mass Storage devices
[ 7629.058505] usb-storage: device found at 5
[ 7629.058507] usb-storage: waiting for device to settle before scanning
[ 7634.060632] usb-storage: device scan complete
[ 7634.062050] scsi 8:0:0:0: Direct-Access     USBest   USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[ 7634.062428] sd 8:0:0:0: Attached scsi generic sg4 type 0
[ 7634.080792] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 7662.708305] usb 1-8: USB disconnect, address 5
[ 7668.616036] usb 1-8: new high speed USB device using ehci_hcd and address 6
[ 7668.749094] usb 1-8: configuration #1 chosen from 1 choice
[ 7668.765920] scsi9 : SCSI emulation for USB Mass Storage devices
[ 7668.768424] usb-storage: device found at 6
[ 7668.768427] usb-storage: waiting for device to settle before scanning
[ 7673.771853] usb-storage: device scan complete
[ 7673.773884] scsi 9:0:0:0: Direct-Access     USBest   USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[ 7673.775838] sd 9:0:0:0: Attached scsi generic sg4 type 0
[ 7673.780499] sd 9:0:0:0: [sdc] Attached SCSI removable disk




```

```


mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /media/sdb1 type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/robyc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robyc)
/dev/sr1 on /media/UNAMONTAGNADIBALLE type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)



```

```

sudo fdisk -l

Disco /dev/sda: 164.7 GB, 164696555520 byte
255 testine, 63 settori/tracce, 20023 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0xffffffff

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19268   154770178+  83  Linux
/dev/sda2           19269       20023     6064537+   5  Esteso
/dev/sda5           19269       20023     6064506   82  Linux swap / Solaris

Disco /dev/sdb: 164.7 GB, 164696555520 byte
255 testine, 63 settori/tracce, 20023 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x00980098

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       20023   160834716   83  Linux




```
```

udevadm info -a -p /sys/block/sdc

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc':
    KERNEL=="sdc"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="1"
    ATTR{ro}=="0"
    ATTR{size}=="0"
    ATTR{alignment_offset}=="0"
    ATTR{capability}=="53"
    ATTR{stat}=="       0        0        0        0        0        0        0        0        0        0        0"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0':
    KERNELS=="9:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="USBest  "
    ATTRS{model}=="USB2FlashStorage"
    ATTRS{rev}=="0.00"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x7f7"
    ATTRS{iodone_cnt}=="0x7f7"
    ATTRS{ioerr_cnt}=="0x7f6"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0':
    KERNELS=="target9:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9':
    KERNELS=="host9"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0':
    KERNELS=="1-8:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="03"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v1307p0163d0100dc00dsc00dp00ic08isc06ip50"
    ATTRS{supports_autosuspend}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-8':
    KERNELS=="1-8"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}==" 98mA"
    ATTRS{urbnum}=="10200"
    ATTRS{idVendor}=="1307"
    ATTRS{idProduct}=="0163"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="6"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="152"
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
    ATTRS{maxchild}=="10"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.32-22-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:02.1"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.1':
    KERNELS=="0000:00:02.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x005b"
    ATTRS{subsystem_vendor}=="0x10de"
    ATTRS{subsystem_device}=="0xcb84"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="21"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v000010DEd0000005Bsv000010DEsd0000CB84bc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""




```

```



udevadm test /sys/block/sdc
run_command: calling: test
udevadm_test: version 151
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/lib/udev/rules.d/40-alsa-firmware-loaders.rules' as rules file
add_rule: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:9
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:9
add_rule: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:10
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:10
add_rule: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:12
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:12
add_rule: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:13
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:13
add_rule: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:15
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:15
add_rule: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:16
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:16
parse_file: reading '/lib/udev/rules.d/40-fuse-utils.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-gnupg.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-hplip.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ia64.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-infiniband.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-isdn.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-kino.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libgphoto2-2.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libpisock9.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libsane.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-pilot-links.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ppc.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-usb-media-players.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-virtualbox-ose-dkms.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-xserver-xorg-video-intel.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-zaptel.rules' as rules file
parse_file: reading '/lib/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/lib/udev/rules.d/45-libmtp8.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libnjb5.rules' as rules file
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:4
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:6
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:8
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:10
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:12
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:14
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:16
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:18
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:20
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:22
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:24
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:26
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:28
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:30
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-libnjb5.rules:32
parse_file: reading '/etc/udev/rules.d/50-bitpim.rules' as rules file
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:1
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:2
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:3
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:4
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:5
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:6
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:7
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:8
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:9
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:10
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:11
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:12
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:13
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:14
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:15
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:16
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:17
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-bitpim.rules:18
parse_file: reading '/lib/udev/rules.d/50-firmware.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-udev-default.rules' as rules file
parse_file: reading '/lib/udev/rules.d/55-dm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/56-hpmud_support.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-cdrom_id.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-floppy.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-input.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-serial.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-dm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-tape.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-v4l.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-gnome-bluetooth-rfkill.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-mobile-action.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-option-modem-modeswitch.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-persistent-storage-edd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/64-device-mapper.rules' as rules file
parse_file: reading '/lib/udev/rules.d/64-xorg-xkb.rules' as rules file
parse_file: reading '/lib/udev/rules.d/66-xorg-synaptics.rules' as rules file
parse_file: reading '/lib/udev/rules.d/69-xorg-vmmouse.rules' as rules file
parse_file: reading '/lib/udev/rules.d/69-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-acl.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-hid2hci.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-printers.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-net-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-tty-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-ericsson-mbm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-longcheer-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-zte-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-graphics-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-sound-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/79-fstab_import.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-drivers.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-udisks.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-console-setup.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-dmraid.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-regulatory.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-usbmuxd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-hal.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-libgpod.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-pulseaudio.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-keyboard-force-release.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-keymap.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-udev-late.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-dell.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-fujitsu.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-gateway.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-ibm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-lenovo.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-toshiba.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-csr.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-hid.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-wup.rules' as rules file
parse_file: reading '/lib/udev/rules.d/97-bluetooth.rules' as rules file
parse_file: reading '/dev/.udev/rules.d/root.rules' as rules file
udev_rules_new: rules use 212328 bytes tokens (17694 * 12 bytes), 34049 bytes buffer
udev_rules_new: temporary index used 56420 bytes (2821 * 20 bytes)
udev_device_new_from_syspath: device 0x210e36b8 has devpath '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc'
udev_device_new_from_syspath: device 0x210e38c8 has devpath '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc'
udev_device_read_db: device 0x210e38c8 filled with db file data
udev_device_new_from_syspath: device 0x210e2b48 has devpath '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0'
udev_device_new_from_syspath: device 0x210e3358 has devpath '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0'
udev_device_new_from_syspath: device 0x210e3508 has devpath '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9'
udev_device_new_from_syspath: device 0x210d9498 has devpath '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0'
udev_device_new_from_syspath: device 0x210d96a0 has devpath '/devices/pci0000:00/0000:00:02.1/usb1/1-8'
udev_device_new_from_syspath: device 0x210d98a8 has devpath '/devices/pci0000:00/0000:00:02.1/usb1'
udev_device_new_from_syspath: device 0x210d9aa8 has devpath '/devices/pci0000:00/0000:00:02.1'
udev_device_new_from_syspath: device 0x210d9c68 has devpath '/devices/pci0000:00'
udev_rules_apply_to_event: LINK 'block/8:32' /lib/udev/rules.d/50-udev-default.rules:3
udev_rules_apply_to_event: GROUP 6 /lib/udev/rules.d/50-udev-default.rules:77
udev_rules_apply_to_event: IMPORT 'usb_id --export /devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc' /lib/udev/rules.d/60-persistent-storage.rules:22
util_run_program: 'usb_id --export /devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc' started
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR=USBest'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR_ENC=USBest\x20\x20'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR_ID=1307'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL=USB2FlashStorage'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL_ENC=USB2FlashStorage'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL_ID=0163'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_REVISION=0.00'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_SERIAL=USBest_USB2FlashStorage-0:0'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_TYPE=disk'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_INSTANCE=0:0'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_BUS=usb'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_USB_INTERFACES=:080650:'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_USB_INTERFACE_NUM=00'
util_run_program: '/lib/udev/usb_id' (stdout) 'ID_USB_DRIVER=usb-storage'
util_run_program: 'usb_id --export /devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc' returned with exitcode 0
udev_rules_apply_to_event: LINK 'disk/by-id/usb-USBest_USB2FlashStorage-0:0' /lib/udev/rules.d/60-persistent-storage.rules:30
udev_rules_apply_to_event: IMPORT 'path_id /devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc' /lib/udev/rules.d/60-persistent-storage.rules:47
util_run_program: 'path_id /devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc' started
util_run_program: '/lib/udev/path_id' (stdout) 'ID_PATH=pci-0000:00:02.1-usb-0:8:1.0-scsi-0:0:0:0'
util_run_program: 'path_id /devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc' returned with exitcode 0
udev_rules_apply_to_event: LINK 'disk/by-path/pci-0000:00:02.1-usb-0:8:1.0-scsi-0:0:0:0' /lib/udev/rules.d/60-persistent-storage.rules:48
udev_rules_apply_to_event: IMPORT '/sbin/blkid -o udev -p /dev/sdc' /lib/udev/rules.d/60-persistent-storage.rules:60
util_run_program: '/sbin/blkid -o udev -p /dev/sdc' started
util_run_program: '/sbin/blkid' (stderr) 'error: /dev/sdc: Permission denied'
util_run_program: '/sbin/blkid -o udev -p /dev/sdc' returned with exitcode 2
udev_rules_apply_to_event: IMPORT 'edd_id --export /dev/sdc' /lib/udev/rules.d/61-persistent-storage-edd.rules:8
util_run_program: 'edd_id --export /dev/sdc' started
util_run_program: '/lib/udev/edd_id' (stderr) 'no kernel EDD support'
util_run_program: 'edd_id --export /dev/sdc' returned with exitcode 2
udev_rules_apply_to_event: IMPORT 'udisks-part-id /dev/sdc' /lib/udev/rules.d/80-udisks.rules:96
util_run_program: 'udisks-part-id /dev/sdc' started
util_run_program: '/lib/udev/udisks-part-id' (stderr) 'libudev: udev_device_new_from_syspath: '
util_run_program: '/lib/udev/udisks-part-id' (stderr) 'device 0x930a1f0 has devpath '/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc''
util_run_program: '/lib/udev/udisks-part-id' (stderr) 'libudev: udev_device_read_db: '
util_run_program: '/lib/udev/udisks-part-id' (stderr) 'device 0x930a1f0 filled with db file data'
util_run_program: '/lib/udev/udisks-part-id' (stderr) 'using device_file=/dev/sdc syspath=/sys/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc, offset=0 ao=0 and number=0 for /dev/sdc'
util_run_program: '/lib/udev/udisks-part-id' (stderr) 'Error opening /dev/sdc: Permission denied'
util_run_program: 'udisks-part-id /dev/sdc' returned with exitcode 0
udev_rules_apply_to_event: RUN '/lib/udev/hdparm' /lib/udev/rules.d/85-hdparm.rules:2
udev_rules_apply_to_event: RUN 'socket:@/org/freedesktop/hal/udev_event' /lib/udev/rules.d/90-hal.rules:2
udev_event_execute_rules: no node name set, will use kernel supplied name 'sdc'
udev_device_update_db: unable to create temporary db file '/dev/.udev/db/block:sdc.tmp': Permission denied
udev_node_add: creating device node '/dev/sdc', devnum=8:32, mode=0660, uid=0, gid=6
udev_node_mknod: preserve file '/dev/sdc', because it has correct dev_t
node_symlink: preserve already existing symlink '/dev/block/8:32' to '../sdc'
link_find_prioritized: found '/sys/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc' claiming '/dev/.udev/links/disk\x2fby-id\x2fusb-USBest_USB2FlashStorage-0:0'
link_update: creating link '/dev/disk/by-id/usb-USBest_USB2FlashStorage-0:0' to '/dev/sdc'
node_symlink: preserve already existing symlink '/dev/disk/by-id/usb-USBest_USB2FlashStorage-0:0' to '../../sdc'
link_find_prioritized: found '/sys/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc' claiming '/dev/.udev/links/disk\x2fby-path\x2fpci-0000:00:02.1-usb-0:8:1.0-scsi-0:0:0:0'
link_update: creating link '/dev/disk/by-path/pci-0000:00:02.1-usb-0:8:1.0-scsi-0:0:0:0' to '/dev/sdc'
node_symlink: preserve already existing symlink '/dev/disk/by-path/pci-0000:00:02.1-usb-0:8:1.0-scsi-0:0:0:0' to '../../sdc'
udevadm_test: UDEV_LOG=6
udevadm_test: DEVPATH=/devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0/block/sdc
udevadm_test: MAJOR=8
udevadm_test: MINOR=32
udevadm_test: DEVNAME=/dev/sdc
udevadm_test: DEVTYPE=disk
udevadm_test: ACTION=add
udevadm_test: SUBSYSTEM=block
udevadm_test: DEVLINKS=/dev/block/8:32 /dev/disk/by-id/usb-USBest_USB2FlashStorage-0:0 /dev/disk/by-path/pci-0000:00:02.1-usb-0:8:1.0-scsi-0:0:0:0
udevadm_test: ID_VENDOR=USBest
udevadm_test: ID_VENDOR_ENC=USBest\x20\x20
udevadm_test: ID_VENDOR_ID=1307
udevadm_test: ID_MODEL=USB2FlashStorage
udevadm_test: ID_MODEL_ENC=USB2FlashStorage
udevadm_test: ID_MODEL_ID=0163
udevadm_test: ID_REVISION=0.00
udevadm_test: ID_SERIAL=USBest_USB2FlashStorage-0:0
udevadm_test: ID_TYPE=disk
udevadm_test: ID_INSTANCE=0:0
udevadm_test: ID_BUS=usb
udevadm_test: ID_USB_INTERFACES=:080650:
udevadm_test: ID_USB_INTERFACE_NUM=00
udevadm_test: ID_USB_DRIVER=usb-storage
udevadm_test: ID_PATH=pci-0000:00:02.1-usb-0:8:1.0-scsi-0:0:0:0
udevadm_test: UDISKS_PRESENTATION_NOPOLICY=0
udevadm_test: run: '/lib/udev/hdparm'
udevadm_test: run: 'socket:@/org/freedesktop/hal/udev_event'





```


HEEEELP

---

### Post by it-RobyC on 2010-05-10
up :(

---

### Post by derklempner on 2010-05-17
> **it-RobyC said:**
> I did format the pen drive as an extended partition and logical partition that cover all the space of the firts one
If you're not going to partition the drive in multiple parts, then just repartition the drive as a primary partition -- *don't* use extended and logical partitions.

---

### Post by it-RobyC on 2010-06-03
I'm trying to FORMAT my pen drive!

I cannot do this! My pen drive doesn't work properly now, so both windows and linux (ubuntu) don't let me format the pen drive.
thank you for your attention

---

### Post by mindpowerz on 2010-06-03
Google for HPUSBFW.exe, that might do the trick.

It will format any type of pen drive under Windows.

---

### Post by derklempner on 2010-06-04
> **it-RobyC said:**
> I'm trying to FORMAT my pen drive!

I cannot do this! My pen drive doesn't work properly now, so both windows and linux (ubuntu) don't let me format the pen drive.
thank you for your attention
Okay, first off, you said this:
> I did format the pen drive as an extended partition and logical partition that cover all the space of the firts one
If you're trying to format the drive, you need to make sure it's partitioned properly.  Perhaps you should start by worrying about the drive's partition table before you worry about formatting it.  If you can partition the drive any way possible, then try partitioning it as a **single primary partition** and then format it.  Then let us know what happens.

---

