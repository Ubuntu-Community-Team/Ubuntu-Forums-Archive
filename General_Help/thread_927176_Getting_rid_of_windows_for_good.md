---
title: "Getting rid of windows for good"
date: 2008-09-22
forum: General Help
---

### Post by Monotoko on 2008-09-22
Hiya guys, just wondering how to get rid of the GRUB loader and make it auto-boot into ubuntu? I no longer have a need for windows, especially vista, and would like it gone -.-

---

### Post by Hyper Tails on 2008-09-22
I don't think you can get rid of the grub loader but all you need to do to get rid of vista is to delete that partition (don't worry it won't hurt you're grub loader
and after you delete that partition got to

root/boot/grub/menu.lst

and delete the following that is under this

```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

delete this:
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

i hope this help ;)

note:
when you delete the vista partiton on your pc you can't resize the partition on the partition that you installed ubuntu on
 i suggest you installed open suse on that partiton (just for advice)

---

### Post by retrow on 2008-09-22
Grub is the bootloader and is essential component in the booting process. Removing grub would result in an error at the very beginning.

---

### Post by WRDN on 2008-09-22
To automatically boot into the default boot option in the GRUB menu, open the terminal and type:

```
sudo gedit /boot/grub/menu.lst
```

Now, find the line "timeout 10" (note the number may be different). Change the number to 0 to stop GRUB appearing.

---

### Post by ryanhaigh on 2008-09-22
Rather than deleting anything just change the timeout in /boot/grub/menu.lst to 1 (or 0 if you really want) and uncomment the hidemenu line
> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu


Also make sure the default value is set to 0 (which should be your ubuntu kernel) as shown above.

---

### Post by lisati on 2008-09-22
> **ryanhaigh said:**
> Rather than deleting anything just change the timeout in /boot/grub/menu.lst to 1 (or 0 if you really want) and uncomment the hidemenu line


Also make sure the default value is set to 0 (which should be your ubuntu kernel) as shown above.

+1. And don't forget that the most important words when tinkering with the configuration of your system's OSes  are "Backup", "Backup" and "Backup"

---

