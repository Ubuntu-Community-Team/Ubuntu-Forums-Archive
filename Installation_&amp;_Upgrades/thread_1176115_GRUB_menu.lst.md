---
title: "GRUB menu.lst"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by ceduriki on 2009-06-02
I accidentally deleted the menu.lst file for GRUB. I tried reinstalling GRUB from the live CD but this didn't rewrite the menu.lst to default. What should I do?

---

### Post by pastalavista on 2009-06-02
follow the instructions from this post
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by ceduriki on 2009-06-02
Yeah, that's what I did to reinstall GRUB. Didn't reset the menu.lst to default.

---

### Post by pastalavista on 2009-06-02
Hmmm.. that's strange. I'm not sure what you mean, did it leave out previous kernels maybe? You might try downloading and burning a [Super Grub Disk]("http://www.supergrubdisk.org")

---

### Post by ceduriki on 2009-06-02
> **pastalavista said:**
> Hmmm.. that's strange. I'm not sure what you mean, did it leave out previous kernels maybe? You might try downloading and burning a [Super Grub Disk]("http://www.supergrubdisk.org")

Well, SuperGrub is down, but I'll keep checking.  
And what I mean is that the menu.lst file is blank and won't go back to default.

---

### Post by pastalavista on 2009-06-02
> **ceduriki said:**
> Well, SuperGrub is down, but I'll keep checking.  
And what I mean is that the menu.lst file is blank and won't go back to default.

OK I see what you mean. Have you tried browsing with nautilus to the /boot/grub directory? There may be a backup menu.lst~ file there you can rename to menu.lst otherwise, Super Grub is probably your best bet. The download is [mirrored here]("http://forjamari.linex.org/frs/download.php/1186/super_grub_disk_0.9797.iso")... good luck

---

### Post by ceduriki on 2009-06-02
> **pastalavista said:**
> OK I see what you mean. Have you tried browsing with nautilus to the /boot/grub directory? There may be a backup menu.lst~ file there you can rename to menu.lst otherwise, Super Grub is probably your best bet. The download is [mirrored here]("http://forjamari.linex.org/frs/download.php/1186/super_grub_disk_0.9797.iso")... good luck

So what do I do once I get the disk running?

---

### Post by pastalavista on 2009-06-14
I bet you've already figured it out by now, but you just select from the list of options, the setup that matches yours, and it will set it up for you. Sorry I didn't get back to you sooner.

---

### Post by presence1960 on 2009-06-14
> **ceduriki said:**
> Yeah, that's what I did to reinstall GRUB. Didn't reset the menu.lst to default.

that set of commands is used to restore GRUB. the comand find /boot/grub/menu.lst only searches for the menu.lst file. Sadly you don't have one because you deleted it. Hopefully you have a backup. All you need to do is put the backup back in the right directory and make sure the filename is correct.

If you don't have a backup of menu.lst try this : [https://help.ubuntu.com/8.04/installation-guide/i386/rescue.html](https://help.ubuntu.com/8.04/installation-guide/i386/rescue.html)

---

