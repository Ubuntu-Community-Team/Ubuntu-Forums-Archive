---
title: "how do I enable scsi emulation for my dvd drive and create a generic scsi device?"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by GazaM on 2005-05-09
OK, I want to speed up the process of ripping cd's in GRIP as it's going extremely slow (about 4-5x) so I looked in the help file and this is what it says;
> 
If you are using an IDE CDrom drive, using SCSI emulation can give a significant 
performance increase. Apparently, dma is not used by the IDE driver (at least in 2.4 kernels). To enable SCSI emulation, add "hdx=ide-scsi" (where the "x" in "hdx" is is replaced with the appropriate letter for your CDRom device) to end of the "kernel" line in /etc/grub.conf (if you are using grub), or as a line after "root=/dev/something" in /etc/lilo.conf (if you are using lilo)

You can also disable paranoia to get approximately a 2x speedup. This is not recommended, however, unless you are very confident in the ability of your drive to do rock-solid CDDA extraction (or unles you enjoy having pops in your audio)

> If you are using a SCSI drive, or an IDE drive under SCSI emulation, Grip needs to access the generic scsi device in addition to the cdrom device. On most systems, the generic scsi device will be /dev/sgx, where 'x' is a number. Unless you have multiple scsi devices, the device would be /dev/sg0. Ensure that your user account has access to this device, and that this device is specified in your rip configuration

OK, so the first problem I have is that I have GRUB on a floppy disk as the first time I installed linux GRUB screwed up my Windows partition so I now use the floppy disk, which means that /etc/grub.conf doesn't exist on my hard-drive to edit. So could someone tell me how i'd go about enabling scsi emulation or 'dma' on my dvd drive (/dev/hda on my computer).

My second problem is that there is no generic scsi device in ubuntu (for me at least) so if someone could tell me how to create one that would be great.

Sorry for the long post but as a person new to linux I am trying to get everything I do most in windows (cd ripping, encoding etc.) to at least the same level in ubuntu, and it's not going so well, I've already completely given up on getting 3d acceleration working on my ATI X700Pro as'NONE' of the various fglrx guides and the such have worked for me.

---

### Post by brickbat on 2005-05-10
i don't have a floppy so i don't know if the directory structure is the same as on the hd but i presume it is.

just browse the floppy and find menu.lst

Then edit it with 

sudo gedit /floppy/grub/menu.lst or whatever the right path is

Append hdd=ide-scsi if your cdrom correlates to /dev/hdd in your fstab and SAVE it.

sudo -s
echo 'ide-scsi' >> /etc/modules
exit

Then reboot computer to enable SCSI emulation for your DVD burner.

ciao
bb

---

### Post by GazaM on 2005-05-10
well, when I open the floppy disk in ubuntu there's nothing on it, but that's ok as I can just type  'sudo hdparm -d1 /dev/hda' and that turns on dma. The problem for me is creating the generic scsi device as there are none in the /dev folder called sgx (x being any number). There are however sgx devices in the /.dev folder, but they show up with an icon of a screen with a plug in front and a large red X on the top right corner of the icon. I've managed to get sg0 and sg1 entries in the /dev folder by typing something along the lines of 'sudo modprobe sg' (or something like that; I did it earlier when I saw it in another post) but the icons are the same and I have no idea how to remove the X in the corner which I assume means that it is not enabled as even when I specify it in GRIP it wont even start ripping anymore. Anybody know how to enable this?

---

