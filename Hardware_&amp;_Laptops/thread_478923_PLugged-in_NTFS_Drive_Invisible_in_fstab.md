---
title: "PLugged-in NTFS Drive Invisible in fstab"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by BoSchafers on 2007-06-19
I have a little 80 gig laptop hard drive which is mounted in a USB converter casing. I recently reformatted the drive from FAT32 to NTSF using XP's Disk Management utility. After that it's no longer seen at all by Feisty: not by doing fdisk -l nor by running  Gparted, it's entirely invisible to the system when plugged in.

-The drive works as expected on Windows XP. 
-Feisty has the latest pmount and NTFS-3g installed. 

Feisty can mount my usb stick which is formatted in NTFS, but this mentioned usb drive is *completely* non-existent to the system.

Why can the drive not be seen? It's like it's not there, how do I make it visible to Ubuntu so it can either be mounted or re-formatted?

TIA
Bo

---

### Post by BoSchafers on 2007-06-19
Someone elsewhere suggested appending ircpoll or noapic to kernal line in grub's menu.lst 

It was a wide shot and had no effect.

Bo

---

### Post by logos34 on 2007-06-19
so

sudo fdisk -l (letter'L')

does not show the disk?

what about

sudo lsusb

sudo lshw

?

And it works fine in windows.  And your ntfs-formatted usb stick shows up.  hmm.

I'm sure you've tried all the obvious things like hot-plugging it, different usb slots, etc.

---

### Post by BoSchafers on 2007-06-20
Hi logos34!

> **logos34 said:**
> 

what about: sudo lsusb


The device shows as:

[COLOR="Navy"]Bus 001 Device 006: ID 048d:8903 Integrated Technology Express, Inc. [/COLOR]

> **logos34 said:**
> 
sudo lshw

[COLOR="Blue"]*-usb
description: Mass storage device
product: USB TO IDE
vendor: ITE TECH. INC.
physical id: 6
bus info: usb@1:6
logical name: scsi7
version: 2.00
serial: 064911000391
capabilities: usb-2.00 scsi emulated
configuration: driver=usb-storage maxpower=100mA speed=480.0MB/s

*-disk UNCLAIMED
description: SCSI Disk
physical id: 0.0.0
bus info: scsi@7:0.0.0[/COLOR]

So there is a USB to IDE device in the slot, name of 'scsi7' but the disk is 'unclaimed'? :o 

There seem to be some clues there, though I'm not versed enough in hardware to me sense of it :(

Anyone have an idea of how to CLAIM it????

Thanks,
Bo

---

### Post by logos34 on 2007-06-20
seems the module for that device is not being detected by linux.

from
**[http://ezix.org/project/wiki/HardwareLiSter](http://ezix.org/project/wiki/HardwareLiSter)**:

> How to interpret lshw's output ¶

lshw displays nodes with attributes in a tree-like structure (that can be in indented plain text form, HTML, XML or graphically displayed in the GUI). Each node has its individual status: it be CLAIMED (potentially usable) or [COLOR="Red"]UNCLAIMED (no driver has been detected for this node)[/COLOR], ENABLED (this device is supported and can be used) or DISABLED (this device is supported but has been disabled):

    * a node is marked as CLAIMED if a driver (usually a kernel module or a driver within the monolithic kernel) has been loaded for it
    [COLOR="Red"]* a node is marked as UNCLAIMED if no specific support for it has been loaded (or lshw has been unable to identify the driver)[/COLOR]
    * a node is marked as ENABLED if a driver has been loaded for it and is fully functional
    * a node is marked as DISABLED if the node has been disabled by a configuration, some hardware failure, etc. 

Each node can contain sub-nodes and can have a number of attributes, capabilities, resources and configuration values. 


> Known problems/limitations ¶

    * on x86, lshw needs to be run as root to be able to access DMI information from the BIOS
    * running lshw as a non-root user usually gives much less detailed information
    [COLOR="Red"]* lshw is sometimes confused about where to connect emulated SCSI devices (like USB storage devices, IEEE1394 disks and SCSI-over-IDE CD writers). This will hopefully be fixed on version 2.6 kernels by using sysfs.[/COLOR]
    * Active tickets against lshw

---

### Post by logos34 on 2007-06-20
'usb-storage' is the driver.  should be loaded because the usb stick uses it too (could be wrong on that)

check output of 
**lsmod**

If not there, try
**sudo modprobe usb-storage**

---

### Post by BoSchafers on 2007-06-20
> **logos34 said:**
> 'usb-storage' is the driver.  should be loaded because the usb stick uses it too (could be wrong on that)

check output of 
lsmod

It's there....listed

[COLOR="Navy"]usb_storage            72256  2[/COLOR]

THANKS for all your valued assistance!


:( So it sounds like the info you've posted is saying that my particular USB to IDE device is not supported by the current (June 2007) Linux kernal?  

But...but....this device was working when it had a Fat32 file system. 

For the benefit of others, my USB-IDE device is 

Welland
2.5" External 
Sub-system
made by
Integrated Technology Express

It's a convenient, little padded case, which is self-powered by the USB cable, it works very well in Linux just don't fromat it to NTFS. You'll not be able to access it again to format it back to another file system in Gparted,

At least this is how I understand it now due to logos34's help.

Bo

---

### Post by logos34 on 2007-06-20
we'er running 2.6.x kernel, so it should have been fixed by now.

to be honest I'm not sure what the deal is here...It may be lshw (and the operating system) is just unable to ID the driver, not necessarily that the driver is not loaded (if in fact it is 'usb-storage' and not some other then it may be just an ID prob).  But if it was working in linux when formatted as FAT32, and it still works in windows then maybe it's not a hardware issue at all.  

Perhaps try setting a volume name using **ntfslabel**...maybe that'll help it being recognized. 

you'll need the package ntfsprogs

Follow the instructions in the 'How to Label' section for NTFS here:
[COLOR="Blue"]http://doc.gwos.org/index.php/Understanding_fstab[/COLOR]

---

### Post by BoSchafers on 2007-06-20
> **logos34 said:**
> 
Perhaps try setting a volume name using **ntfslabel**...maybe that'll help it being recognized. 


Hi logos34,

I did install ntfsprogs and tried to change the label, I managed changing it on the USB stick (the one that works), however I was unable to find the name of the device I'm actually trying to label i.e. the unrecognosed USB hard drive. After all it's not a device, its 'Unclaimed'. If don't have the name of the device then ntfslabel cannot work with it.

Catch 22...
Bo

---

