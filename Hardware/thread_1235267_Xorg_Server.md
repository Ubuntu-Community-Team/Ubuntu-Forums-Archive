---
title: "Xorg Server"
date: 2009-08-08
forum: Hardware
---

### Post by RedSingularity on 2009-08-08
I just messed up my Xorg.conf file.  I cannot boot into any graphical interface.  Can someone please help me work out this problem.  I would like to learn how to fix this sort of thing on my own.  Thanks.

---

### Post by overdrank on 2009-08-08
> **Shadow121 said:**
> I just messed up my Xorg.conf file.  I cannot boot into any graphical interface.  Can someone please help me work out this problem.  I would like to learn how to fix this sort of thing on my own.  Thanks.

Hi and I am assuming you are using Jaunty with the Nvidia Geforce 8600GT, you are not able to boot into recovery mode and use the xfix option to correct the graphical issues?

---

### Post by lswb on 2009-08-08
For several versions now there has been a "repair X" option on the menu that appears when you select "recovery mode" from the grub boot menu. You may need to press the escape key while booting if your grub menu is not normally visible. Try that first.

Or, if you are able to boot to cli, you can run the same command that the recovery/repair x menu item does:

sudo dpkg-reconfigure -phigh xserver-xorg

If you need to save any info from your messed-up xorg.conf make a copy of it before running this command, I can't recall if it automatically makes a backup or not.

---

### Post by RedSingularity on 2009-08-09
> **overdrank said:**
> Hi and I am assuming you are using Jaunty with the Nvidia Geforce 8600GT, you are not able to boot into recovery mode and use the xfix option to correct the graphical issues?


I can believe i didnt think of that.  Well it did the trick!  Thanks a lot guys.

---

