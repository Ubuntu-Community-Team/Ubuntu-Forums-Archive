---
title: "partition"
date: 2012-11-11
forum: Hardware
---

### Post by whitlock501 on 2012-11-11
hi i have downloaded and installed ubuntu ... it was not at my needs anymore so i went into my unistall a program in cotrol panal in windows... i uninstalled it but when i reboot my computer it always asks me if i want to boot on ubuntu or windows and my hardrive is still at 350gb when it suposed to be at 650gb . what can i do to completely remove ubuntu ?

---

### Post by gerowen on 2012-11-12
> **whitlock501 said:**
> hi i have downloaded and installed ubuntu ... it was not at my needs anymore so i went into my unistall a program in cotrol panal in windows... i uninstalled it but when i reboot my computer it always asks me if i want to boot on ubuntu or windows and my hardrive is still at 350gb when it suposed to be at 650gb . what can i do to completely remove ubuntu ?

As far as fixing the bootloader, I found some instructions here:

[http://www.windowsreference.com/windows-7/how-to-reinstall-windows-7-boot-loader/](http://www.windowsreference.com/windows-7/how-to-reinstall-windows-7-boot-loader/)

As far as fixing the partition issue, GParted Live should be able to remove the Ubuntu partition and resize your NTFS partition to take up the whole hard drive.  You can get it here:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by whitlock501 on 2012-11-12
as far for the bootloader the instoctions dint realy help me ...

---

### Post by oldfred on 2012-11-12
Was this a partitioned install or a wubi install inside the NTFS formatted partition?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by whitlock501 on 2012-11-12
yes

---

### Post by oldfred on 2012-11-12
You have to use BCDedit from Windows to remove wubi entry.

See links posted above for more detail, I do not know BCDedit nor Windows.

Uninstall wubi:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)
bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)

---

