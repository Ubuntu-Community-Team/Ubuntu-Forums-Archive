---
title: "NVME and SATA dual-boot how to"
date: 2021-05-23
forum: Hardware
---

### Post by vidtek on 2021-05-23
Many struggle with this issue.  Motherboard manufacturers give options to disable sata drives, often on an individual basis.

As for as I have been able to ascertain NO manufacturer gives that same option for NVME (M2) motherboard connectors.

Here is a simple work-around for others like me who clone drives and want to boot into a sata drive on occasion instead of the NVME drive.

[https://ubuntuforums.org/showthread.php?t=2462260&p=14039563#post14039563]("https://ubuntuforums.org/showthread.php?t=2462260&p=14039563#post14039563")

As you will see, in certain configurations you can also boot windows 10 from a usb attached drive.

Cheers Tony.

---

### Post by tea for one on 2021-05-23
> **vidtek said:**
> Many struggle with this issue.  Motherboard manufacturers give options to disable sata drives, often on an individual basis.

As for as I have been able to ascertain NO manufacturer gives that same option for NVME (M2) motherboard connectors.

To be honest, I had the opposite opinion about desktop motherboards which allow more than one drive to be connected.
I thought that isolating each drive was a fairly widespread feature.
Although, now, I reckon the way each vendor implements the UEFI firmware is more of a consideration.

My weapon of choice at the moment is an Intel NUC8i3BEH approx 2 years old.
Internally, it contains a SATA port for a 2.5" SSD and a M.2 slot for a M.2 drive [COLOR="#0000FF"]or[/COLOR] NVME drive.
I have installed a Sandisk 2.5" SSD and a Kingston NVME.

The UEFI firmware allows me to independently isolate, de-activate or disable either drive. 
I can also disable both drives and use an external USB stick or drive.
Lastly, I can run an OS externally via a NVME drive in a suitable enclosure. (connected to the USB C port on the back panel).

I would doubt that Intel are alone in allowing this facility.

---

### Post by vidtek on 2022-03-11
> **tea for one said:**
> To be honest, I had the opposite opinion about desktop motherboards which allow more than one drive to be connected.
I thought that isolating each drive was a fairly widespread feature.
Although, now, I reckon the way each vendor implements the UEFI firmware is more of a consideration.

My weapon of choice at the moment is an Intel NUC8i3BEH approx 2 years old.
Internally, it contains a SATA port for a 2.5" SSD and a M.2 slot for a M.2 drive [COLOR="#0000FF"]or[/COLOR] NVME drive.
I have installed a Sandisk 2.5" SSD and a Kingston NVME.

The UEFI firmware allows me to independently isolate, de-activate or disable either drive. 
I can also disable both drives and use an external USB stick or drive.
Lastly, I can run an OS externally via a NVME drive in a suitable enclosure. (connected to the USB C port on the back panel).

I would doubt that Intel are alone in allowing this facility.

Sorry, old thread just noticed your post.

I decided in the end it would be cheaper and less hassle to buy a PCI docking removable caddy for the NVME boot drive, there is no option on my motherboard to disable NVME drives.   Otherwise new mobo etc with all the aggro that entails and this rig serves all my needs for the foreseeable future.

[IMG]https://images-eu.ssl-images-amazon.com/images/I/41DjhoKbQxL._SY180_.jpg[/IMG]

---

