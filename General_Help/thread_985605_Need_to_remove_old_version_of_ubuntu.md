---
title: "Need to remove old version of ubuntu"
date: 2008-11-17
forum: General Help
---

### Post by Silvernail on 2008-11-17
I need to remove an old version of Ubuntu. I want to install a newer version but the bootup keeps going straight to login and not looking to see if the CD has a boot module.

I have tried changing the BIOS to not have a harddrive and only CDroms but it seems to find the HD anyway.

The book I have seems to assume that I am migrating from Windows??

Does linux have an application that will just wipe the drive clean?

Thanks
Dave

---

### Post by ncanna1 on 2008-11-17
You could try disabling booting from HD from your BIOS for the time being completely, and then trying to boot from the CD.  Once on the live disk, you could use gparted (the partition manager) and completely reformat your drive.

---

### Post by Silvernail on 2008-11-18
> **ncanna1 said:**
> You could try disabling booting from HD from your BIOS for the time being completely, and then trying to boot from the CD.  Once on the live disk, you could use gparted (the partition manager) and completely reformat your drive.

In the BIOS I tried setting all boot devices to CDRom. Still booted off the hard drive. Go figure.

Looked at 'gparted' and decided it was too complicated for me. Besides it looked dangerous. Found 'cfdisk' and emptied the 2 partitions on the HD. To confirm the partitions were empty I rebooted. Got to the line 'Loading GRUB' and up pops 'ERROR 22'.

Power down. Put my CD with 'Edgy Elf' in and it installs as expected.
Power down.  Empty the partitions again.

Last spring I bought a flash drive from MadTux with 7.10 installed on that would boot like a CD. Used it 3 weeks ago on a new drive I installed in this computer. Plug that into a USB socket.

Nothing.

Leave the flash drive in place and put the CD in its drive and reboot.
'Edgy' installs and I have an icon on the screen for the flash drive. That has a folder marked Install, I open it and everything in there gives me the error of no application on this computer to handle this type of file.

What I would really like  to do is get back to HH 8.04.
Does anyone know how to upgrade from Edgy Elf? It seems that version is deprecated.

Thanks
Dave

---

