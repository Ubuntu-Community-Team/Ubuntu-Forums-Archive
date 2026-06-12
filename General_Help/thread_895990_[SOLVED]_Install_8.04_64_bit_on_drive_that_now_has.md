---
title: "[SOLVED] Install 8.04 64 bit on drive that now has XP with 2nd drive Ubuntu 32 bit"
date: 2008-08-20
forum: General Help
---

### Post by 73ckn797 on 2008-08-20
Greetings,

I have installedUbuntu 32 bit 8.04 on a second drive. I booted the system from a live CD and installed from that. I can dual boot with no problems. Does that mean that I performed a WUBI install? I do not believe that is what I have done. I initially did perform an install through Windows but have been playing around and reversed that procedure. There were problems with Windows loading but I corrected that in several instances.

I see that there are 2 files (Wubr) on the XP drive (C:) that affect the boot up process. The XP "boot.ini" file shows the location of the Ubuntu drive. I plan on wiping the C drive of XP and want to install the 64 bit Ubuntu 8.04 on that drive. What will I need to make sure that I can dual boot to both drives. The second drive has Ubuntu 32 bit 8.04. If the 64 bit installs and I can work out the Java issues for an image uploader, I will then use only the 64 bit and wipe the second drive.

Being so new to the Ubuntu system, I do not possess very much knowledge. I am aware and have downloaded the Super Grub and created the disk. Will I need to use that first or proceed with the 63 bit install? Will the 64 bit install do what will be needed to still have the dual boot for both drives?

Does any of this make sense?

---

### Post by Sef on 2008-09-06
Please do not mark threads as solved unless you provide an answer.  Could you state how you resolved your problem.  Thank you.

---

### Post by 73ckn797 on 2008-09-06
> **Sef said:**
> Please do not mark threads as solved unless you provide an answer.  Could you state how you resolved your problem.  Thank you.

I consider this solved because:

I figured out how to use terminal and entered "gksudo gedit /boot/grub/menu.lst". There I deleted the references to Windows XP. wiped the Windows drive and installed the 64 bit Ubuntu. When the 64 bit would not boot from the Grub menu I did some searches in the forum and reading that helped out. I then edited the "menu.lst" with the correct drive references ie... hd0, hd1,  which I copied and pasted from the menu.lst created by the second OS installation. When the 64 bit version would not load I experimented in the boot menu with the edit function and changed the drive references until one of them worked. That will be different with each computer configuration.

I now can load or unload any different version of Ubuntu or other OS and if there are any boot up issues they can mostly be fixed with editing of the menu.lst.

I pays to do some homework.

---

