---
title: "Ubuntu Full Install on USB"
date: 2008-10-28
forum: General Help
---

### Post by master_script_maker on 2008-10-28
Hi everyone!
Im trying to install the full Ubuntu 8.04 package on a USB drive. I have looked at several guides here, and on other sites, but to my distress they have led to grub error 15 and 17. I looked up how to solve these problems on your forums also, but nothing worked. Then i thought about using a different boot system(maybe syslinux?), would this be possible?
Thanks.

---

### Post by mlentink on 2008-10-28
I do this regularly, in fact this is how I test new releases, like Intrepid at the moment.
Preferably use the alternate installer (thought it should work with the guit installer as well). At partition time, make sure you specify the right drive and partitions to install to (I use a 20GiB USB drive, so I usually simply choose to take the whole drive). After most of the stuff has been installed, you will be asked where to install GRUB. Make sure to select the right drive, which will probably be something like '(hd1)'. In the gui-installer you select the 'advanced' option in the screen where you get to commit changes to partitions and installation options.
The installer will happily install everything. But when you try to boot, you will get errors. So you boot up with your current local install (or with the LiveCD, if you prefer, or if, heaven forbid, your local install should be that other os). Edit the 'boot/grub/menu.lst' file on the usb-drive, and change the references at the installed os's from (hd1,x) to (hd0,x), and vice versa (if you want to be able to access the os on your local drive). Then reboot to your USB-drive.

---

### Post by caljohnsmith on 2008-10-28
Just to clarify, are you are trying to install Ubuntu to your USB drive, or trying to install the Ubuntu Live CD to the USB drive? I assume it is the former case, and if that is true, just click on the "advanced" button in the last stage of installation and tell Grub to install to /dev/sdb or whichever is your USB drive; just don't use (hd0) unless you want to put Grub in the MBR (Master Boot Record) of your internal drive. That should work, but if you get any Grub errors after doing that, let me know, and I can help you sort them out. :)

---

