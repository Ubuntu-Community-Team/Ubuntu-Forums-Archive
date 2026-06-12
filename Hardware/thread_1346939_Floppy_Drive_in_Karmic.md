---
title: "Floppy Drive in Karmic"
date: 2009-12-05
forum: Hardware
---

### Post by deamon_knight on 2009-12-05
I'm trying to get Floppy support in Karmic. I've seen that several threads reporting problems but I haven't found a solution.

My floppy Drive works, i've flashed the BIOS from it, I can read & write in PuppyLinux, and after adding floppy to /etc/modules, I can 'mount /dev/fd0' and access it. However, I cannot use the entry in nautilus' file browser to access the floppy drive. It consistently reports no media, even after the floppy drive is successfully mounted from CLI. The same is true in palimpset. I've also noticed that the default user account has not been added to the floppy group, although adding the user to this group does not solve the problem either. Any suggestions on how to get this working properly?

Thanks

---

### Post by Vampire0 on 2009-12-12
I have excatly the same problem, except that I don't need to add floppy to /etc/modules to mount the floppy from command line, this works right from the start. This is a freshly installed Karmic on a freshly assembled box.

---

### Post by TitanusEramius on 2009-12-12
Almost the same here on Karmic, but after i mounts fd0 from cli, Nautilus stops saying that the fdd is empty and works fine. I actually thought my fdd was dead, so this is kinda good news

---

### Post by deamon_knight on 2009-12-17
Still no solution Huh?

---

### Post by n.hinton on 2010-01-09
As a dirty workaround, I added my username to floppy group (check box) created a launcher in my system menu: type: Application, Name: Mount Floppy, Command: mount /dev/fd0, Icon: /usr/share/icons/gnome/scalable/devices/3floppy_unmount.svg

patience is required as its slow, but works on my karmic

When done with floppy, right click desktop icon and unmount

---

### Post by mhampson on 2010-03-24
Found a simpler solution to a similar problem (not ideal but quick and it works) - try:

sudo nautilus

---

### Post by and003 on 2010-08-21
Anyone who may still have floppy mounting issues can try this solution:
[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571)

---

