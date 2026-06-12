---
title: "adding a 2nd hard drive"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by dog-soldier on 2009-09-24
i have 2 hard drives for this computer, 1 ubuntu 8.04 and the other windows xp. i want to hook both up so i can chose between them instead of unhooking and rehooking.
which drive should go where or will i need to reinstall ubuntu which i hope i dont.

---

### Post by rreese6 on 2009-09-25
you can hook both of the drives up. put ubuntu first then windows.
boot into ubuntu and edit the file menu.lst in the /boot/grub folder.
in terminal type:
```
cd /boot/grub
sudo gedit menu.lst
```

if you get an error about gedit not found, you can install it or just use nano to edit the file.

```
sudo nano menu.lst
```

you will need to add the windows information to make it dual boot.
you will add this to the bottom of the file.

```

title Windows XP
root (hda1,0)
makeactive
chainloader +1
```


Save the file then reboot, Windows should now be in your grub menu.

If that doesn't work for you, you may have to restore the grub.
here is a good link to do that:

[http://gwos.org/udsf/doku.php/core:grub:restore]("http://gwos.org/udsf/doku.php/core:grub:restore")

---

