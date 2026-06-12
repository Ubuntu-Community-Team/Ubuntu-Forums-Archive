---
title: "Ubuntu Dual Boot Problems 2 Hard Drives"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by Andrew12 on 2009-03-12
Ok... So I want to have a dual boot Windows XP + Ubuntu 8.10. I have 2 hard drives. I want to have XP on the FIRST one, and ubuntu on the second one. I tried to install GRUB onto the FIRST HD... it worked... but it wouldn't boot from it. GRUB kept giving me Error 21... So I put in my XP disc and went into the recovery console and ran fixboot and fixmbr. XP booted... I reinstalled ubuntu onto the second HD and put GRUB there. Now what I want to do is I want to have the Windows boot loader let me choose from XP or ubuntu. The XP disc cannot be formatted, as I am using it for a project... the second one I do not care about.. right now there is nothing on it but a Ubuntu clean install and GRUB. Please help! :popcorn:

---

### Post by thesavager on 2009-03-12
Hi,

Dualboot in windowsXP is not supported.
You could try , putting the second drive as first drive in bios , since you installed grub on second drive.(if you have ata or sata you just have to switch bootdrive in bios) or else you may have to change the drive-settings, manualy on harddisks.(jumper-settings)

ERROR 21 , could be that one of the hard disks is not identified by grub.

so make sure they are present in bios.

cheers...

---

