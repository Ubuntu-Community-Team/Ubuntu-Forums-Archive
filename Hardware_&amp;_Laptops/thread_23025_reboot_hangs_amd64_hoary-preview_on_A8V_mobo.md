---
title: "reboot hangs: amd64 hoary-preview on A8V mobo"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by dmallery on 2005-03-30
hi

using two separately downloaded and burned iso images, i get this result trying to load the latest hoary preview iso.

the first phase works perfectly, eject cd and reboot.  the reboot proceeds thru:

starting ubuntu

ata3: disabling port

and there it sits!

if i try the "failsafe" grub boot option:

it goes much further, finding my scsi disks till it says:

Stopping tasks: ===

and that's all she wrote.

did not expect this from hoary since warty worked perfectly.

any help will be gratefully received!

thanks

dave mallery

---

### Post by mossholderm on 2005-04-03
[QUOTE=dmallery]hi

using two separately downloaded and burned iso images, i get this result trying to load the latest hoary preview iso.

the first phase works perfectly, eject cd and reboot.  the reboot proceeds thru:

starting ubuntu

ata3: disabling port

and there it sits!

if i try the "failsafe" grub boot option:

it goes much further, finding my scsi disks till it says:

Stopping tasks: ===

and that's all she wrote.

did not expect this from hoary since warty worked perfectly.

any help will be gratefully received!

thanks

dave mallery[/QUOTE]
 Have you tried booting with the following? :

*acpi=off noapic pci=routeirq*

I had problems with the stock kernel without those parameters Once I upgraded to a new kernel, I was able to scale back to just *acpi=off*. YMMV.

     --Matt

---

### Post by silic0n-jebus on 2005-05-20
I have an ASUS A8V Deluxe mobo as well, however when I install mine, it reboots, extracts the packages, then reboots the computer when it is loading what looks to be x windows. THe last thing i see is something like "Extracting Gnome" or something along that line. PLEASE HELP! I really want to run ubuntu.

Specs:
ASUS A8V Deluxe, AMD 64 3400+
512 PC400 DualChannel mem
IBM 80 GB SATA
Geforce 5950

---

