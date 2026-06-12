---
title: "Boot problem with 9.10"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by Chromos on 2009-10-19
Hi,

while booting it stucks at the splashscreen ang gives me this

> Check cryptops=source=bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev -r
Alert! /dev/by-uuid/Ocafa742-69c-4(usw...) does not exist. Dropping to Shell!

BusyBox Version ....

I checked the UUID of the bootpartition and it isnt equal to the one in the error:
> sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda5: UUID="40916d54-8a77-41b3-863e-0171c0197ec6" TYPE="ext2"

Do I have to change it anywhere?

greeting chromos

---

### Post by dabl on 2009-10-19
Are you booting a Live CD?  If yes, then it sounds like a defective CD.

Check the downloaded ISO image md5sum, and make sure it matches the one on the download site.  Then burn it at your slowest burn speed, "DAO" mode if that is available.

---

### Post by Chromos on 2009-10-19
no Im booting from HD. And Ive got the problem since an upgrade from ubuntu 9.04 to 9.10.

---

### Post by gare on 2009-10-21
Hello -

I have same problem.  Is there a resolution?

Thanks.

---

### Post by pearcec on 2009-11-01
Looks like a known issue, I wish I knew why though.

[https://help.ubuntu.com/community/KarmicUpgrades#Unable%20to%20Load%20Linux%20Drive](https://help.ubuntu.com/community/KarmicUpgrades#Unable%20to%20Load%20Linux%20Drive)

---

