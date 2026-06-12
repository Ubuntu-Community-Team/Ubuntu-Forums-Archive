---
title: "using GRUB instead of the windows boot loader"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by coldfusion1313 on 2009-08-30
I installed Ubuntu 9.04 on my laptop and I want to install Windows XP too. I know when I install windows it uses it own boot loader, can i reinstall grub over it?

---

### Post by presence1960 on 2009-08-30
> **coldfusion1313 said:**
> I installed Ubuntu 9.04 on my laptop and I want to install Windows XP too. I know when I install windows it uses it own boot loader, can i reinstall grub over it?

Install windows. it will overwrite the MBR with it's own bootloader. To restore GRUB to MBR follow this 30 second process:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

In #6 use setup (hd0) to put GRUB on MBR if you have only 1 hard disk.

---

### Post by coldfusion1313 on 2009-08-30
thanks it help a lot

---

