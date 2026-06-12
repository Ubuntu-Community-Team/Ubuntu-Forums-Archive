---
title: "usb stick not mountable"
date: 2013-12-16
forum: Hardware
---

### Post by Sinnlosvoll on 2013-12-16
Hey there,

my parents did somehow crash their 32gig usb drive somehow using their tv. Weird stuff :D

Anyhow i tried to acces the usb-drive on ubuntu but it isn't detected by fdisk so it is not mounted. 

it does show up under
```
lsusb 
```
though.
the
```
dmesg
```
 looks like this:

```
[SIZE=1][FONT=arial][COLOR=#333333][ 1077.228074] usb 1-1: new high-speed USB device number 8 using ehci-pci[/COLOR]
[COLOR=#333333][ 1077.365415] usb 1-1: New USB device found, idVendor=13fe, idProduct=4100[/COLOR]
[COLOR=#333333][ 1077.365423] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3[/COLOR]
[COLOR=#333333][ 1077.365428] usb 1-1: Product: USB DISK 2.0[/COLOR]
[COLOR=#333333][ 1077.365432] usb 1-1: Manufacturer:         [/COLOR]
[COLOR=#333333][ 1077.365436] usb 1-1: SerialNumber: 07052BFE1716EB99[/COLOR]
[COLOR=#333333][ 1077.365845] usb-storage 1-1:1.0: USB Mass Storage device detected[/COLOR]
[COLOR=#333333][ 1077.366462] scsi12 : usb-storage 1-1:1.0[/COLOR]
[COLOR=#333333][ 1078.452082] scsi 12:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 4[/COLOR]
[COLOR=#333333][ 1078.452544] sd 12:0:0:0: Attached scsi generic sg2 type 0[/COLOR]
[COLOR=#333333][ 1078.525246] sd 12:0:0:0: [sdb] Attached SCSI removable disk[/COLOR][/FONT][/SIZE]

```

Is is possible to mount the stick somehow so i can reformat it?

---

### Post by sudodus on 2013-12-16
Welcome to the Ubuntu Forums :-)

If the stick is not recognized at all by fdisk it might be severely damaged. Did you try

```
sudo fdisk -lu
```

If it is shown at least as a device **/dev/sdb** or **/dev/sdc** ... there is hope. Then you can probably create new partitions with ***gparted***.

You can also try

```
sudo parted -l
``` which should give about the same information, but also information if there is a GUID partition table, GPT, instead of a classic MSDOS partition table.

---

### Post by Sinnlosvoll on 2013-12-16
Yeah, thanks for the welcome :)

It does not appear either when using 
@root
> fdisk -lu
nor does it in 
> parted -l

So i should assume that the stick is busted?

---

### Post by sudodus on 2013-12-16
I am afraid it is. The tools, that I know need to have the device recognized like that.

You should try in another computer, because sometimes a particular USB device and a particular computer (USB system) cannot cooperate.

The flash hardware has limited and unpredictable lifetime, it happens quite often that a pendrive is damaged or destroyed, while some of them last for years even with quite heavy usage.

---

### Post by Sinnlosvoll on 2013-12-16
Okay, then I know what they'll be getting for christmas :D

Thanks though, great support here, I'll give you that.

---

