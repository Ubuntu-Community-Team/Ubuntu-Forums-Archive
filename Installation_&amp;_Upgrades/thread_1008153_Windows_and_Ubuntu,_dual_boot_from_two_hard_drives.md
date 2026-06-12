---
title: "Windows and Ubuntu, dual boot from two hard drives - windows boot hangs..."
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by slayer^_^ on 2008-12-11
This happened to me, hope it can be useful to everybody...

The question is this...

I've got Ubuntu on my primary hard drive and windows on hte secondary... after an installation of Ubuntu 8.10 Intrepid Ibex, grub is able to recognize the Windows installation but isnot able to boot it or, better, the boot hangs...

This is the solution, it should work for everybody:

This is a permanent solution. After having done it you will no longer have to edit menu.lst.

Just type in the console:

```
sudo gedit /boot/grub/menu.lst
```

You should search for a piece of code very similar to this one:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

and write this one instead of it (i suggest to ADD these lines instead of replacing them, you can inactivate the former ones by putting a #before them... so you can go easily back to the original menu.lst file if you want!):

```
title           Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify            (hd1,0)
makeactive
chainloader     +1
boot
```

This way you can check if Windows boots... Of course it is a very empiric solution, you better know your partition table before, but it works in most of the cases...

For more info, this website is very useful...

[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by lametike on 2008-12-11
two hard disk? thats not call dual boot.

---

### Post by slayer^_^ on 2008-12-11
i don't decide which hard disk to boot, i use grub... that's the difference ;)

---

