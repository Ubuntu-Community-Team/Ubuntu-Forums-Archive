---
title: "Transfer Hard Drive"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by markster80 on 2009-07-25
Installed Ubuntu 9.04 a few months ago on a previous computer.  Dual boot with Ubuntu on a dedicated hard drive and XP on a separate hard drive.  I want to physically remove the Ubuntu drive and install it into my new computer but when I tried the old computer (which is being used by someone else) would not boot directly to windows.  It stated "GRUB ERROR 21" and remained idol.

Is there any way to do this and save all my Ubuntu files and programs and re-set the previous computer to boot to windows.

Thanks,
Mark

---

### Post by balaknair on 2009-07-25
To fix the Windows boot problem,
Boot from the XP CD, and choose the recovery option at the setup screen by pressing 'R'. This will now present a list of drives with Windows installations, (you may be asked for an admin password). You now get to a command prompt screen, type in the command FIXMBR, confirm when asked(by pressing Y), and exit. Now boot without the CD in the drive and the XP install should boot properly.

To boot from Ubuntu on your new computer, you might need to reinstall GRUB.
I'm not too sure how well that would work in your case, but I think you will find this guide helpful
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

