---
title: "External hard drive isn't recognized."
date: 2010-10-07
forum: Hardware
---

### Post by rhemode on 2010-10-07
Dear All:

I'm relatively new to Ubuntu/Linux and don't have a good conceptual understanding of how it interfaces with its various components and peripherals; please bear with me.

I have a Lacie 1TB external hard which I connect to the computer via USB. Several days ago I installed Ubuntu 10.04 on my desktop computer (Gateway DX4720-03). It is currently the only operating system on this computer. I had to use the ubuntu 10.04 alternate installer amd64 disk to get things to work properly, but that's hopefully another story.

When I plug the Lacie drive into any of the various USB ports there is no indication that the computer even knows the drive is there.

When I plug my Seagate 250GB drive into any USB port it is, however, automatically mounted and visible in the Computer folder.

I also have a laptop with a Windows Vista/Ubuntu 10.04 dual boot that can recognize both drives, in both Windows and Ubuntu.

I searched the forums for similar problems, but nothing seemed to help my situation.

Let me know if there's any technical info/diagnostic results I should post to help specify the problem.

Thanks in advance!

---

### Post by srs5694 on 2010-10-08
Try the following:


[list=1]
[*]Unplug the disk, if it's currently plugged in.
[*]Open a text-mode command window (terminal).
[*]Type "dmesg | tail" in that window.
[*]Type "ls /dev/sd?".
[*]Plug the disk in and wait a few seconds (20 seconds should be plenty).
[*]Type "dmesg | tail -n 20" and compare the output with the previous dmesg output. New lines are kernel messages related to plugging in the new disk. Post them here.
[*]Type "ls /dev/sd?". If a new device appears, that device is associated with the disk.
[*]If there's a new /dev/sd? device (say, /dev/sdb), type "sudo fdisk -l /dev/sdb" (changing /dev/sdb, if appropriate, for the new device) and post the results here, ideally between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. Also post the output of "ls /dev/sdb*", adjusting the device appropriately.
[/list]


The information you post will provide necessary diagnostic information. These procedures will not make the disk accessible by themselves, though.

---

### Post by ScrewBaxster on 2010-10-09
> **srs5694 said:**
> Try the following:


[list=1]
[*]Unplug the disk, if it's currently plugged in.
[*]Open a text-mode command window (terminal).
[*]Type "dmesg | tail" in that window.
[*]Type "ls /dev/sd?".
[*]Plug the disk in and wait a few seconds (20 seconds should be plenty).
[*]Type "dmesg | tail -n 20" and compare the output with the previous dmesg output. New lines are kernel messages related to plugging in the new disk. Post them here.
[*]Type "ls /dev/sd?". If a new device appears, that device is associated with the disk.
[*]If there's a new /dev/sd? device (say, /dev/sdb), type "sudo fdisk -l /dev/sdb" (changing /dev/sdb, if appropriate, for the new device) and post the results here, ideally between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. Also post the output of "ls /dev/sdb*", adjusting the device appropriately.
[/list]


The information you post will provide necessary diagnostic information. These procedures will not make the disk accessible by themselves, though.


--

I am having the same problem. When I plug the hdd into this computer (10.04), it is not detected--not even in disk utility. I plug into Windows and a laptop with ubuntu 10.04 and it works fine. 

I tried the steps above and these are the results:

:~$ dmesg |tail
[  245.194952] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  255.892033] wlan1: no IPv6 routers present
[  275.180360] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  275.315546] usb 1-5: configuration #1 chosen from 1 choice
[  292.156957] usb 1-5: USB disconnect, address 4
[  453.730077] lo: Disabled Privacy Extensions
[ 1300.120100] lo: Disabled Privacy Extensions
[ 1312.364051] usb 1-5: new high speed USB device using ehci_hcd and address 5
[ 1312.500594] usb 1-5: configuration #1 chosen from 1 choice
[ 3564.992783] usb 1-5: USB disconnect, address 5

:~$ ls /dev/sd?
/dev/sda  /dev/sdb

