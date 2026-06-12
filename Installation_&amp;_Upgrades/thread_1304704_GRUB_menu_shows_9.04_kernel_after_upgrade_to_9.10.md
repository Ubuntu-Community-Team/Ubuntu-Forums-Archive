---
title: "GRUB menu shows 9.04 kernel after upgrade to 9.10"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by hetx on 2009-10-29
If you do an upgrade to 9.10 via the update manager you run the risk of ending up with a non-updated /boot/grub/menu.lst, grub menu. I'm guessing this is due to the switch to GRUB 2 (that only applies to new installs, not upgrades.

This will make you boot 2.6.28-14/15, instead of the new 2.6.31-14 kernel, which can result in hardware failures, such as sound or wireless. To solve the problem you can manually update menu.lst.

WARNING: if you accidentally ruin /boot/grub/menu.lst you will need a LiveCD to fix it. Make sure you have one available.
```
gksu gedit /boot/grub/menu.lst
```

It's a good idea now to save the original file as menu.lst.bak

Scroll down to the entry for your first kernel, starting with "title Ubuntu 9.04". Copy this whole entry (including uuid, initrd and so on) and the recovery mode and paste it just above the first entry. Change the kernel and the initrd to /boot/vmlinuz-2.6.31-14-generic and /boot/initrd.img-2.6.31-14-generic

The end result looks like this in my menu.lst: (ps, use your own uuid!)
```
title       Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        6e08943a-8da4-4b93-8d5b-440e954dba61
kernel      /boot/vmlinuz-2.6.31-14-generic root=UUID=6e08943a-8da4-4b93-8d5b-440e954dba61 ro vga=795 splash quiet
initrd      /boot/initrd.img-2.6.31-14-generic
quiet

title       Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
uuid        6e08943a-8da4-4b93-8d5b-440e954dba61
kernel      /boot/vmlinuz-2.6.31-14-generic root=UUID=6e08943a-8da4-4b93-8d5b-440e954dba61 ro  single
initrd      /boot/initrd.img-2.6.31-14-generic
```


Hopefully devs will fix this soon, but if you can't wait, good luck =)

---

### Post by shaggy999 on 2009-10-29
EDIT: Nevermind, misread.

---

### Post by brel on 2009-10-31
Thanks for the comment!! I had the same problem and now my sounds working again and I'm hoping the rest as well.

This seems like a fairly major problem and I'm surprised there isn't some big warning somewhere. I took me a while to stumble on this msg.

---

### Post by Manksman on 2009-10-31
I had the same problem too, now fixed with an edit of menu.lst, however as soon as I had rebooted the desktop was blank, except for the tool bars. Firefox blanks out too if maximised, I can get it to about 2/3rds of the screen before it goes. very strange. I guess if I go back to the old kernel I can have my desktop back but no sound!

---

### Post by hetx on 2009-11-01
May be way off but check if your proprietary Hardware Drivers are still activated. System -> Administration -> Hardware Drivers

With the new kernel you have to reactivate the drivers.

---

