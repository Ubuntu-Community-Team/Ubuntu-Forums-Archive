---
title: "Expand the size of partition after installation?"
date: 2008-11-19
forum: General Help
---

### Post by gychang on 2008-11-19
I installed the 8.1 using wubi and like it a lot in dual boot mode with XP.

I find myself I need more hard drive space than what I setup originally using wubi,  (When I tried to copy all my .flac files to 8.1, got a warning not enough HD space) only gave ?8G for original 8.1 install and I have much more HD space.

can I expand the HD space without reinstalling the 8.1? How?

gychang

---

### Post by Orlsend on 2008-11-20
Thankfully we have the WUBI guide for all this sort of problems.

[I]How do I resize the virtual disks?

You can use LVPM, at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

As an alternative, you can use the following script to move /home or /usr to a dedicated virtual disk.

Download wubi-add-virtual-disk, open a terminal and run:

sudo sh wubi-add-virtual-disk /home 15000

Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.

The 2 directories you are most likely to migrate are /home (if you have a lot of user data) and /usr (if you installed a lot of software).

You should now reboot. If you are happy with the result, you can now remove /home.backup. To undo the changes remove /home, copy rename /home.backup to /home and remove the /home line in /etc/fstab.

[/I]

Just a tip to remember, WUBI does not make partitions, only virtual disks (Wich are just files)

For all the other WUBI needs use this as a reference.

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

Enjoy your new space.

---

### Post by gychang on 2008-11-20
> **Orlsend said:**
> Thankfully we have the WUBI guide for all this sort of problems.

[I]How do I resize the virtual disks?

You can use LVPM, at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

As an alternative, you can use the following script to move /home or /usr to a dedicated virtual disk.

Download wubi-add-virtual-disk, open a terminal and run:

sudo sh wubi-add-virtual-disk /home 15000

Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.

The 2 directories you are most likely to migrate are /home (if you have a lot of user data) and /usr (if you installed a lot of software).

You should now reboot. If you are happy with the result, you can now remove /home.backup. To undo the changes remove /home, copy rename /home.backup to /home and remove the /home line in /etc/fstab.

[/I]

Just a tip to remember, WUBI does not make partitions, only virtual disks (Wich are just files)

For all the other WUBI needs use this as a reference.

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

Enjoy your new space.

thanks so much, lots to learn, wubi is great.

gychang

---

