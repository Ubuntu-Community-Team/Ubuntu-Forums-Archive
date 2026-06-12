---
title: "Ubuntu can't see my WD passport external drive"
date: 2009-10-02
forum: Hardware
---

### Post by ulibumpa on 2009-10-02
Hi all :)
 
I'm new to linux/ubuntu and struggling a bit to get everything working properly.
 
I've got ubuntu 9.04 installed on a Dell Inspiron 5100 laptop but it wont recognise my WD120 passport connected with USB. Nothing is seen on the desktop or in places. I've tried to connect while up and running as well as before booting - nothing. It works fine on other computers (windows and mac). There is no on/off button but the light turns on and it starts whirling up when connected.
 
:confused:
 
Please help 
 
Thanks

---

### Post by kgas on 2009-10-02
Can you post the out put of lsub and demsg before and after connection the USB drive? Also check with fdisk -l for your device get recognised.

---

### Post by ulibumpa on 2009-10-02
Thanks kgas
 
Sorry but I have no idea what lsub or demsg means :( please explain what I have to do.
I did read something about fdisk -l somewhere here and wacked it in the terminal (never used terminal commands before..this is all very new to me) and got this:
 
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e
 
Device Boot Start End Blocks Id System
/dev/sda1 * 1 4659 37423386 83 Linux
/dev/sda2 4660 4864 1646662+ 5 Extended
/dev/sda5 4660 4864 1646631 82 Linux swap / Solaris 
 
:confused: I can't tell if it's there or not...is it the "extended"?

---

### Post by BraedenNaylor on 2009-10-02
In terminal put:
```
lsusb [return]
```
```
demsg [return]
```
```
fdisk -l [return]
```
as seperate commands. copy and paste output here.

---

### Post by ulibumpa on 2009-10-02
fdisk -l output as previous message
 
sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 079b:007e Sagem 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
sudo demsg
sudo: demsg: command not found
 
Not really sure what this "sudo" is but it had to be there to get any outputs
 
("Sagem" is my internet modem)
 
edit: this is after the drive is connected. I'll post again with before connected...just a sec...

---

### Post by ulibumpa on 2009-10-02
Ok, sorry for the mess. Here are all the outputs:
 
**Before connecting:**
 
sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 079b:007e Sagem 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
sudo demsg
sudo: demsg: command not found
 
sudo fdisk -l
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e
 
Device Boot Start End Blocks Id System
/dev/sda1 * 1 4659 37423386 83 Linux
/dev/sda2 4660 4864 1646662+ 5 Extended
/dev/sda5 4660 4864 1646631 82 Linux swap / Solaris
 
**And after connecting:**
 
sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 079b:007e Sagem 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
sudo demsg
sudo: demsg: command not found
 
sudo fdisk -l
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e
 
Device Boot Start End Blocks Id System
/dev/sda1 * 1 4659 37423386 83 Linux
/dev/sda2 4660 4864 1646662+ 5 Extended
/dev/sda5 4660 4864 1646631 82 Linux swap / Solaris 
 
Obviously not there, huh :(
 
What can I do?

---

### Post by kgas on 2009-10-03
After inserting your

 usb drive in terminal type

dmesg | tail -4
you will get the follwing out put if the drive is detected

usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.

for sudo fdisk -l command if your device is detected correctly

you will get
Disk identifier: 0x93fca0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7868     2014192    e  W95 FAT16 (LBA)

for the usb drive (here the drive uses FAT16 file system)

From your output it seems that the drive is not detected. If the drive is of NTFS file system then you may have to install the ntfs tools thro' your synaptic manager.

---

### Post by ulibumpa on 2009-10-03
The drive has FAT32 format...
 
Now with the right spelling of commands I get this:
 
dmesg | tail -4
[  294.684462] usb 2-1: configuration #2 chosen from 2 choices
[  294.790647] eth1: register 'cdc_ether' at usb-0000:00:1d.0-1, CDC Ethernet Device, 00:25:69:59:7c:34
[  294.791102] usbcore: registered new interface driver cdc_ether
[  309.152076] eth1: no IPv6 routers present

But without the "tail -4" I got a MASSIVE output including this bit  
 
dmesg
.........
[  152.044075] usb 1-1: new high speed USB device using ehci_hcd and address 6
[  152.112283] hub 1-0:1.0: unable to enumerate USB device on port 1
[  153.515047] hub 1-0:1.0: [B]over-current change on port 1
[/B]........
 
:confused: WTF?

---

### Post by kgas on 2009-10-05
There is a power surge in your usb hub and blocked for further processing.Try to use the hub with an external power adapter or remove any other devices connected and try only with your usb drive.

---

### Post by ulibumpa on 2009-10-08
Thanks
I haven't got a hub w external power :( The main point with this one was mobility...
I guess I'll have to find another drive.

---

