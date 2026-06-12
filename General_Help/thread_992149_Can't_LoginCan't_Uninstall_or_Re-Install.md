---
title: "Can't Login/Can't Uninstall or Re-Install"
date: 2008-11-24
forum: General Help
---

### Post by Coastalguy on 2008-11-24
Installed version 8.04.1 LTS on my Windows XP Home, external USB drive K. After installation, my User ID and Password ID that I set on installation won't work. Tried to uninstall using both the Windows Control Panel and the Ubuntu-Uninstall.exe file on the drive, but both start initially then just stop. Tried to re-install using the CD, but again it just starts and then stops.

All other id's and passwords on Windows, websites and others work fine using both Caps and lowercase, so it appears not to be a keyboard problem with the login. 

Cannot login or uninstall, so I have a useless Ubuntu OS. I understand that all files are within the installed folder, so removing it is just a matter of deleting the folder? But then, I have to get my MBR back to just Windows. Saw references to EasyBCD, but saw that this is only for Vista, not XP. Any suggestions?

============================================================================
Found how to reset the password through GRUB. Other posts I had found neglected to advise to select the "Recovery Mode" item from the 5 options available. I am now in, but still would like to know how to uninstall if I want to transfer the OS to a separate partition on my 2nd hard drive.

---

### Post by ago on 2008-11-25
For uninstallation problems in 8.04 see: [https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu)

For login issues, make sure that the keyboard is setup correctly (type the password in a cleartext form like the username to check the chars)

---

### Post by Coastalguy on 2008-11-25
ago,

Thanks for the link. However the "Manual Uninstall" section notes to remove the ubuntu boot line on boot.ini in my C:\ root directory. My problem is that I only have wubildr.mbr and wubildr files in my root, however I do have a "boot.ini.backup" file in my c:\windows\pss folder. This file does have both a windows and ubuntu line with the ubuntu line pointing to the wubildr.mbr in the c:\ root directory.

If I remove the complete ubuntu installed directory completely, I assume that I should remove the ubuntu line in my boot.ini.backup file and remove the wubildr.mbr from the c: root directory? Should then the boot.ini.backup be renamed to boot.ini and moved back to the c:\ root directory?

Thanks,

---

### Post by Coastalguy on 2008-11-25
Oops!

Found boot.ini. It was a hidden file and did not display using windows explorer. Opened it with start/run c:\boot.ini and there were the 2 boot lines, one for windows and one for ubuntu. Just wondering if I remove (or comment out ;) the ubuntu line, should the wubildr.mbr and wubildr files be deleted?

Thanks,

---

