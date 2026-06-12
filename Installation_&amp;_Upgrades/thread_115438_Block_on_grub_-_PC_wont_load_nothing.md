---
title: "Block on grub - PC wont load nothing"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by mschievano on 2006-01-10
Hello,
tonight when i power UP the PC, after the initial test to blue Q (on capital and one not) like this:
[COLOR="Navy"]Q             q[/COLOR]
appears instead of grub loader, nd the PC wont reboot even if i press CTRL ALT CANC.

Now i'm writing with a knoppix live.

How can I reinstall the ubuntu Grub leaving my boot menu untouchable ? (I have several kernel edition)

thanks

------
think I have resolved:

mount -t -o rw auto /dev/hda2 /mnt/hda2
chroot /mnt/hda2 /bin/bash
grub-install

-------

IT WORKS!

---

### Post by Sef on 2006-01-10
Thank you for supplying an answer.  I am sure it will be used by others at some point in the future.

---

### Post by mschievano on 2006-01-11
[QUOTE=Sef]Thank you for supplying an answer.  I am sure it will be used by others at some point in the future.[/QUOTE]

this is the correct lines:

[FONT="Century Gothic"][COLOR="DarkRed"]mount -t auto -o rw dev/hda2 /mnt/hda2
chroot /mnt/hda2 /bin/bash
grub-install /dev/hda[/COLOR][/FONT]

sometimes it redo the problem! Bha....

---

