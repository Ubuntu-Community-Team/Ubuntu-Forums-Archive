---
title: "Hard drive switch"
date: 2011-01-27
forum: Hardware
---

### Post by ratcat on 2011-01-27
Cannot get info at  WIndows 7 forums, here goes. SATA drive a 5400 rpm Windows 7 Ultimate original disc drive, SATA b 7200 rpm, Ubuntu 10.
Possible to change Windows 7 to 7200 sata drive? Changes to Ubuntu on b drive? And will W7 let this happen? I have recovery disc for W7, upgrade disc for Ultimate. Will I notice a big improvement in WIndows ? The W7 system is used daily for art and photo work and runs a bit slow with complex art in Adobe CS5 and Xara. 
Thanks

---

### Post by grahammechanical on 2011-01-27
I have heard that if you change or replace a component like a hard drive then you will need to get authentication from Microsoft for the re-installation of Windows to complete. You might find that the recovery CD has some kind of imprint from the drive that you are using for Windows and it might not like it if you try to recover the OS on to a different hard drive. I may be completely wrong.

Do not forget that you will have to change the settings at the back of the drives From master to slave for the present Windows drive and slave to master for the present Ubuntu drive.

Regards.

---

### Post by tgalati4 on 2011-01-27
It would seem simpler to purchase another 7200 rpm drive and install Windows7 to it.  That way, if you run into trouble, you still have a working Win setup.  Once your new drive is set up and verified that all your apps are working, then you keep the old drive as a backup for a while, then when that backup is no longer needed, you can wipe it and simply copy Ubuntu to it:

sudo cp /dev/sdb /dev/sdc (your drive designations will be different)

Use gparted to recapture any space left over on the drive and rewrite the partition table.  You may need to use blkid and adjust the UUID's in grub because they will change, but it's quicker than reinstalling Ubuntu and reconfiguring it the way you want.  If you don't have too much customization, then you can simply install a new Ubuntu version then copy your /home over.

If you don't need the extra SATA drive in your machine, then purchase either an esata, firewire, or usb enclosure for it so you can use it for multiple backups.

---

### Post by Bucky Ball on 2011-01-27
Pro-level AV work = nothing less than 7200rpm. Not saying it can't be done, but you are finding out why it's not. ;)

---

