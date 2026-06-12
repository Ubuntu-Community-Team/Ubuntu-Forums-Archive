---
title: "Accidentally remove Ubuntu"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by plikadot on 2009-06-24
I just have accidentally removed Ubuntu from my Windows partition (I installed it in NTFS - under Windows XP - wubi?) I deleted the "Ubuntu" folder from C:/ without proper uninstallation.

Now, I'm getting confused, how to remove LILO boot loader from my computer. If I reinstall new Ubuntu, will it create a new bootloader option, instead of replacing/reusing the old one? Actually I want to delete the old bootloader since I want to upgrade the Ubuntu.

Need ur help. Thanks alot.

---

### Post by raymondh on 2009-06-24
> **plikadot said:**
> I just have accidentally removed Ubuntu from my Windows partition (I installed it in NTFS - under Windows XP - wubi?) I deleted the "Ubuntu" folder from C:/ without proper uninstallation.

Now, I'm getting confused, how to remove LILO boot loader from my computer. If I reinstall new Ubuntu, will it create a new bootloader option, instead of replacing/reusing the old one? Actually I want to delete the old bootloader since I want to upgrade the Ubuntu.

Need ur help. Thanks alot.

Are you referring to the UBUNTU option as you boot up?  If so ... in windows ...

Control Panel > System > Advanced tab > Startup & Recovery options >  Edit

You will bring up the boot.ini file.  In there, ***_ONLY_*** remove the line referring to wubi/Ubuntu.  It's this line

**C:\wubildr.mbr = "Ubuntu"**

**DO NOT REMOVE/EDIT ANYTHING ELSE AS YOU WILL LOSE YOUR OPTION TO BOOT INTO WINDOWS.**

For your reference

[http://ubuntuforums.org/showthread.php?p=7501325#post7501325](http://ubuntuforums.org/showthread.php?p=7501325#post7501325)

Good luck.

---

### Post by plikadot on 2009-06-24
No need to do ... fdisk/mbr or something like that?
Thanks anyway. :popcorn:

---

### Post by raymondh on 2009-06-24
> **plikadot said:**
> No need to do ... fdisk/mbr or something like that?
Thanks anyway. :popcorn:

If you have the original windows install disk .... you can use that to access a command prompt and either fixmbr or fixboot.  Fix mbr fixes the existing MBR whilst fixboot will write a new boot sector. 

If you decide to do that, the steps are Boot into the install disc > repair > access a command prompt > and type what you decide to do (either fixboot or fixmbr)

If this was a wubi install and you are referring to the ubuntu option still there as you boot up, why not just remove it from the boot.ini file and still retain the existing windows bootrec?  Just be cautious .... see the link.

Nevertheless, it is your choice.  You can try to fixmbr.  If that does not work, try fixboot.  If the UBUNTU option is still there, then you have to do some editing on the boot.ini file.

Are you referring to another issue and not that 'ubuntu-option-when-you-boot-since-you-no-longer-have-ubuntu'?

Good luck.  Back-up your files.

---

