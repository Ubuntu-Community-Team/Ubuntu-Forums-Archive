---
title: "Bad Ubuntu Uninstall Mistake"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by Chucklz on 2009-10-09
I had Ubuntu installed on a partitioned portion of my hard drive and I also gave the GRUB loader priority so that Ubuntu would load first. I had Ubuntu installed for several months (probably 7 or so) and have used it very infrequently (Never figured out how to install my wifi USB dondle) so I decided to give up and uninstall it. I decided the easiest way would be to departition the Ubuntu Partition and leave it at that. I departitioned everything and rebooted. Upon start up, GRUB loader ran (in my haste, i forgot to switch Vista priority back) and it stopped (due to the lack of an Ubuntu anymore). I already have a solution, that being installing Windows 7, but that'll take a couple of weeks to get. I was wondering if there was a way to boot Windows Vista (bleak) and get rid of the GRUB loader with this problem (being that my computer doesn't start up past the grub loader)

---

### Post by aheckler on 2009-10-09
You need to download Super GRUB Disk and use Fix MBR. Check [here]("http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html").

Edit: **DO NOT DO THIS!** See [this reply]("http://ubuntuforums.org/showpost.php?p=8080691&postcount=4") instead.

---

### Post by cholericfun on 2009-10-09
alternativly put the windows disk inside and go into recovery mode (or whatever it is called) and get yourself to a terminal where you can type 
fixmbr

---

### Post by presence1960 on 2009-10-09
> **cholericfun said:**
> alternativly put the windows disk inside and go into recovery mode (or whatever it is called) and get yourself to a terminal where you can type 
fixmbr

**_fixmbr is for XP not Vista._**

boot your Vista disk and follow the instructions for Vista [here]("http://ubuntuforums.org/showthread.php?t=1014708") to put Vista back on MBR.

If you don't have a Vista disk you can download an iso and burn it to CD which will allow you to boot into Vista Recovery console and perform the instructions above. get it [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

---

### Post by aheckler on 2009-10-09
Shoot, you're right! I guess I didn't read the OP as close as I should have. I'll edit my post accordingly.

---

