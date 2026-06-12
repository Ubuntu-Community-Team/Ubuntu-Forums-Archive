---
title: "ubuntu 8.10 wont recognise my partition"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by kiragu12 on 2009-03-04
Hi
Am trying to install ubuntu 8.10 from a live cd but i gets to stage 4 (prepare partitions) and its blank. I've been to the desktop to try to mount the partitions but i cant. i've even added some applications (disk manager and mountmanager) but nothing works. help.

I have a 64 bit vista computer
NVIDIA mGPU 8200
AMD Athlon X2 (64) 2.7 GHz
EXcelstor 250 GB SATA HDD
2 GB of RAM DDR2

---

### Post by taurus on 2009-03-04
What's the output of this command from Ubuntu LiveCD?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by kiragu12 on 2009-03-04
nothing
i've tried that and sudo fdisk -lu

---

### Post by taurus on 2009-03-04
Maybe you want to go into the BIOS and turn on the AHCI for the harddrive.

---

### Post by kiragu12 on 2009-03-04
"Maybe you want to go into the BIOS and turn on the AHCI for the harddrive"

By this, you mean i got to the vista boot menu and turn on the AHCI

---

### Post by taurus on 2009-03-04
When you first turn on your computer, you would see a logo from your mobo with a message either at the bottom or upper right corner telling you what to press if you want to get into the BIOS or Setup.  On some systems, you have to press F2, F12, or Del to get into the BIOS.

And if your machine starts either booting into Ubuntu LiveCD or windows, it means you didn't press the right key in time to access the BIOS.

---

### Post by kiragu12 on 2009-03-04
I pressed DEL and accessed the BIOS Menu but nothing like AHCI came up.
The closest was ACPI: suspend mode - S3 (STR)
                      ACPI version features - ACPI v1.0
                      ACPI APIC support - Enabled
I'll go back and try to look for anything closer.

---

### Post by kiragu12 on 2009-03-04
I found a menu to change the SATA mode or something from SATA mode to AHCI.
then it asked me if i need to change the AHCI DID for linux and I enabled that feature.

---

