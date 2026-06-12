---
title: "Need help."
date: 2008-10-31
forum: General Help
---

### Post by marzik on 2008-10-31
Im very new to Ubuntu and thought i'd give it a try and use it on a lap top i use for downloading, off my very old lap top a
HP Compaq nc 6120 i downloaded the ubuntu and burned it to dvd 
Intall went awsome. A month later having time to play with this Lap top i can not remember the pass word i used.   How do i uninstall this ubuntu  with out access to the system. 

I will be reinstalling the same version of ubuntu then updating and going with the same plan  using it for a download machine. 


Please help me out by either, info on uninstall or password recovery    lol    i know im a tard.

---

### Post by geirha on 2008-10-31
Turn on your laptop, and when grub loads, hit Esc to show the menu. In the menu select the second entry, which should be a recovery entry. Once booted, you will be given a few choices, choose to get a root shell. Once in the root shell, type ```
passwd *yourusername*
``` to change the password for *yourusername*. Reboot and enjoy.

---

### Post by marzik on 2008-10-31
ok pressed esc. took me to a kerrnal loading screen pages
then the command at the bottom of the page was give root password for maintenance or press control + d to reboot to normal gnome load  nothing still hitting a password protected area . linux mint  Gnome is the version

---

### Post by Wayne_V on 2008-10-31
Yes, later versions of ubuntu require a password on booting recovery mode.

You can try one of:

1) Edit the grub boot line and add "init=/bin/bash"

2) boot the LiveCD, mount your root file system, vi etc/passwd and etc/shadow (on the hard disk, not the ramfs the liveCD runs from) and remove clear the passwd field.

see: [http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

---

### Post by geirha on 2008-10-31
> **Wayne_V said:**
> 
2) boot the LiveCD, mount your root file system, vi etc/passwd and etc/shadow (on the hard disk, not the ramfs the liveCD runs from) and remove clear the passwd field.


Instead of editing /etc/passwd and /etc/shadow manually, I'd open a terminal and run chroot on the mount-point, then run passwd

```
sudo chroot /media/disk
passwd *username*
```

---

