---
title: "Hardware-independent system image"
date: 2008-11-18
forum: General Help
---

### Post by desktop user on 2008-11-18
Hello,

If we use Tar\[Dar]("http://dar.linux.free.fr/") to backup system, then following steps should provide bare metal recovery\deploy on different hardware: 
1) packing up entire root filesystem, excluding certain files\folders which represent hardware and its settings;
2) installing from scratch (Ubuntu Live CD\DVD) on whatever hardware when needed (hdd failure etc.);
3) restoring filesystem from backup: users' settings, installed software etc.

Is that possible to achieve?


..Initial idea taken from [here](http://ubuntuforums.org/showthread.php?t=564836) (thanks **tech9** and **epimeteo**), exclusion of /etc/acpi for hardware-independent backup taken from [here](http://ubuntuforums.org/showthread.php?p=5293593). 
So current list of objects to exclude:
/boot
/etc/fstab
/etc/acpi


Please correct\supplement current list and\or drop link(s) where one can find related documentation. Thanks :)

---

### Post by desktop user on 2008-11-19
up

---

### Post by desktop user on 2008-11-19
up

---

### Post by desktop user on 2008-11-20
up

---

### Post by sedawk on 2008-11-20
Why to backup the whole system if you never do a full recovery (e.g
via a Live-CD and some tool like "partimage").

Why not to backup only /home and /export (assuming all extra software is on
/export) and then to recover these two?

(In professional environments /home and /export are anyway not local, 
 but mounted from a file server or a SAN or exist on different partitions,
 so reinstalling ubuntu doesn't touch these partitions if you don't want to)

What might be handy is to include the output of "dpkg -l" into
the backup, so you exactly know which additional ubuntu packages
have been installed previously.
(I like to forget adding "mplayer" or "cryptsetup" or "build-essential"
 after doing a fresh installation).

---

### Post by desktop user on 2008-11-20
> **sedawk said:**
> Why to backup the whole system if you never do a full recovery (e.g
via a Live-CD and some tool like "partimage").
What do you mean? Dar is able to recover filesystem exactly as it was at time of backup..

> **sedawk said:**
> 
Why not to backup only /home and /export (assuming all extra software is on
/export) and then to recover these two?
Good idea, thnx... But I'm not sure where on local filesystem all installed software resides (/etc, /usr/bin, /usr/lib, /usr/sbin, /usr/share, /var/lib ??). 
..In your example /export is a repository with all needed packages?  

> **sedawk said:**
> 
What might be handy is to include the output of "dpkg -l" into
the backup, so you exactly know which additional ubuntu packages
have been installed previously.
What gives? Still I would need to install that packages from scratch? 

thanks

---

