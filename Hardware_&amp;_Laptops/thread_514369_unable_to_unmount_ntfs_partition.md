---
title: "unable to unmount ntfs partition"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by Chymera on 2007-07-31
i made a previous thread on the exct same issue but accidentally typo-ed the threads name so badly, that it is incomprehensible, consequently almost no one went through it; i tried to modify it, and found out that it cant be done :(

[http://ubuntuforums.org/showthread.php?t=514055](http://ubuntuforums.org/showthread.php?t=514055)

---

### Post by zidane2 on 2007-08-01
sudo umount /dev/sda1
should work

---

### Post by Chymera on 2007-08-02
hmmm, 
> sudo umount /dev/sda1 
gives the following output
> umount: /dev/sda1: not mounted

however, > sudo umount /media/sda1 seems to work
but why cant i umnount it through rightclick->unmount or in gparted?

furthermore, to get it back on i cant use 
> sudo mount /media/sda1 i have to use > sudo mount /dev/sda1
I find that quite suspicious since i needed to mention the other location in order to unmount it

---

### Post by merlinus on 2007-08-02
IIRC, a partition is unmounted via its mount point, and has to be done as root.  That's why right-clicking does not work.

To mount again, it has to been done as a device, not a mount point.

-merlin

---

### Post by Chymera on 2007-08-03
10x 4 the info, however gparted is run as root.... how come i cant unmount it from gparted?

---

### Post by merlinus on 2007-08-03
Perhaps it is in use?

-merlin

---

### Post by Chymera on 2007-08-03
then why does it work problemless through command line in the exact same circumstances?
btw, even if i unmounted it i seemed to be unable to resize it :(

---

### Post by merlinus on 2007-08-03
If you are wanting to re-size partitions, best to use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It has new features and capabilities that are superior to the version on the ubuntu live cd.

-merlin

---

### Post by Gremlinzzz on 2007-08-03
if all else fails type xkill in terminal then click what you want to kill.
the root command i like is gksudo nautilus  gives complete control in files drag drop delete the whole nine yards.:guitar:

---

