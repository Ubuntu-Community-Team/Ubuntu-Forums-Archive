---
title: "Looking for command"
date: 2008-11-18
forum: General Help
---

### Post by marcusau2 on 2008-11-18
I am looking for 2 commands, one that will give me read write access to the file viewer (Nautilus) as root so I can drag and drop files and also a command for the terminal that will enable me to give write permissions to an individual folder.  Thanks

---

### Post by philinux on 2008-11-18
gksudo nautilus

then right click properties, permissions

Be careful, here be dragons. :lolflag:

---

### Post by Battalion on 2008-11-18
The solution for nautilus is posted by philinux, but for the command for the terminal its rather more complicated.

In konsole, you have to mount the drive as read rewrite at the beginning.  so unmount the drive, then mount it as root again but change the right permissions:
>>sudo mount -rw /dev/drive /media/mount_point

or in konsole when you have cd to your required folder, just use 'sudo' which will give you root, or superuser privileges!

*Warning, Root is the source of all evil*!!! 

Don't delete a partition or any valuable information by mistake or else it is gone!

---

### Post by prshah on 2008-11-18
> **marcusau2 said:**
> I am looking for 2 commands, one that will give me read write access to the file viewer (Nautilus) as root so I can drag and drop files and also a command for the terminal that will enable me to give write permissions to an individual folder.  Thanks

1) ```
gksudo nautilus
``` However, running nautilus as root (sudo) is _highly_ discouraged, and should be avoided at all costs. If you are mounting a device as root, that should also _not_ be done. Why do you want to use root to drag/drop?

2) Assuming you or your group is / are owners of the folder in question, you can use ```
chmod a+w foldername
``` to give write permissions to (a)ll, u+w for (u)ser, or g+w for (g)roup. If you don't own the directory, use "sudo" with the above command.

---

### Post by philinux on 2008-11-18
There is nothing wrong with using gksudo nautilus in fact I've seen more damage done by people using sudo in the terminal.
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)
It's my pc after all.

---

### Post by prshah on 2008-11-18
> **philinux said:**
> There is nothing wrong with using gksudo nautilus 


I've had arguments about this before; here's an [illuminating post]("http://ubuntuforums.org/showpost.php?p=5579065&postcount=8") about this.

---

