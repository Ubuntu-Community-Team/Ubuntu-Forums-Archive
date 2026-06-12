---
title: "Ubuntu 12.04 repeatedly trying to mount a StarTech KVM USB Dongle (bad performance)"
date: 2013-09-09
forum: Hardware
---

### Post by Sniperm4n on 2013-09-09
Hi everyone,

I'm dealing with an odd issue where Ubuntu 12.04 Server LTS 64-bit is repeatedly attempting to mount a StarTech KVM USB dongle that's attached via VGA and USB. I've already contacted StarTech's technical support team and they are pretty much worthless when it comes to Linux support (they know nothing about Debian/Ubuntu, only RedHat). The moment I connect the USB portion of the dongle to the server, I get spammed by the following (so much so the console is completely unusable):

Sep  9 16:10:04 nseng1 kernel: [6289822.375627] sd 19:0:0:0: [sdc]
Sep  9 16:10:04 nseng1 kernel: [6289822.375629] Sense Key : Not Ready [current]
Sep  9 16:10:04 nseng1 kernel: [6289822.375634] sd 19:0:0:0: [sdc]
Sep  9 16:10:04 nseng1 kernel: [6289822.375637] Add. Sense: Logical unit not ready, manual intervention required
Sep  9 16:10:04 nseng1 kernel: [6289822.381618] sd 19:0:0:0: [sdc] Test WP failed, assume Write Enabled
Sep  9 16:10:04 nseng1 kernel: [6289822.387616] sd 19:0:0:0: [sdc] Cache data unavailable
Sep  9 16:10:04 nseng1 kernel: [6289822.387621] sd 19:0:0:0: [sdc] Assuming drive cache: write through
Sep  9 16:10:04 nseng1 kernel: [6289822.432620] sd 19:0:0:0: [sdc] READ CAPACITY failed
Sep  9 16:10:04 nseng1 kernel: [6289822.432625] sd 19:0:0:0: [sdc]
Sep  9 16:10:04 nseng1 kernel: [6289822.432628] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  9 16:10:04 nseng1 kernel: [6289822.432631] sd 19:0:0:0: [sdc]
Sep  9 16:10:04 nseng1 kernel: [6289822.432634] Sense Key : Not Ready [current]
Sep  9 16:10:04 nseng1 kernel: [6289822.432638] sd 19:0:0:0: [sdc]
Sep  9 16:10:04 nseng1 kernel: [6289822.432641] Add. Sense: Logical unit not ready, manual intervention required
Sep  9 16:10:04 nseng1 kernel: [6289822.438619] sd 19:0:0:0: [sdc] Test WP failed, assume Write Enabled
Sep  9 16:10:04 nseng1 kernel: [6289822.444620] sd 19:0:0:0: [sdc] Cache data unavailable
Sep  9 16:10:04 nseng1 kernel: [6289822.444625] sd 19:0:0:0: [sdc] Assuming drive cache: write through
Sep  9 16:10:04 nseng1 kernel: [6289822.489624] sd 19:0:0:0: [sdc] READ CAPACITY failed

I've been researching how to write udev rules to block this USB device for several hours now, and am completely stumped. Here is some additional information I captured using the command "udevadm info -a -p /sys/block/sdc":

looking at device '/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.2/host19/target19:0:0/19:0:0:0/block/sdc':
    KERNEL=="sdc"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{ro}=="0"
    ATTR{size}=="0"
    ATTR{stat}=="       0        0        0        0        0        0        0        0        0        0        0"
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

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.2/host19/target19:0:0/19:0:0:0':
    KERNELS=="19:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{rev}=="3.0a"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="5"
    ATTRS{model}=="Emulated Disk   "
    ATTRS{state}=="running"
    ATTRS{queue_type}=="none"
    ATTRS{iodone_cnt}=="0x3cd2"
    ATTRS{iorequest_cnt}=="0x3cd3"
    ATTRS{timeout}=="30"
    ATTRS{evt_media_change}=="0"
    ATTRS{max_sectors}=="240"
    ATTRS{ioerr_cnt}=="0x3cd1"
    ATTRS{queue_depth}=="1"
    ATTRS{vendor}=="Generic "
    ATTRS{device_blocked}=="0"
    ATTRS{iocounterbits}=="32"

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.2/host19/target19:0:0':
    KERNELS=="target19:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.2/host19':
    KERNELS=="host19"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.2':
    KERNELS=="3-1:1.2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="02"
    ATTRS{interface}=="Floppy"

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb3/3-1':
    KERNELS=="3-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="1"
    ATTRS{idVendor}=="9999"
    ATTRS{speed}=="12"
    ATTRS{bNumInterfaces}==" 3"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="16"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}==" 96mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="0"
    ATTRS{bcdDevice}=="0100"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{serial}=="000013f23617"
    ATTRS{version}==" 2.00"
    ATTRS{urbnum}=="86530"
    ATTRS{manufacturer}=="Generic"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="0120"
    ATTRS{bDeviceClass}=="00"
    ATTRS{product}=="CAT5 Adapter"

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="0"
    ATTRS{idVendor}=="1d6b"
    ATTRS{speed}=="12"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{authorized_default}=="1"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="1"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="2"
    ATTRS{bcdDevice}=="0305"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{serial}=="0000:00:1d.1"
    ATTRS{version}==" 1.10"
    ATTRS{urbnum}=="287"
    ATTRS{manufacturer}=="Linux 3.5.0-31-generic uhci_hcd"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="0001"
    ATTRS{bDeviceClass}=="09"
    ATTRS{product}=="UHCI Host Controller"

  looking at parent device '/devices/pci0000:00/0000:00:1d.1':
    KERNELS=="0000:00:1d.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{irq}=="10"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x0c0300"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000001"
    ATTRS{device}=="0x2689"
    ATTRS{msi_bus}==""
    ATTRS{local_cpulist}=="0"
    ATTRS{vendor}=="0x8086"
    ATTRS{subsystem_device}=="0x01b2"
    ATTRS{numa_node}=="-1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

Here is my most recent attempt at creating a new rule in /etc/udev/rules.d:
username@hostname:/etc/udev/rules.d$ cat 10-startechkvm.rules
SUBSYSTEM=="block", ATTR{size}=="0", ATTRS{model}=="Emulated Disk   ", OPTIONS=="ignore_device"

I then restarted the udev service and I'm still getting spammed on the console. This is occurring on both of my DNS/DHCP servers, and makes them impossible to use (I have to disconnect the USB cable and restart the udev service in order for them to be usable, otherwise I can't see what I'm typing on the console due to the exorbitant amount of spam). Does anyone have any input as to what I'm doing wrong?

Much thanks,
-Snipe

---