:~$ dmesg |tail -n20
[   13.639449] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   13.639453] vboxdrv: Found 1 processor cores.
[   13.641892] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   13.641896] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[   19.791372] hda-intel: IRQ timing workaround is activated for card #2. Suggest a bigger bdl_pos_adj.
[   22.440020] eth0: no IPv6 routers present
[   77.584027] Clocksource tsc unstable (delta = -250010077 ns)
[  244.940320] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  245.194952] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  255.892033] wlan1: no IPv6 routers present
[  275.180360] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  275.315546] usb 1-5: configuration #1 chosen from 1 choice
[  292.156957] usb 1-5: USB disconnect, address 4
[  453.730077] lo: Disabled Privacy Extensions
[ 1300.120100] lo: Disabled Privacy Extensions
[ 1312.364051] usb 1-5: new high speed USB device using ehci_hcd and address 5
[ 1312.500594] usb 1-5: configuration #1 chosen from 1 choice
[ 3564.992783] usb 1-5: USB disconnect, address 5
[ 3605.580056] usb 1-5: new high speed USB device using ehci_hcd and address 6
[ 3605.716861] usb 1-5: configuration #1 chosen from 1 choice

:~$ ls /dev/sd?
/dev/sda  /dev/sdb

----

I have tried switching it USB ports, and out of 5 attempts, it works once. 

Suggestions?

Thanks for all the help. :guitar:

---

### Post by srs5694 on 2010-10-09
ScrewBaxster, it seems that your system is recognizing that something's being attached, but it's not recognizing that it's a disk device. Perhaps the device is damaged, or maybe it's weird enough that Linux's standard USB flash drive handling features can't cope with it. My only suggestion for a solution is to upgrade your kernel, but if you're keeping up with system updates, the only way to get something more recent would be to compile it yourself, perhaps with any patches you can find related to USB disk devices. Unless you've done this before or are technically motivated, I'd be reluctant to suggest doing this.

You might be able to find slightly more information with lsusb. With the device disconnected, type "lsusb," then plug the device in, wait a few seconds, and type "lsusb" again. Compare the two outputs; the new entry refers to the USB flash drive. You can then type "sudo lsusb -v -i busnum:devicenum", where busnum and devicenum are the bus and device numbers for the device in the earlier lsusb output. This will produce lots of technical details on the device. You can post them here, but I'm not sure if it will really produce anything useful for creating a quick fix. (There's a chance that a new udev rule will get it working; but it's also possible that a kernel modification would be required.)

---

### Post by ScrewBaxster on 2010-10-09
> **srs5694 said:**
> ScrewBaxster, it seems that your system is recognizing that something's being attached, but it's not recognizing that it's a disk device. Perhaps the device is damaged, or maybe it's weird enough that Linux's standard USB flash drive handling features can't cope with it. My only suggestion for a solution is to upgrade your kernel, but if you're keeping up with system updates, the only way to get something more recent would be to compile it yourself, perhaps with any patches you can find related to USB disk devices. Unless you've done this before or are technically motivated, I'd be reluctant to suggest doing this.

You might be able to find slightly more information with lsusb. With the device disconnected, type "lsusb," then plug the device in, wait a few seconds, and type "lsusb" again. Compare the two outputs; the new entry refers to the USB flash drive. You can then type "sudo lsusb -v -i busnum:devicenum", where busnum and devicenum are the bus and device numbers for the device in the earlier lsusb output. This will produce lots of technical details on the device. You can post them here, but I'm not sure if it will really produce anything useful for creating a quick fix. (There's a chance that a new udev rule will get it working; but it's also possible that a kernel modification would be required.)

---


srs5694, thanks for the help.:) 
I know the drive works fine because I connected it to a laptop running ubuntu 10.04 as well and it is automounted as it regularly did on this pc. I connect it to Windoz and it is also autoplayed there. I must say this weird behavior started after the last update--couple of days ago. I thought of undoing those changes but Synaptic warned me of provoking system unstability by removing such packages. 

These are the results for the commands suggested: 


:~$ lsusb
Bus 002 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 002: ID 046d:c313 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


:~$ lsusb
Bus 002 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 002: ID 046d:c313 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The command "lsusb" with "-i" was invalid so I assumed it was "-s".

:~$ sudo lsusb -v -s 001:007

Bus 001 Device 007: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04b4 Cypress Semiconductor Corp.
  idProduct          0x6830 CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
  bcdDevice            0.01
  iManufacturer          56 Cypress Semiconductor
  iProduct               78 USB2.0 Storage Device
  iSerial               100 DEF107727402
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

I must say this installation is just a week old. I had to reinstall it cuz I messed up something in the previous installation :lolflag:

---

