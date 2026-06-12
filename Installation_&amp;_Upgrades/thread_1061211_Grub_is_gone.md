---
title: "Grub is gone?"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by y0umebednow on 2009-02-05
So im trying to Re-install XP on my laptop which currently has ubuntu 8.10 and windows XP in dual boot. i know when i install XP again, the grub will be gone and i wont be able to boot into Ubuntu. So, im trying to back up the menu.lst but when i type in sudo gedit /boot/grub/menu.lst. into the terminal, the file menu.lst comes up but it is blank. no letters, numbers, or symbols. So how do i go about doing this task?

Thank you

---

### Post by Elfy on 2009-02-05
You don't need to back it up - it doesn't delete the file - it just writes it's onw unsharing bootloader to the mbr - all you need to do is reinstall grub with your livecd

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by dstew on 2009-02-05
It sounds like gedit is trying to create a new menu.lst file. I am not sure why. One possibility: gedit is a gnome graphical editor. Perhaps the sudo command is not giving it root privleges. Usually, for a gnome program, you need to do **gksudo** instead of sudo. Press Alt-F2 to get a graphical command line, then enter```
gksudo gedit /boot/grub/menu.lst
```and see if that works.

---

### Post by Elfy on 2009-02-05
Of course if you want to back a file up - use cp

```
sudo cp /path/to/file /path/to/backup
```

Like

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.0502
```

---

