---
title: "Boot Ubuntu after installing Windows"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by stevenroose on 2009-01-03
Hi,

I had Ubuntu and Windows both installed on my computer, but the Windows, like always started to really slow down. So I re-installed it. But when booting up my pc, Windows now starts automatically without showing the GRUB Loader.
Now cleaned the Windows partition temporary to be able to boot Ubuntu again.

Does anyone knows how to install Windows (on another partition) but still having Ubuntu managing the Boot Loading??

thanks in advance,

Steven Roose

---

### Post by tommcd on 2009-01-03
If you dual boot Windows and Ubuntu, Windows should be installed to the 1st primary partition on your hard drive. Then install Ubuntu to a primary or logical partition on your hard drive after installing Windows. If you reinstall Windows after installing Ubuntu, Windows will overwrite your master boot record and you will no longer be able to boot Ubuntu. To reinstall grub to the master boot record and be able to see the grub menu and choose between booting Windows or Ubuntu on bootup follow the instructions here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by wpshooter on 2009-01-03
Always install M/S windows O/S first, then install Ubuntu afterwards/second.

---

### Post by stevenroose on 2009-01-03
> **wpshooter said:**
> Always install M/S windows O/S first, then install Ubuntu afterwards/second.

I'm not gonna re-install my working Ubuntu just to re-install Windows...

> **tommcd said:**
> If you dual boot Windows and Ubuntu, Windows should be installed to the 1st primary partition on your hard drive. Then install Ubuntu to a primary or logical partition on your hard drive after installing Windows. If you reinstall Windows after installing Ubuntu, Windows will overwrite your master boot record and you will no longer be able to boot Ubuntu. To reinstall grub to the master boot record and be able to see the grub menu and choose between booting Windows or Ubuntu on bootup follow the instructions here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Thanks!
Gonna try asap, but should be working I think.

---

