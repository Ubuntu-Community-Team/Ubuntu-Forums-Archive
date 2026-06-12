---
title: "wubi-add-virtual-disk"
date: 2008-11-27
forum: General Help
---

### Post by Dorotheos on 2008-11-27
> How do I resize the virtual disks?

You can use LVPM, at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

As an alternative, you can use the following script to move /home or /usr to a dedicated virtual disk.

Download wubi-add-virtual-disk, open a terminal and run:

sudo sh wubi-add-virtual-disk /home 15000

Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.

The 2 directories you are most likely to migrate are /home (if you have a lot of user data) and /usr (if you installed a lot of software).

You should now reboot. If you are happy with the result, you can now remove /home.backup. To undo the changes remove /home, copy rename /home.backup to /home and remove the /home line in /etc/fstab.

From [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

So basically i tried to get more space in wubi. I used wubi-add-virtual-disk and it worked: yep it gave me a fresh new start! So i want all my stuff back but how? It says "o undo the changes remove /home, copy rename /home.backup to /home and remove the /home line in /etc/fstab" but i run into permission problems. Does anyone know how to do this?

---

