---
title: "Reviving &quot;Want to force USB stick to be '/dev/sda'&quot; I can't believe t'is impossible"
date: 2014-01-28
forum: Hardware
---

### Post by david144 on 2014-01-28
I apologize in advance, I know this is going to be long and very rantish, please bare with me and I really appreciate any constructive assistance that anyone can provide. Thanks! :)

Ok so I've been building an iSCSI target server for the last two weeks trying to figure out problems I've been having by being a good user and searching forums and the internet, but this problem is still plaguing me and it has become an itch that I absolutely must scratch.

So this guy [plonka2000 asked the exact question I'm looking for the answer to back in 2008]("http://ubuntuforums.org/showthread.php?t=920658") and I've been searching for two days (accumulated over the last week) on this problem and I know the obvious question everyone is asking themselves right now is:

[QUOTE=bingoUV][COLOR=#000000] I ask this to figure out why do you care about its device name changing?[/COLOR][/QUOTE]
[COLOR=#000000]asked in the very same post..

The answer is simply: I want to setup my RAID drives manually, and I want to know they will be labeled/mounted as a specific /dev/sd[/COLOR][COLOR=#ff0000]*X*[/COLOR] based on what I set them to be; that way when I setup my hot and cold spares I know that it will be what I printed a label up for to paste on the drive trays, so that when I get a warning that some drive has failed I can quickly pull the drive, plug in a spare and move on to configuring a new cold spare and programming fstab or whatever else I want. I don't want to spend time playing guessing games opening my case while the system is powered off to look up serial numbers and figure out what drive was labeled as what when, I want to do it manually one time.. the only time.

[Someone with the same question and a different reason for needing to mount in a specific order]("http://askubuntu.com/questions/322859/custom-udev-rules-wont-work")

As I've been testing raids with different drive configurations to figure out other problems I'm having with 4K sectors (will be a separate post) I've been peeved off about the boot drive constantly moving around as the other drives get detected and move it from sda to sdc back to sdb up to sdf.

I realize that a big portion of my problem is what I'm doing. Like plonka2000 I built my system using a flash disk. I connected to the mobo header pins because I intend to dedicate every single available bay to drives, and every PCI & PCIe slot to network cards and raid controllers and I intend to connect USB external drives for dumb storage pools as well on my external USB connectors. In the end I hope to have 16 TB of various raid configurations, and another 10-16TB of individual USB drives, I hope to have 4 nic's running in LACP (waiting on my new switch), and I want this thing to be the baddest home built SAN that I can afford on my limited means (which is pretty limited LOL) [COLOR=#ff0000]*Why not buy a QNAP or DROBO? *[/COLOR]Why should I give them the satisfaction when Linux is free to everyone! That and it's so much more satisfying to build something yourself. Been building computers since I was 11. 26 years, and yet I'm still always behind the curve and you young kids pick everything up so quick... I feel old trying to figure out what a KiB is and the standard was introduced when I was out of high school only four years... I digress :) 
:lolflag:

[COLOR=#000000]I installed from a Flash drive built from the 12.04 Server iso (not liveCD). [/COLOR][COLOR=#000000]When I installed, my installer Flash came up as sda and my boot drive partitions were created on sdb. When I boot the system with nothing but the boot flashdrive it comes up as sda, I add one hard drive my boot becomes sdb, two drives it sometimes comes up sdb sometimes sdc.

I know for many people they don't care about the device lettering so long as their /home, /, and swap work, but I'm old and stubborn! I want it to make sense to my brain which demands logic ;)

Ok so the obvious that I ran into everywhere was udev... everyone talks about udev to make your USB sticks come up as familiar mount points. I'm not interested in making /media/MyLittlePonyFlash128GB or /mnt/SpiderManUSBkeychain :) hehehe 
[/COLOR]
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221) has tons of great information but I can't get it to work, maybe it should and I've done something wrong? I hope someone can tell me where I've botched it.

[COLOR=#000000]My boot flash disk is a PNY 16GB (on sale $9 at Fry's [/COLOR]:)[COLOR=#000000] so I bought three LOL)[/COLOR][COLOR=#000000]
[/COLOR]```
san@iSCSI-SAN:/$ udevadm info -q all -n /dev/sdb
custom logging function 0x7fd5fb4fa250 registered
selinux=0
runtime dir '/run/udev'
calling: info
device 0x7fd5fb4fa2d0 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host8/target8:0:0/8:0:0:0/block/sdb'
P: /devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host8/target8:0:0/8:0:0:0/block/sdb
device 0x7fd5fb4fa2d0 filled with db file data
N: sdb
S: disk/by-id/usb-PNY_USB_2.0_FD_AA00000000002914-0:0
S: disk/by-path/pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0
E: DEVLINKS=/dev/disk/by-id/usb-PNY_USB_2.0_FD_AA00000000002914-0:0 /dev/disk/by-path/pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0
E: DEVNAME=/dev/sdb
E: DEVPATH=/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host8/target8:0:0/8:0:0:0/block/sdb
E: DEVTYPE=disk
E: ID_BUS=usb
E: ID_INSTANCE=0:0
E: ID_MODEL=USB_2.0_FD
E: ID_MODEL_ENC=USB\x202.0\x20FD\x20\x20\x20\x20\x20\x20
E: ID_MODEL_ID=007a
E: ID_PART_TABLE_TYPE=dos
E: ID_PATH=pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0
E: ID_PATH_TAG=pci-0000_00_0b_1-usb-0_8_1_0-scsi-0_0_0_0
E: ID_REVISION=1100
E: ID_SERIAL=PNY_USB_2.0_FD_AA00000000002914-0:0
E: ID_SERIAL_SHORT=AA00000000002914
E: ID_TYPE=disk
E: ID_USB_DRIVER=usb-storage
E: ID_USB_INTERFACES=:080650:
E: ID_USB_INTERFACE_NUM=00
E: ID_VENDOR=PNY
E: ID_VENDOR_ENC=PNY\x20\x20\x20\x20\x20
E: ID_VENDOR_ID=154b
E: MAJOR=8
E: MINOR=16
E: SUBSYSTEM=block
E: UDEV_LOG=7
E: USEC_INITIALIZED=2772919

```[COLOR=#000000]

to which I created 
[/COLOR]```
san@iSCSI-SAN:/$ cat /etc/udev/rules.d/10-local.rules
# Boot Drive - PNY USB 2.0 Flash Disk connected on motherboard internal header
# disk by-id:
KERNEL=="usb-PNY_USB_2.0_FD_AA00000000002914-0:0" KERNELS=="usb1" SUBSYSTEM=="usb" NAME="sda"
KERNEL=="usb-PNY_USB_2.0_FD_AA00000000002914-0:0-part1" KERNELS=="usb1" SUBSYSTEM=="usb"  NAME="sda1"
KERNEL=="usb-PNY_USB_2.0_FD_AA00000000002914-0:0-part2" KERNELS=="usb1" SUBSYSTEM=="usb"  NAME="sda2"
KERNEL=="usb-PNY_USB_2.0_FD_AA00000000002914-0:0-part5" KERNELS=="usb1" SUBSYSTEM=="usb"  NAME="sda5"
# disk by-path:
KERNEL=="pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0" KERNELS=="usb1" SUBSYSTEM=="usb"  NAME="sda"
KERNEL=="pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0-part1" KERNELS=="usb1" SUBSYSTEM=="usb"  NAME="sda1"
KERNEL=="pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0-part2" KERNELS=="usb1" SUBSYSTEM=="usb"  NAME="sda2"
KERNEL=="pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0-part5" KERNELS=="usb1" SUBSYSTEM=="usb"  NAME="sda5"
# disk by-uuid          (only valid for sda1 & sda5, sda2 has no blkid/uuid)
KERNEL=="3adeea69-9fd4-4428-86c3-f8101fb88e4b" KERNELS=="usb1" SUBSYSTEM=="usb"  NAME="sda5"
KERNEL=="ab273f03-db3e-4c59-902b-c095d726357d" KERNELS=="usb1" SUBSYSTEM=="usb"  NAME="sda1"

```

I set logging to debug and have attached a syslog[ATTACH=CONFIG]249793[/ATTACH] in case there's any additional info anyone can extrapolate from it (don't mind my iscsitarget and mdadm errors, obviously without the drives in they aren't working) but I'm at my wits end and needed to post here to save my sanity :)

I've seen other threads suggest editing grub but not giving any details on how or what to look for to change.

Less helpful are the people who suggest changing the priority in the BIOS... would have already had to do that to make it boot ;)

Is this something that can even be done or is it a kernel-life-altering event to which I should just /wrists and *blowBRAINSout* now?

---

### Post by ian-weisser on 2014-01-28
Well, mdadm internally uses UUIDs, not /dev/sdx devices. So a udev rule shouldn't be needed.
Once you create the RAID array the first time, check /etc/mdadm/mdadm.conf to confirm that the array is identified by UUID.
When you reboot, the device mount order should be irrelevant. You can even scramble it. mdadm will look for the right UUIDs and resume work.

Great discussion at [https://lists.debian.org/debian-user/2011/06/msg02164.html](https://lists.debian.org/debian-user/2011/06/msg02164.html)

 I tag my drives with the UUID and S/N instead of /dev/sdx.

---

### Post by david144 on 2014-01-28
Is there a way to customize the mdadm monitoring notification emails to include the UUID?

I started on this quest because my emails come like this:
```

[FONT=arial]This is an automatically generated mail message from [/FONT][FONT=arial]mdadm[/FONT]
[FONT=arial]running on iSCSI-SAN[/FONT]

[FONT=arial]A FailSpare event had been detected on md device /dev/md0.[/FONT]

[FONT=arial]It could be related to component device /dev/sdd.[/FONT]

[FONT=arial]Faithfully yours, etc.[/FONT]

[FONT=arial]P.S. The /proc/mdstat file currently contains the following:[/FONT]

[FONT=arial]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10][/FONT]
[FONT=arial]md0 : active raid1 sdc[0][/FONT]
[FONT=arial]      15694592 blocks super 1.2 [2/1] [U_][/FONT]

[FONT=arial]unused devices: <none>[/FONT]
```

---

### Post by david144 on 2014-01-31
ok so I tried changing the GRUB device.map and while I verified at the grub command line that my USB stick was hd0, when booting into the kernel it still goes back to sdb, sd...

So I've tried reducing my my 10-local.rules to:
```

KERNEL=="sdb", KERNELS=="usb1", SUBSYSTEM=="usb", NAME="sdz"

```

and that still didn't work

Sorry I didn't realize that I probably should have provided an attribute-walk:
```
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.
  looking at device '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host6/target6:0:0/6:0:0:0/block/sdb':
    KERNEL=="sdb"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{ro}=="0"
    ATTR{size}=="31405824"
    ATTR{stat}=="    3099     2727   138126   101580      438      697    12184  2422236        0    95120  2523816"
    ATTR{range}=="16"
    ATTR{discard_alignment}=="0"
    ATTR{events}=="media_change"
    ATTR{ext_range}=="256"
    ATTR{events_poll_msecs}=="2000"
    ATTR{alignment_offset}=="0"
    ATTR{inflight}=="       0        0"
    ATTR{removable}=="1"
    ATTR{capability}=="51"
    ATTR{events_async}==""
  looking at parent device '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host6/target6:0:0/6:0:0:0':
    KERNELS=="6:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{rev}=="1100"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="5"
    ATTRS{model}=="USB 2.0 FD      "
    ATTRS{state}=="running"
    ATTRS{queue_type}=="none"
    ATTRS{iodone_cnt}=="0x12f7"
    ATTRS{iorequest_cnt}=="0x12f7"
    ATTRS{timeout}=="30"
    ATTRS{evt_media_change}=="0"
    ATTRS{max_sectors}=="240"
    ATTRS{ioerr_cnt}=="0x1"
    ATTRS{queue_depth}=="1"
    ATTRS{vendor}=="PNY     "
    ATTRS{device_blocked}=="0"
    ATTRS{iocounterbits}=="32"
  looking at parent device '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host6/target6:0:0':
    KERNELS=="target6:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""
  looking at parent device '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host6':
    KERNELS=="host6"
    SUBSYSTEMS=="scsi"
    DRIVERS==""
  looking at parent device '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0':
    KERNELS=="1-8:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"
  looking at parent device '/devices/pci0000:00/0000:00:0b.1/usb1/1-8':
    KERNELS=="1-8"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="8"
    ATTRS{idVendor}=="154b"
    ATTRS{speed}=="480"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="3"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="500mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="0"
    ATTRS{bcdDevice}=="1100"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{serial}=="AA00000000002914"
    ATTRS{version}==" 2.00"
    ATTRS{urbnum}=="13285"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="PNY Technologies"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="007a"
    ATTRS{bDeviceClass}=="00"
    ATTRS{product}=="USB 2.0 FD"
  looking at parent device '/devices/pci0000:00/0000:00:0b.1/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="0"
    ATTRS{idVendor}=="1d6b"
    ATTRS{speed}=="480"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{authorized_default}=="1"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="0mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="10"
    ATTRS{bcdDevice}=="0308"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{serial}=="0000:00:0b.1"
    ATTRS{version}==" 2.00"
    ATTRS{urbnum}=="56"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="Linux 3.8.0-35-generic ehci_hcd"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="0002"
    ATTRS{bDeviceClass}=="09"
    ATTRS{product}=="EHCI Host Controller"
  looking at parent device '/devices/pci0000:00/0000:00:0b.1':
    KERNELS=="0000:00:0b.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci-pci"
    ATTRS{irq}=="11"
    ATTRS{subsystem_vendor}=="0x10de"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x0c0320"
    ATTRS{companion}==""
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000001"
    ATTRS{device}=="0x036d"
    ATTRS{uframe_periodic_max}=="100"
    ATTRS{enable}=="1"
    ATTRS{msi_bus}==""
    ATTRS{local_cpulist}=="0"
    ATTRS{vendor}=="0x10de"
    ATTRS{subsystem_device}=="0xc55e"
    ATTRS{numa_node}=="-1"
    ATTRS{d3cold_allowed}=="1"
  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

### Post by david144 on 2014-02-01
Ok I've got a heartbeat but it's still not quite making sense to me.

So the first problem I had originally was in my initial post I didn't have commas separating the match and assignment keys. (DUR!! only took me 10 re-reads of several of the guides online before I noticed that LOL)

Second I was trying to use KERNEL and KERNELS from two different devices entries of the attribute-walk, narrowing it down to the KERNELS=="1-8" device has gotten me some actual rules processing finally.

So here's my /etc/udev/rules.d/10-local.rules:
```

# Boot Drive - PNY USB 2.0 Flash Disk connected on motherboard internal header
KERNELS=="1-8", SUBSYSTEMS=="usb", ATTR{serial}=="AA00000000002914", NAME:="sdz"

```

I know this is matching because I see it in my log:
```

[U][B][COLOR=#008000]Feb  1 17:52:56 iSCSI-SAN udevd[480]: NAME 'sdz' /etc/udev/rules.d/10-local.rules:4
[/COLOR][COLOR=#ff0000]Feb  1 17:52:56 iSCSI-SAN udevd[480]: MODE 0664 /lib/udev/rules.d/50-udev-default.rules:55
[/COLOR][/B][/U]Feb  1 17:52:56 iSCSI-SAN udevd[480]: IMPORT builtin 'usb_id' /lib/udev/rules.d/50-udev-default.rules:56
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_VENDOR=PNY_Technologies
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_VENDOR_ENC=PNY\x20Technologies
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_VENDOR_ID=154b
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_MODEL=USB_2.0_FD
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_MODEL_ENC=USB\x202.0\x20FD
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_MODEL_ID=007a
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_REVISION=1100
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_SERIAL=PNY_Technologies_USB_2.0_FD_AA00000000002914
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_SERIAL_SHORT=AA00000000002914
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_BUS=usb
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_USB_INTERFACES=:080650:
Feb  1 17:52:56 iSCSI-SAN udevd[480]: kernel-provided name 'bus/usb/001/003' and NAME= 'sdz' disagree, please use SYMLINK+= or change the kernel to provide the proper name
Feb  1 17:52:56 iSCSI-SAN udevd[480]: creating device node '/dev/sdz', devnum=189:2, mode=0664, uid=0, gid=0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: mknod '/dev/sdz' 189:2 020664
Feb  1 17:52:56 iSCSI-SAN udevd[480]: set permissions '/dev/sdz' 020664 uid=0 gid=0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: atomically replace '/dev/char/189:2'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: created db file '/run/udev/data/c189:2' for '/devices/pci0000:00/0000:00:0b.1/usb1/1-8'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: passed -1 bytes to netlink monitor 0x7fee552e3cd0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1556 processed with 0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1557 running
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552a1720 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: no db file to read /run/udev/data/+usb:1-8:1.0: No such file or directory
Feb  1 17:52:56 iSCSI-SAN udevd[480]: passed -1 bytes to netlink monitor 0x7fee552e3cd0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1557 processed with 0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1558 running
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552a31a0 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: no db file to read /run/udev/data/+scsi:host0: No such file or directory
Feb  1 17:52:56 iSCSI-SAN udevd[480]: passed -1 bytes to netlink monitor 0x7fee552e3cd0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1558 processed with 0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1559 running
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552a12d0 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/scsi_host/host0'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: no db file to read /run/udev/data/+scsi_host:host0: No such file or directory
Feb  1 17:52:56 iSCSI-SAN udevd[480]: passed -1 bytes to netlink monitor 0x7fee552e3cd0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1559 processed with 0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1560 running
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552ae930 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: no db file to read /run/udev/data/+scsi:target0:0:0: No such file or directory
Feb  1 17:52:56 iSCSI-SAN udevd[480]: passed -1 bytes to netlink monitor 0x7fee552e3cd0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1560 processed with 0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1561 running
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552ae930 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0/0:0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: no db file to read /run/udev/data/+scsi:0:0:0:0: No such file or directory
Feb  1 17:52:56 iSCSI-SAN udevd[480]: passed -1 bytes to netlink monitor 0x7fee552e3cd0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1561 processed with 0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: seq 1562 running
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552ae930 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0/0:0:0:0/block/sdb'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552ae930 filled with db file data
Feb  1 17:52:56 iSCSI-SAN udevd[480]: removing watch on '/dev/sdb'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: GROUP 6 /lib/udev/rules.d/50-udev-default.rules:67
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552a2430 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0/0:0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552a29f0 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552af030 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552af5a0 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552afb20 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552b0130 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552b0730 has devpath '/devices/pci0000:00/0000:00:0b.1'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: device 0x7fee552b0d10 has devpath '/devices/pci0000:00'
Feb  1 17:52:56 iSCSI-SAN udevd[480]: IMPORT builtin 'usb_id' /lib/udev/rules.d/60-persistent-storage.rules:39
Feb  1 17:52:56 iSCSI-SAN udevd[480]: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0: if_class 8 protocol 6
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_VENDOR=PNY
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_VENDOR_ENC=PNY\x20\x20\x20\x20\x20
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_VENDOR_ID=154b
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_MODEL=USB_2.0_FD
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_MODEL_ENC=USB\x202.0\x20FD\x20\x20\x20\x20\x20\x20
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_MODEL_ID=007a
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_REVISION=1100
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_SERIAL=PNY_USB_2.0_FD_AA00000000002914-0:0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_SERIAL_SHORT=AA00000000002914
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_TYPE=disk
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_INSTANCE=0:0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_BUS=usb
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_USB_INTERFACES=:080650:
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_USB_INTERFACE_NUM=00
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_USB_DRIVER=usb-storage
Feb  1 17:52:56 iSCSI-SAN udevd[480]: LINK 'disk/by-id/usb-PNY_USB_2.0_FD_AA00000000002914-0:0' /lib/udev/rules.d/60-persistent-storage.rules:44
Feb  1 17:52:56 iSCSI-SAN udevd[480]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-persistent-storage.rules:61
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_PATH=pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: ID_PATH_TAG=pci-0000_00_0b_1-usb-0_8_1_0-scsi-0_0_0_0
Feb  1 17:52:56 iSCSI-SAN udevd[480]: LINK 'disk/by-path/pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0' /lib/udev/rules.d/60-persistent-storage.rules:62
Feb  1 17:52:56 iSCSI-SAN udevd[480]: IMPORT '/sbin/blkid -o udev -p /dev/sdb' /lib/udev/rules.d/60-persistent-storage.rules:74
Feb  1 17:52:56 iSCSI-SAN udevd[481]: seq 1566 running
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552a2670 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552a2670 filled with db file data
Feb  1 17:52:56 iSCSI-SAN udevd[481]: no node name set, will use kernel supplied name 'bsg/0:0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: creating device node '/dev/bsg/0:0:0:0', devnum=252:1, mode=0600, uid=0, gid=0
Feb  1 17:52:56 iSCSI-SAN udevd[481]: preserve file '/dev/bsg/0:0:0:0', because it has correct dev_t
Feb  1 17:52:56 iSCSI-SAN udevd[481]: preserve permissions /dev/bsg/0:0:0:0, 020600, uid=0, gid=0
Feb  1 17:52:56 iSCSI-SAN udevd[481]: preserve already existing symlink '/dev/char/252:1' to '../bsg/0:0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: created empty file '/run/udev/data/c252:1' for '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: passed -1 bytes to netlink monitor 0x7fee552e3e30
Feb  1 17:52:56 iSCSI-SAN udevd[481]: seq 1566 processed with 0
Feb  1 17:52:56 iSCSI-SAN udevd[481]: seq 1567 running
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552ae500 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: no db file to read /run/udev/data/+scsi_device:0:0:0:0: No such file or directory
Feb  1 17:52:56 iSCSI-SAN udevd[481]: passed -1 bytes to netlink monitor 0x7fee552e3e30
Feb  1 17:52:56 iSCSI-SAN udevd[481]: seq 1567 processed with 0
Feb  1 17:52:56 iSCSI-SAN udevd[594]: starting '/sbin/modprobe -bv input:b0003v0D3Dp0040e0100-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw'
Feb  1 17:52:56 iSCSI-SAN udevd[479]: '/sbin/modprobe -bv input:b0003v0D3Dp0040e0100-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw'(err) 'WARNING: Not loading blacklisted module evbug'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: seq 1568 running
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552a2880 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0/0:0:0:0/scsi_disk/0:0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: no db file to read /run/udev/data/+scsi_disk:0:0:0:0: No such file or directory
Feb  1 17:52:56 iSCSI-SAN udevd[481]: passed -1 bytes to netlink monitor 0x7fee552e3e30
Feb  1 17:52:56 iSCSI-SAN udevd[481]: seq 1568 processed with 0
Feb  1 17:52:56 iSCSI-SAN udevd[481]: seq 1569 running
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552a2900 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0/0:0:0:0/scsi_generic/sg1'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552a2900 filled with db file data
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552aebc0 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0/0:0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552a2de0 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552a3570 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552a37c0 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552a2340 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552af9b0 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552aff90 has devpath '/devices/pci0000:00/0000:00:0b.1'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: device 0x7fee552b0560 has devpath '/devices/pci0000:00'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: GROUP 6 /lib/udev/rules.d/50-udev-default.rules:85
Feb  1 17:52:56 iSCSI-SAN udevd[481]: no node name set, will use kernel supplied name 'sg1'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: creating device node '/dev/sg1', devnum=21:1, mode=0660, uid=0, gid=6
Feb  1 17:52:56 iSCSI-SAN udevd[481]: preserve file '/dev/sg1', because it has correct dev_t
Feb  1 17:52:56 iSCSI-SAN udevd[481]: set permissions /dev/sg1, 020660, uid=0, gid=6
Feb  1 17:52:56 iSCSI-SAN udevd[481]: preserve already existing symlink '/dev/char/21:1' to '../sg1'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: created empty file '/run/udev/data/c21:1' for '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host0/target0:0:0/0:0:0:0/scsi_generic/sg1'
Feb  1 17:52:56 iSCSI-SAN udevd[481]: passed -1 bytes to netlink monitor 0x7fee552e3e30
Feb  1 17:52:56 iSCSI-SAN udevd[481]: seq 1569 processed with 0

```

But I think the problem is I'm still trying to do this once the root has mounted.

So I have new questions to look into:
1. What is the deal with [COLOR=#008000]_**/etc/udev/rules.d/10-local.rules** _[/COLOR]and _**[COLOR=#ff0000]/lib/udev/rules.d/50-udev-default.rules [/COLOR]**_processing at the same time?

2. How do I manipulate the /run/udev/rules.d files so that I can do this before root is mounted? (is this the right track, I'm clueless on tmpfs/booting)

[ATTACH=CONFIG]250014[/ATTACH] 
(it seems like if I could manipulate the udevd workers before this point then I'd get the results I want)
Sorry for the blurry picture above, my cameraphone sucks and I'm hypertensive so I shake a lot, here's what it says:
```

udevadm[314]: selinux=0
[COLOR=#ff0000][I]
*unreadable*[/I][/COLOR]ir '/run/udev'
*[COLOR=#ff0000]*unreadable*[/COLOR]*14]: runtime dir '/run/udev'

calling: control
udevadm[314]: calling: control

udevd[00]: udevd message (EXIT) received         *[COLOR=#0000ff](at least I think it's 00 I forget, might have been 80, might have been cheesypoofs for all I can tell)[/COLOR]*

udevd[00]: worker [216] exit

udevd[00]: worker [216] cleaned up

udevd[00]: worker [217] exit

udevd[00]: worker [217] cleaned up

done.
[         0.382998] init: ureadahead mail process (325) terminated with status 5
[         0.642195] Adding 2899852k swap on /dev/sdb5. Priority:-1 extents:1 across: 2899852k
[         9.379433] EXT4-fs (sdb1): re-mounted. .....

```
  
3. Why does the USB stick keep changing host/targets when it's not moving around on the USB connectors? (It jumps from [COLOR=#ff0000]*8:0:0:0*[/COLOR] to *[COLOR=#ff0000]6:0:0:0[/COLOR]* to *[COLOR=#FF0000]3:0:0:0[/COLOR]* and I don't see why when it's always on usb1 1-8 ('/devices/pci0000:00/0000:00:0b.1/usb1/1-8') does anyone know what the deal with that is? It's literally taped to my case inside and I haven't changed the mobo header since I put it there weeks ago.

---

### Post by david144 on 2014-02-03
It seems like I should be doing these udev NAME changes in the initramfs but so far the closest thing I've found discussing this topic in relation to setting up things via user space before root is mounted is this [https://wiki.ubuntu.com/Initramfs](https://wiki.ubuntu.com/Initramfs) however I can't determine from that wiki what I need to do to put the changes I want into an image.

I tried backing up my current images and making a new **[COLOR=#008000]initrd.img-3.8.0-35-generic [/COLOR]**hoping it would incorporate the **[COLOR=#0000ff]10-local.rules [/COLOR]**file that I included in the /run/udev/rules.d and /lib/udev/rules.d (that matched the one in /etc/udev/rules.d) but on reboot I see a ton of new action fly by about devices and paths, however once the kernel is booted and I'm logged in I'm still not getting the USB Flash boot drive as sdz and I have no way to know what was happening (at least that I can see)

Is there a log anywhere of what happens before root mounts?

---

### Post by david144 on 2014-02-05
This is maddening! :(

I can't figure out why this USB stick is being shifted all around, and why it isn't mounted as sda every time...

lspci
```

[EMAIL="san@iSCSI-SAN:~$"]san@iSCSI-SAN:~$[/EMAIL] lspci
00:00.0 Host bridge: NVIDIA Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: NVIDIA Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: NVIDIA Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: NVIDIA Corporation MCP55 SMBus (rev a2)
00:0b.0 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a1)
[COLOR=#008000]**00:0b.1 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a2)**[/COLOR]
00:0d.0 IDE interface: NVIDIA Corporation MCP55 IDE (rev a1)
[COLOR=#FF0000]00:0e.0 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a2)[/COLOR]
00:0f.0 PCI bridge: NVIDIA Corporation MCP55 PCI bridge (rev a2)
00:12.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a2)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
[EMAIL="san@iSCSI-SAN:~$"]san@iSCSI-SAN:~$[/EMAIL]

```

disk/by-path
```

[EMAIL="san@iSCSI-SAN:~$"]san@iSCSI-SAN:~$[/EMAIL] ls /dev/disk/by-path/ -al
total 0
drwxr-xr-x 2 root root 160 Feb  5 15:35 .
drwxr-xr-x 5 root root 100 Feb  5 15:35 ..
lrwxrwxrwx 1 root root   9 Feb  5 15:35 pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0 -> ../../sdd
lrwxrwxrwx 1 root root  10 Feb  5 15:35 pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  10 Feb  5 15:35 pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0-part2 -> ../../sdd2
lrwxrwxrwx 1 root root  10 Feb  5 15:35 pci-0000:00:0b.1-usb-0:8:1.0-scsi-0:0:0:0-part5 -> ../../sdd5
lrwxrwxrwx 1 root root   9 Feb  5 15:35 pci-0000:00:0e.0-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root   9 Feb  5 15:35 pci-0000:00:0e.1-scsi-0:0:0:0 -> ../../sdc
[EMAIL="san@iSCSI-SAN:~$"]san@iSCSI-SAN:~$[/EMAIL]

```
Where the heck is sdb even right now!?!???!?  

ROFL, it's showing up in my system just apparently not by path...
```

[EMAIL="san@iSCSI-SAN:~$"]san@iSCSI-SAN:~$[/EMAIL] ls /dev/disk/by-id/ -al
total 0
drwxr-xr-x 2 root root 300 Feb  5 15:35 .
drwxr-xr-x 5 root root 100 Feb  5 15:35 ..
lrwxrwxrwx 1 root root   9 Feb  5 15:35 ata-ST4000DM000-1F2168_W300AGRR -> ../../sdb
lrwxrwxrwx 1 root root   9 Feb  5 15:35 ata-ST4000DM000-1F2168_Z30053FT -> ../../sdc
lrwxrwxrwx 1 root root   9 Feb  5 15:35 ata-ST4000DM000-1F2168_Z3005ZQQ -> ../../sda
lrwxrwxrwx 1 root root   9 Feb  5 15:35 scsi-SATA_ST4000DM000-1F2_W300AGRR -> ../../sdb
lrwxrwxrwx 1 root root   9 Feb  5 15:35 scsi-SATA_ST4000DM000-1F2_Z30053FT -> ../../sdc
lrwxrwxrwx 1 root root   9 Feb  5 15:35 scsi-SATA_ST4000DM000-1F2_Z3005ZQQ -> ../../sda
lrwxrwxrwx 1 root root   9 Feb  5 15:35 usb-PNY_USB_2.0_FD_AA00000000002914-0:0 -> ../../sdd
lrwxrwxrwx 1 root root  10 Feb  5 15:35 usb-PNY_USB_2.0_FD_AA00000000002914-0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  10 Feb  5 15:35 usb-PNY_USB_2.0_FD_AA00000000002914-0:0-part2 -> ../../sdd2
lrwxrwxrwx 1 root root  10 Feb  5 15:35 usb-PNY_USB_2.0_FD_AA00000000002914-0:0-part5 -> ../../sdd5
lrwxrwxrwx 1 root root   9 Feb  5 15:35 wwn-0x5000c5004fa01eab -> ../../sdc
lrwxrwxrwx 1 root root   9 Feb  5 15:35 wwn-0x5000c5004fadea5d -> ../../sda
lrwxrwxrwx 1 root root   9 Feb  5 15:35 wwn-0x5000c500609ec3a2 -> ../../sdb
[EMAIL="san@iSCSI-SAN:~$"]san@iSCSI-SAN:~$[/EMAIL]

```


grub device.map: failed
udev: failed


I'm down to wondering is there even a way to manipulate the sysfs? I started reading about kobjects and my brain turned to pudding.

Hoping someone can help, I'm too old to understand this version kernel with all these crazy bootloaders, preboot and ramdisk based systems, and I'm much too poor to afford windows 2008 storage edition (or would love to do 2012 since it has built in NIC teaming)

---

### Post by david144 on 2014-02-08
Would like to send many thanks out to Greg Kroah-Hartman, for taking time to respond to me regarding this issue.

Sadly it seems this is just impossible, see Greg's response here:
[http://www.spinics.net/lists/hotplug/msg05861.html](http://www.spinics.net/lists/hotplug/msg05861.html)

Going to build my mdadm based on the by-id's and degrade the array to see if it will notify me that way but I'm guessing it will still send the device name and I'll have to login to do any troubleshooting before pulling drives :(

Marking for Admin to close thread.

---

### Post by bapoumba on 2014-02-08
Closed as requested. If you wish to have it opened again, please use the same report button :)

---

