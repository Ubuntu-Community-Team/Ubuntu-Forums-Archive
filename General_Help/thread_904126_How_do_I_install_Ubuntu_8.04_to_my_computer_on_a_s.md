---
title: "How do I install Ubuntu 8.04 to my computer on a seperate partition"
date: 2008-08-29
forum: General Help
---

### Post by dorame on 2008-08-29
How do I install Ubuntu 8.04 to my computer on a seperate partition but without the grub boot loader?

I want to use the default Windows Boot Loader to boot my Ubuntu installation. How do I do this?

Thank

---

### Post by tuxxy on 2008-08-29
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

---

### Post by unutbu on 2008-08-29
In step 4 of the install process ("Prepare diskspace/partitions") choose "Guided" partitioning.
There, you will be able to select the partition where  Ubuntu will be installed.

In step 7, ("Ready to install"), click the Advanced Button. Uncheck the box which says "Install boot loader". GRUB will then not be installed.

---

### Post by cdtech on 2008-08-29
You'll need to create a bin file that Windows can use to boot the Ubuntu installation and then modify the "boot.ini" file within the Windows C:\ directory to include the Ubuntu bin file:

dd if=/dev/**sda2** of=/mnt/**XP**/**temp**/ubuntu.bin bs=512 count=1 

Create a mount point (using the live cd) within Ubuntu to mount the windows partition (ie../mnt/XP). I created a "temp" directory under my C:\ directory to copy to. Then adjust the above command to match your partitions and mount points. This will give you the bin file that the Windows "boot.ini" file will point to.

Add to the last line of the "boot.ini" file:
C:\temp\ubuntu.bin="Ubuntu Hardy 8.04"

See this link for using Vista:
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

---

