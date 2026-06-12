---
title: "installing fedora9 made ubuntu unreachable"
date: 2008-07-21
forum: General Help
---

### Post by chriskin on 2008-07-21
i installed fedora 9 on a partition of my laptop (fujitsu siemens amilo xi 2428 in case it matters) and fedora replaced the boot loader, causing ubuntu to be unreachable, even though windows were recognised perfectly

is there any way i can solve this, preferably through fedora since i do not have a live cd for ubuntu (if not, i can download it in minutes )

---

### Post by lesergi on 2008-07-21
Hi!

You must add Ubuntu entry in grub configuration.

You can do it editing the file /boot/grub/menu.lst:

```
gksu gedit /boot/grub/menu.lst
```

And add this in final file:

```

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic

```

This is my Grub Ubuntu entry. You must change the needed options.

If you want to be helped better, please, copy the next output (as root):

```
fdisk -l
```

Bye!

---

### Post by chriskin on 2008-07-21
those commands seem to work on ubuntu but not on fedora, i will visit fedora forums and get the same commands for fedora and i will post the outcome

thanks :D

---

### Post by chriskin on 2008-07-21
anyway, i do not really like fedora

i will delete it

---

### Post by bobbob1016 on 2008-07-21
Instead of "gksu ..." do "su -" then enter your password, then do "..." or whatever the ... is.

---

### Post by sisco311 on 2008-07-21
try:
```
su    #enter the root password
 gedit /boot/grub/menu.lst
exit
```mount the ubuntu partition and copy/paste the menu entry 
from the ubuntu menu.lst

---

### Post by chriskin on 2008-07-21
this seems to work
thanks everyone :D

---

