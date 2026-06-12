---
title: "[SOLVED] Key to select Ubuntu's partition when booting"
date: 2008-09-18
forum: General Help
---

### Post by avidog on 2008-09-18
I have installed Ubuntu V6.06 from a CD, and told the computer to use the largest unused space for Ubuntu's partition.  That seemed to work.  After the install I had the whole Ubuntu package running from my hard drive.  But when I reboot the computer, it starts only in Windows Vista, and does not give me a screen to select Linux instead.  Is there a key I can hold down during the boot sequence that will force the computer to find Ubuntu instead of Windows?  That would solve my problem adequately for now. Once I have 6.06 installed and booting properly, I will proceed with upgrades online.

---

### Post by drs305 on 2008-09-18
Here is a link to getting a grub menu. It was written to restore grub after installing windows but may apply in your case as well. What it does is overwrite the Windows bootloader in the MBR and replace it with grub. 

If this is an acceptable way for you, here is the link on how to do it:
[RestoreGrub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

---

