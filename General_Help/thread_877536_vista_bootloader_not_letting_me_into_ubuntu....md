---
title: "vista bootloader not letting me into ubuntu..."
date: 2008-08-01
forum: General Help
---

### Post by jorik42 on 2008-08-01
ive been working with ubuntu for a while, and wanted to install in on my new computer (as a dual-boot with vista).  feeling lazy (and somewhat curious) i thought id try the install-from-within-vista option for installation.  however, this method creates an ubuntu entry in the windows vista bootloader.  This is not to my satisfaction, so i wanted to switch back to grub; however, i cant.  Even doing a fresh install of ubuntu (where grub is setup and configured in the process) does not replace the windows bootloader with grub.  anyone have any ideas on how to fix this?

thanks

jorik42

---

### Post by jualin on 2008-08-01
Are you getting both, Vista's Boot Loader and Grub?

---

### Post by jualin on 2008-08-01
For the Vista Bootloader, you can take out Ubuntu from the list by accessing the Microsoft Configuration Utility in Vista. Just go to start, run and write > msconfig The Boot loader list will be in the Boot Tab, and deleting Ubuntu from the list will make it disappear from the Vista Boot Loader.

---

### Post by AnonCat on 2008-08-01
Use EasyBCD (tutorial and link below) to configure Vista's bootloader to give you the option of booting into either Linux or Vista. 

Download EasyBCD software (freeware):

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Follow this tutorial:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by jorik42 on 2008-08-01
ok

a.) there is no option for linux in the boot tab of msconfig.  the only option there is vista.  the vista bootloader doesnt know about ubuntu  (note, i re-installed ubuntu in an attempt to put grub first, so there is no longer an ubuntu entry in the vista bootloader).

b.) i dont want to use the vista bootloader.  i would like to use grub, and it seems that the tutorial is setting us up to use the vista bootloader.  

so, how do i replace or remove the vista bootloader in order to use grub in its place?

---

### Post by Ender305 on 2008-08-01
find one of the many "reinstalling grub" topics and just follow those directions, I'm not sure it will autodetect vista, so you might have to add that afterwards

---

### Post by jualin on 2008-08-01
So did you install Ubuntu already or your machine doesnt have Ubuntu? You can install Ubuntu using the LiveCD and this should automatically detect Vista and make the Grub for you, you just have to be careful with the partioning since you can delete Vista if you make a mistake. [Check this link for a tutorial]("http://https://help.ubuntu.com/community/WindowsDualBoot") of how to install a correct Dual Boot system (which I believe you want). Hope this helps!

---

### Post by jorik42 on 2008-08-02
yes, ubuntu is installed.  i just re-installed it to make sure.  it still does not set up grub correctly.  

im not sure how best to describe this; normally, when ubuntu boots, it goes through the bios setup screens, ect.  then it enters grub, where i choose my desired OS.  however, in this case, rather than entering grub, it loads the vista bootloader program instead.  id like it to be the other way around (loading grub instead).

---

### Post by jualin on 2008-08-02
Did you install Ubuntu using the LiveCD or did you install it using the Wubi Installer (within Windows)?

---

### Post by jualin on 2008-08-02
In other words, can you uninstall Ubuntu using Windows Control Panel, Add and Remove Programs?

---

### Post by jorik42 on 2008-08-02
originally, at the beginning of this whole process, i installed it using wubi.  i then installed ubuntu via the live cd to the same partition (desiring to use grub).  i have since re-installed a few times to the same partition (via the live cd).  

perhaps i should have first uninstalled it via the control panel? ill go try reinstalling/uninstalling via wubi...

---

### Post by jualin on 2008-08-02
If you installed it via wubi then you have to use the Vista Boot loader. You should uninstall Ubuntu from Windows via Windows Control Panel and then boot the Live CD and install it from there. Be careful when you select your partitions because you might delete your Vista partition if you are not careful. Good luck!

---

### Post by jorik42 on 2008-08-02
yeah thats kinda the problem.  thats exactly what ive been doing and its *not working*.

---

### Post by jualin on 2008-08-02
Check the tutorial in my sig

---

