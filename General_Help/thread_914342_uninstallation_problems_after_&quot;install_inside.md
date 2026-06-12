---
title: "uninstallation problems after &quot;install inside windows&quot;"
date: 2008-09-08
forum: General Help
---

### Post by brianstewey on 2008-09-08
Hola,

I run windows vista <insert flavour here>. I installed 8.04 ubuntu with the "install inside windows" option. I did something funny when I was doing the actual boot into ubuntu and install, and now i cant uninstall "install inside windows" ubuntu from windows

ie. it shows up in Programs and Features -> add/remove but it doesn't remove it
ie. running uninstall-ubuntu.exe fails (in the ubuntu install directory)

Also,
I can't boot into the ubuntu installation (it fails)
I have tried to run the "install inside windows" option again but it fails

I would like to remove this somehow especially the bootloader it installed

cheers

---

### Post by Kumagoro on 2008-09-09
Following the wiki :)

Remove C:\ubuntu (C:\wubi in 7.04) and C:\wubildr*. 

**In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via control_panel > system > advanced > startup_and_recovery and pressing "Edit". **For Windows 98 you have to edit C:\config.sys, and remove the Wubi block. 

To remove Wubi from the add/remove list, delete the registry key: HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

---

