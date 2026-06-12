---
title: "make ubuntu start with noapic"
date: 2008-11-09
forum: General Help
---

### Post by 2j4ez on 2008-11-09
Ive just build a system amd64 1640 1gb ram geforce graphics When i use the live CD i have to add the option noapic to get the live cd to boot

It installed fine but runs a little slow maybe my HDD its a old 40gb ide one i had lying around (will get a new one when i get paid)

Each time i boot i have to add noapic or i get a kernal panic
how/where do i add noapic to get it boot with out entering anything on startup

thanks

---

### Post by teddks on 2008-11-09
Go into the file /boot/grub/menu.lst and find this section:

```
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/mapper/main_lvm-root ro

```

Uncomment the last line and add what you want (noapic in this case).

NOTE: Your line there won't look like mine.

---

### Post by 2j4ez on 2008-11-09
Found it and it wont let me save it (i'm still new to ubuntu) maybe its me 
It says I dont have permissions to save it

---

### Post by teddks on 2008-11-09
That's because you don't. Whenever you're editing a file outside of your home directory (/home/username) or the /tmp folder (assuming you own the file in /tmp) you need to be root. You can temporarily ascend to root with the 'sudo' command.

So instead of doing something like this:
```
 gedit /boot/grub/menu.lst
```

You need to append 'sudo' to run the command as root (to **do** the command as a **s**uper **u**ser), like this:

```
 sudo gedit /boot/grub/menu.lst
```

---

### Post by CatKiller on 2008-11-09
Typo in there, sorry. And for reasons explained [here]("http://www.psychocats.net/ubuntu/graphicalsudo"), it's best to use gksudo for graphical applications. So ```
gksudo gedit /boot/grub/menu.lst
``` would be better.

---

### Post by slimaxlel on 2008-11-10
Make sure you're using the 64-bit install CD.  
I got the same error on my new AMD box when I was using the 32-bit version.

---

