---
title: "USB2  slows down to 1.1 after reformat??"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by ovron on 2007-03-31
thanks anyway but the problem was resolved... just a simple reload of the kernel modules did it... why didn't i think of that...

to fix: 

sudo rmmod ohci_hcd
sudo rmmod ehci_hcd
sudo modprobe ehci_hcd
sudo modprobe ohci_hcd





Hello Everyone,

I jut switched to ubuntu a few months ago from windows and i am very happy with it, had a few problems getting beryl working with ATI cards but whatever. my latest problem comes up with my just purchased USB 2.5" sata drive. I first used it a few days ago and it worked great, usb 2.0 with high transfer rates. about an hour ago there was a crash(caused by beryl again) that corrupted some data on the drive so i decided to reformat (i didn't bother with a backup because i had almost nothing of import on it).

the corruption was kinda odd in the fact that the drive would only read as read-only while in ubuntu so i booted into windows and reformatted it, then came back to Linux and formated again as fat32 to get around the ntfs-3g auto mount issue with edgy. it formatted fine and reported 150GB like it should but the write speed is usb 1.1 or 12Mbits/sec... i don't know what i am missing but i think something went wrong with the format. stats and data are listed below for reference.


ct@loki:/dev$ sudo lshw | grep usb
Password:
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
        *-usb:0
           *-usbhost
                bus info: usb@2
                logical name: usb2
                capabilities: usb-1.10
              *-usb:0
                   bus info: usb@2:1
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=2mA speed=12.0MB/s
              *-usb:1
                   bus info: usb@2:3
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
        *-usb:1
           *-usbhost
                bus info: usb@3
                logical name: usb3
                capabilities: usb-1.10
        *-usb:2
           *-usbhost
                bus info: usb@1
                logical name: usb1
                capabilities: usb-2.00

ct@loki:/dev$ sudo mount | grep sda1
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
 
ct@loki:/dev$ dmesg | grep usb
[17179579.532000] usbcore: registered new driver usbfs
[17179579.532000] usbcore: registered new driver hub
[17179579.748000] usb usb1: configuration #1 chosen from 1 choice
[17179580.176000] usb usb2: configuration #1 chosen from 1 choice
[17179580.600000] usb usb3: configuration #1 chosen from 1 choice
[17179580.800000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[17179580.996000] usb 2-1: not running at top speed; connect to a high speed hub
[17179581.008000] usb 2-1: configuration #1 chosen from 1 choice
[17179581.320000] usb 2-3: new low speed USB device using ohci_hcd and address 3
[17179581.528000] usb 2-3: configuration #1 chosen from 1 choice
[17179595.104000] usbcore: registered new driver libusual
[17179595.124000] usbcore: registered new driver hiddev
[17179595.128000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-3
[17179595.128000] usbcore: registered new driver usbhid
[17179595.128000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179595.296000] usbcore: registered new driver usb-storage
[17179595.296000] usb-storage: device found at 2
[17179595.296000] usb-storage: waiting for device to settle before scanning
[17179600.296000] usb-storage: device scan complete

ct@loki:/dev$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c03d Logitech, Inc. 
Bus 002 Device 002: ID 152d:2338  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

hardware:
drive: 160G|WD 5K 8M SATA WD1600BEVS
external case: BYTECC BT-280SATA COMBO
computer: Toshiba satalite a75-s1253

the strange thing is that before the format everything was working fine...

---

