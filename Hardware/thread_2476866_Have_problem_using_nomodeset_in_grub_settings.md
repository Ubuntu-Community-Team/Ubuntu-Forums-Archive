---
title: "Have problem using nomodeset in grub settings ?"
date: 2022-07-09
forum: Hardware
---

### Post by aug7744 on 2022-07-09
Thanks for read my topic.
I has installed Nvidia binary driver working correctly.
I had added in /etc/default/grub the setting before installing the driver
GRUB_CMDLINE_LINUX="nomodeset"
thus not is loaded the nouveau driver

Have any problem using the "nomodeset" setting in kernel ?
Have an nice day.

---

### Post by oldfred on 2022-07-09
You typically do not add nomodeset to /etc/default/grub
It is automatically added to recovery mode, or is manually added as you boot, only until you install the correct nVidia driver.
Newest versions of Ubuntu let you choose to automatically install restricted drivers as part of install now including the nVidia driver. The ppa is now not normally required to get correct driver. 
You usually have to use Safe boot option to have video work correctly when using the live installer.

If changing nVidia driver, you must purge all old drivers as installing new does not do the purge & you end up with conflicts.

[FONT=monospace]If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)



[/FONT]

---

### Post by aug7744 on 2022-07-10
Thanks for your help.
Exactly need add "nomodeset" to grub before installing Nvidia driver because nouveau is loaded from initramfs.
I only need understand if using "nomodeset" in grub can create problems in video acceleration, security or etc.

---

