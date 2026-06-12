---
title: "Problem with Grub, since installing another distro"
date: 2008-08-19
forum: General Help
---

### Post by Muppeteer on 2008-08-19
Ok, so i've been running Ubuntu alonside Windows on the same drive now for quite a while. And for some reason i decided to give Fedora a try on another drive. So i installed grub on that other drive too, with the idea that i could just boot from different drives with seperate grubs.

Not the case. When i tried going into Ubuntu, grub gave me the errors:
"Error 22: No such partition"

And when i tried to boot XP
"Error 13: Invalid of unsupported executable format"

So i booted back into Fedora and added Ubuntu into the /boot/grub/menu.lst. This works, but i'm afraid if i want to get rid of Fedora, will i still have this problem? And would it just be as simple as booting from a live cd to reinstall grub?

Are both installations of grub conflicting somehow, or is Fedora version overriding it?

---

### Post by meindian523 on 2008-08-19
Fedora version has overwritten Ubuntu's Grub.If you delete Fedora,you lose Grub and have a non-booting box of electronics.To solve that(future) case,see
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Muppeteer on 2008-08-19
Thanks, that's what i thought but seems weird it would overwrite something on a completely different drive :confused:

---

### Post by meindian523 on 2008-08-19
I'm assuming you installed Grub to the MBR?

---

### Post by Muppeteer on 2008-08-19
Yeah but on a different drive...

---

### Post by caljohnsmith on 2008-08-19
Please run the following commands and post the output, because they will help deduce which partition (distro) is controlling the MBR of your HDDs:
```
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
```
And also post the output of:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
grub> find /boot/stage1
grub> find /grub/stage1
grub> geometry (hd0)
grub> geometry (hd1)
grub> quit
```

---

