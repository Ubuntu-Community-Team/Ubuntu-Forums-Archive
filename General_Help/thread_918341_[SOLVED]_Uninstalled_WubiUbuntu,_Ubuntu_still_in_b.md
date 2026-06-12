---
title: "[SOLVED] Uninstalled Wubi/Ubuntu, Ubuntu still in boot menu..."
date: 2008-09-12
forum: General Help
---

### Post by Rickeo on 2008-09-12
Im runnning Vista x64, and I have realized that editing the boot menu in Vista isnt as easy as it was in XP. I looked into BCDEDIT, but that was to confusing for me. I just want Ubuntu gone from my boot menu so that I dont have to hit "enter" on Vista. I know Vista will boot by default anyway, but Ubuntu shouldnt be there now that I uninstalled it. It seems the Wubi people forgot about this... :confused:

So, what do i do?

---

### Post by Kumagoro on 2008-09-13
Wiki:

In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via control_panel > system > advanced > startup_and_recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys, and remove the Wubi block.



That's the only way... just delete the proper lines and make a backup just in case

---

### Post by Rickeo on 2008-10-01
That EasyBCD was perfect! Exactly what I was looking for and more actually. I only wonder why that was never mentioned in any of my googling.

---

