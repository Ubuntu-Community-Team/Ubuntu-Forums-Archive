---
title: "execute sh file"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by vze57gc8 on 2009-01-10
i in the process of putting bt3 on a usb i must run "bootinst.sh" 
in the terminal i run 
craig@Playtoy:~$ chmod +x bootinst.sh
chmod: cannot access `bootinst.sh': No such file or directory

any1 have an idea of what to do?

---

### Post by natetheskate on 2009-01-10
did you use the cd command to navigate to the bootinst.sh file first?

---

### Post by chex_m8 on 2009-01-10
check to make sure you have execute permission for the file, ls -l
it looks like you missed something in your command
you typed
    craig@Playtoy:~$ chmod +x bootinst.sh
try this
    craig@Playtoy:~$ chmod a+x bootinst.sh

---

### Post by vze57gc8 on 2009-01-10
# cd /media/disk/boot
nothing happens

craig@Playtoy:~$  chmod a+x bootinst.sh
chmod: cannot access `bootinst.sh': No such file or directory

---

### Post by albinootje on 2009-01-10
> **vze57gc8 said:**
> i in the process of putting bt3 on a usb i must run "bootinst.sh" 
in the terminal i run 
craig@Playtoy:~$ chmod +x bootinst.sh
chmod: cannot access `bootinst.sh': No such file or directory


Did you follow the instructions exactly, or wherever appropriate to your setup ?

I assume you're following this :
[http://forums.remote-exploit.org/showthread.php?t=14486](http://forums.remote-exploit.org/showthread.php?t=14486)

The error message 
> 
chmod: cannot access `bootinst.sh': No such file or directory

might mean that you're simply in the wrong directory, and that the file bootinst.sh cannot be found.

---

### Post by chex_m8 on 2009-01-10
can you post the output of ls -l /media/disk/boot

---

### Post by vze57gc8 on 2009-01-11
cd and ./bootinst.sh did the trick
thx alot guys

---

