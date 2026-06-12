---
title: "Wubi uninstall won't run please somebody help"
date: 2008-11-16
forum: General Help
---

### Post by hoboy on 2008-11-16
I have installed ubuntu with wubi, I am using dual booting with vista
now I want remove ubuntu and reinstalled it, but E:\Ubuntu\Uninstall-Ubuntu.exe refuse to launch, is there any other way of installing it ?

---

### Post by premier69 on 2008-11-16
I can second that problem.

I Can't launch the uninstaller when trying to remove ubuntu / kubuntu from the vista control panel uninstall.

I am using up to date hotfixes, Vista x64 with sp1 and nothing at all happens when trying to launch the uninstaller.

---

### Post by Marcus Derekus on 2008-11-16
Don't know why you would ever uninstall ubuntu but:

Try inserting the installation disk and it might give you an option to uninstall if you choose to install

---

### Post by Marcus Derekus on 2008-11-16
you can also just delete the ubuntu folder

then download EasyBCD and delete the Ubuntu boot option

---

### Post by hoboy on 2008-11-17
I have installed wubi, I used dual booting with vista, but I have select E:\ drive to install ubuntu insted of c:\ where vista is installed, now I want to uninstall ubuntu then reinstall it but E:\Ubuntu\Uninstall-Ubuntu.exe refuse to launch, is there any other way of uninstalling ubuntu ?

---

### Post by Marcus Derekus on 2008-11-17
All of the ubutnu files are stored in the ubuntu folder. 

So. Just deleting the ubuntu folder then removing the Ubuntu option from the bootloader using EastBCD should work.

Then just reinstall ubuntu THEN REBOOT

btw after you do all that:  IF for some reason ubuntu doesn't show up on the bootloader after reinstallation, than directions for fixing that are here [http://ubuntuforums.org/showthread.php?t=983302](http://ubuntuforums.org/showthread.php?t=983302)

OTHER WISE THATS IT

---

### Post by ago on 2008-11-18
See the guide [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) there is a section on uninstallation problems, and if that fails there is a section with manual uninstallation instructions.

---

### Post by IBUA on 2008-11-20
> **ago said:**
> See the guide [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) there is a section on uninstallation problems, and if that fails there is a section with manual uninstallation instructions.


I had the same problem on XP (The Uninstall wouldn't work)

But if you go on the guide thingy above and download it it should work.

---

