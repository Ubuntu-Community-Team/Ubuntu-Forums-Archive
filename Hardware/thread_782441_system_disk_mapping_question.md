---
title: "system disk mapping question"
date: 2008-05-05
forum: Hardware
---

### Post by pendrachken on 2008-05-05
I have performed a new Hardy install and am having a slight problem with disk mapping. NORMALLY on Linux ( at least since I started using it - Red Hat 8ish ) a PATA ( IDE ) drive will be labeled with HDx and SCSI / SATA drives are the SDx drives. Now with hardy though ALL of my HDD are labeled SDx, 3 PATA drives and both of my SATA drives. Is there a way to change the system mapping of the drives to point to the HDx entries in /dev ( right now for my first PATA drive I can NOT mount it using mount -t ext3 /dev/hda1 /MOUNTPOINT) I have to use sda1. 

I need to be able to mount disks on the fly from scripts ( and no I do not want to re-write / edit all the scripts I have ) using the HDx format for all 3 of my PATA drives. Other than the scripts that need the old style names everything mounts fine, my data is all there and accessible. 

Any help, or explanations of why the installer / kernel / grub system map or whatever may be causing this would be appreciated. 

As a side not, while google diving for some answers I ran accross a tutorial that had screenshots showing the same thing, PATA and SATA drives all listed as SDx in the hardy installer.

---

