---
title: "USB installation destroyed my GRUB"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by zmA on 2009-02-18
I was attempting to install a copy of Ubuntu onto a USB thumb drive as a "PC on a keychain."  I used the 8.10 live CD and the install went fine, except that when I boot the computer it now seeks the GRUB file on the USB drive instead of the internal HD.  If I don't have the USB plugged in, all I get is an "error 17" when the computer is looking for GRUB.  

How do I point the computer towards the correct drive on boot?

Many thanks!

---

### Post by lha on 2009-02-18
You'll have to reinstall Grub. See [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") for instructions. However, do not use the Super Grub Disk method, because the Grub version that comes on Super Grub Disk does not support uuid -command.

---

### Post by caljohnsmith on 2009-02-18
You need to install Grub to the MBR (Master Boot Record) of the USB drive, and then restore a Windows MBR to your Windows drive. You can do that via the directions in either of these threads:

[http://ubuntuforums.org/showthread.php?p=6665548](http://ubuntuforums.org/showthread.php?p=6665548)
[http://ubuntuforums.org/showthread.php?p=6452340](http://ubuntuforums.org/showthread.php?p=6452340)

Let me know how that goes or if you run into problems.

---

### Post by zmA on 2009-02-26
Thanks!  I will let you know if I run into any problems.

---

### Post by adrian15 on 2009-03-10
> **lha said:**
> You'll have to reinstall Grub. See [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") for instructions. However, do not use the Super Grub Disk method, because the Grub version that comes on Super Grub Disk does not support uuid -command.

Super Grub Disk should recover Grub even if it does not support uuid.

Super Grub Disk might boot or not boot your Linux depending on which Boot Linux option you use, that's true.

Do you know or have lived any Super Grub Disk Grub's fix that has failed? Can you please post a link or just write about it here?

Thank you very much for your feedback!

By the way I plan to include uuid support but in the mid-term.

adrian15

---

### Post by zmA on 2009-03-10
I've resolved this problem.  Many thanks to all who responded.

---

### Post by lha on 2009-03-12
> **adrian15 said:**
> Super Grub Disk should recover Grub even if it does not support uuid.

Super Grub Disk might boot or not boot your Linux depending on which Boot Linux option you use, that's true.

Do you know or have lived any Super Grub Disk Grub's fix that has failed? Can you please post a link or just write about it here?

Ok, I didn't know that. Thanks for pointing it out.

I haven't encountered any problems caused by Super Grub Disk, but installing non-Ubuntu Grub may lead to problem (due to the lack of uuid support). Nevertheless, as adrian15 mentioned, Super Grub Disk can recover Ubuntu's Grub.

> **zmA said:**
> I've resolved this problem.  Many thanks to all who responded.

I'm glad to hear you were able to fix it.

---

