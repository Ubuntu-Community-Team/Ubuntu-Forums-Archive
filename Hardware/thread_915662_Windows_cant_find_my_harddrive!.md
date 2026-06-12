---
title: "Windows cant find my harddrive!"
date: 2008-09-10
forum: Hardware
---

### Post by brammer on 2008-09-10
Hi. My laptop came with XP Home. All the files piled up, and I choose to install ubuntu. I realise some program i need only is for windows. I tried to install XP Pro with out removing ubuntu. Windows couldn't find my harddrive. Then i tried to unallocate the entire harddrive with gparted. Still no harddrive. Then i tried to format it to nfts with Gparted. Still no harddrive. 

Now i installed ubuntu again, just so i can use my laptop. I would like to have windows back.

I own a Lenovo/IBM Thinkpad R60.

Please help me ;)

---

### Post by IntuitiveNipple on 2008-09-10
This doesn't immediately solve the issue, but it'll avoid having to re-write the entire drive again.

Windows expects to be in the first *recognisable* partition in the partition table (unrecognised partition types are ignored - this is why Windows recovery partitions are installed in the first partition by system manufacturers).

So, 'reformat' the drive once more, with the first partition reserved for use by Windows. Allocate it sufficient space (For a working XP with applications, that probably requires 10GB minimum).

The layout of the partitions might then be something like this:

#1 Windows (type 7, active)
#2 /boot (type 83)
#3 swap (type 82)
#4 LVM (type 83)

Install Ubuntu using the LVM (logical volume management) option into partition #4. Within that LV you can create volumes for:

**vgRoot** / (root) 6 to 12GB
**vgVar** /var (growing files) 4GB+
**vgHome** /home (user space) remaining free-space (less an amount for 'unallocated')
***unallocated*** (spare for allocating to other LVs if they become full)

With this layout you can then mess about with Windows without trashing the Ubuntu installation, provided you don't try to erase the entire drive from the Windows installer (if it recognises the disk-drive).

Now, as to the problem with XP not recognising the drive. It is likely that the original XP installer doesn't have the drivers for the hard disk controller (probably a SATA controller?) and you need to provide them at the beginning of the Windows installation by giving it a driver floppy/CD with them on. I think it prompts briefly to "Press F6 for additional driver disk..." (or some similar message).

Use Linux to discover the disk controller:
```

lspci -vnn

```
and use that information (in particular, the PCI device ID) to locate he correct Windows driver package. From that package, read the .inf file and determine what files are installed for the PCI ID of the controller. Put the .inf, .sys, and .dll files onto a floppy or CD.

When the Windows installer runs and prompts, press F6 (or whatever key it says) and provide the driver disk. It will read the disk and give you a choice of what driver to install from the .inf file. Once that is done the Windows installer should recognise the disk drive and you can install into partition #1.

---

### Post by invisiblebob8616 on 2008-09-16
I also have a lenovo laptop and one issue I encountered with reinstalling XP is that the XP installer does not recognize SATA hard drives.  If you go into the BIOS you can change the settings so that the BIOS spoofs the SATA hd as an IDE.  If you do that, XP should install normally.

---

### Post by in-dust-rial on 2008-09-16
read this issue 3 weeks ago.
maybe forum search could help

good luck

---

