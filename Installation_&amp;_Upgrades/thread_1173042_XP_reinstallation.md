---
title: "XP reinstallation"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by vijaysarathy on 2009-05-29
Hi all,
I have two OSs in my system.
Windows XP and Ubuntu 9.04..
XP is installed in C Drive. I wish to format that drive and reinstall XP.
If I do this, is there any possibility of getting problems with the Grub or others. 
Or anyone pls tell me how to safely format the drive containing XP and reinstall it without affecting Ubuntu.
Thanks in advance ...

---

### Post by Mark Phelps on 2009-05-29
Resinstalling XP will overwrite the MBR and remove GRUB from it -- there's no way around that.

You should be able to boot from your XP CD, select the existing XP "drive" and reformat it as part of reinstalling XP.

After that, you'll need to boot from the Ubuntu LiveCD and reinstall GRUB. See the link below for details:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

