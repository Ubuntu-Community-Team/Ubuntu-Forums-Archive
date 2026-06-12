---
title: "partition name changed"
date: 2008-10-15
forum: General Help
---

### Post by matiw on 2008-10-15
hi,
i installed ubuntu 8.04 in a partion. later something happend and parition name changed(eg form sda3 to sda7). 

well, to solve this problem i replaced, on menu.lst, the old name. 

since then everything was ok, but yesterday i updated the linux-header and 

when i rebooted it asked me for the older partion name.

i want to know what i have to do, so next update it will aks for the new partiton name.

---

### Post by Pro-reason on 2008-10-15
Instead of /dev/xxx, use LABEL=xxxxxxx.  It is more robust.

---

### Post by Rocket2DMn on 2008-10-15
I use UUIDs in /etc/fstab rather then /dev/ entries, and you can label your drives by following directions on this wiki page: [uhelp]community/RenameUSBDrive[/uhelp] (it works on internal drives, too).

---

### Post by matiw on 2008-10-15
i forgot to say that the partition name that i was talking about is the ubuntu-boot partition. does labeling work anyway?

---

### Post by jerome1232 on 2008-10-15
> **matiw said:**
> i forgot to say that the partition name that i was talking about is the ubuntu-boot partition. does labeling work anyway?

Yes labeling works on any partition with a file system.

---

### Post by matiw on 2008-10-16
thanks, ill try it

---

### Post by geirha on 2008-10-16
For it to stick in menu.lst, you need to change the line that reads
```
# kopt=root=/dev/sda3 ro
```
to something like
```
# kopt=root=UUID=<uuid-string> ro
# kopt=root=LABEL=<label> ro

```

Everytime a kernel is removed or installed, a script called update-grub is run (you can run it manually too, with sudo)

update-grub removes all entries between 

### BEGIN AUTOMAGIC KERNELS LIST
### END DEBIAN AUTOMAGIC KERNELS LIST

And creates new entries for all installed kernels, using the values from those commented options inside the automagic kernels list. If you didn't change that kopt-line last time, then that's the reason why your change was lost. It's a good idea to always run **sudo update-grub** after editing menu.lst. That way you'll avoid such surprises in the future.

---

