---
title: "install from vmware to usbdrive gives grub error 17"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by Digitallysick on 2009-03-14
So i got the latest ubuntu, and i plugged in my external usb drive and tried to install to it, it shows up as /dev/sdb1 when it comes time to install grub the choices it gives me are /dev/sdb and /dev/sdb1 so i select sdb1, when i reboot the computer and select my usb drive, i get grub error 17

so how do i make it where grub can reside on the usb drive itself and point to the OS? thanks

---

### Post by meierfra. on 2009-03-14
> install grub the choices it gives me are /dev/sdb and /dev/sdb1 so i select sdb1,  

You need to select /dev/sdb

---

### Post by Digitallysick on 2009-03-14
So sd1 and sdb are both choices, my drive is sdb1 so i select sdb?>

---

### Post by meierfra. on 2009-03-14
If you choose /dev/sdb1 Grub will be installed to the first sector of the Ubuntu partititon. But you need to  install Grub to the  MBR (the first sector) of the hard disk. 
 So you need to select "/dev/sdb" (Just like that, no number)

---

