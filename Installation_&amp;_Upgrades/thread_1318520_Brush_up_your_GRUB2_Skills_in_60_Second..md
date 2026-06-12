---
title: "Brush up your GRUB2 Skills in 60 Second."
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by SilverWave on 2009-11-07
GRUB 2 is the default boot loader for Ubuntu 9.10 Karmic.
So before installing you may want to brush up your GRUB skills by taking the 60 second tour below :)

Note:
====
If the menu is hidden at bootup "shift" will show it (not esc).
In GRUB 2 there is no menu.lst 
GRUB 2 counts the first drive as 0, the first partition as 1.
e.g: If the Ubuntu system is on sda5, enter: set root=(hd0,5)
The StartUp-Manager gui package works with GRUB 2

Important files and locations
==================

/etc/grub.d/
Scripts that "sudo update-grub" runs in order to recreate /boot/grub/grub.cfg

/etc/grub.d/40_custom
Put your stuff in here if needed.

/etc/default/grub
GRUB 2 Menu settings.
e.g.
GRUB_TIMEOUT="3"
After any changes run "sudo update-grub".

/boot/grub/grub.cfg
View only - not to be altered manually.
"sudo update-grub" runs the scripts in /etc/grub.d/ to rebuild this file.
An example menu item:

menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c73a37c8-ef7f-40e4-b9de-8b2f81038441
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c73a37c8-ef7f-40e4-b9de-8b2f81038441 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}

Great howto by drs305 at: [https://help.ubuntu.com/community/Grub2/](https://help.ubuntu.com/community/Grub2/)

---

### Post by bapoumba on 2009-11-08
Moved to Installation & Upgrade.

---

