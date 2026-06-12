---
title: "[SOLVED] UUID of sda1 differs for fstab &amp;amp; blkid outputs?"
date: 2008-08-23
forum: General Help
---

### Post by ddarsow on 2008-08-23
I am having some drive mounting troubles (unable to find mount point error) and noticed that the UUID of my /dev/sda1 differs in the fstab & blkid outputs.

See below:

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=d10a56f4-efdb-4eb7-8d5b-858c659439f7 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=c6faeef9-72b6-4d2f-b461-ceb6263f5691 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

~$ sudo blkid
/dev/sda1: UUID="8f1045be-5d05-43b3-b277-663b44ad0d91" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="c6faeef9-72b6-4d2f-b461-ceb6263f5691"

---

### Post by munkyeetr on 2008-08-24
A couple things I would try are:

---------------------------------------------------------------------------------
1) copy the fstab entry that is currently listed, paste it directly below the original, then comment it out with a '#' sign.
2) edit the original line with the UUID you get from blkid output. See if that make it right.
---------------------------------------------------------------------------------

or

---------------------------------------------------------------------------------
If you don't change drives out on your system, just replace the UUID with /dev/sda1
I would still copy and comment out the line as a backup.
---------------------------------------------------------------------------------

---

### Post by Patb on 2008-08-24
Ddarsow, it is strange that this has happened on your root partition. It is normal for a UUID to be changed when a partition is altered or formatted. Boot from a live CD. Then back up and edit your fstab to have the correct UUID. 
```
sudo gedit /etc/fstab
```
check you have the correct mount point. Since you quote the fstab contents, I'm assuming you know where to find it.  

Good luck, Pat.

---

### Post by tact on 2008-08-24
> **ddarsow said:**
> I am having some drive mounting troubles (unable to find mount point error) and noticed that the UUID of my /dev/sda1 differs in the fstab & blkid outputs.

See below:

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=d10a56f4-efdb-4eb7-8d5b-858c659439f7 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=c6faeef9-72b6-4d2f-b461-ceb6263f5691 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

~$ sudo blkid
/dev/sda1: UUID="8f1045be-5d05-43b3-b277-663b44ad0d91" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="c6faeef9-72b6-4d2f-b461-ceb6263f5691"

If /dev/sda1 is your boot drive i guess you cannot even boot the system.  Is that correct?

If thats the case you need to change /etc/fstab to the correct UUID as reported by blkid.  You will also need to change the entry in /boot/grub/menu.lst  or grub will not be able to find the correct partition and your system still will not boot.

PLEASE back up both files before editing!   Use something like:
```
sudo cp /etc/fstab /etc/fstab.20080824
```

Now you can edit /etc/fstab.  Don't use a wordprocessor.  Use a text editor like gedit.  example code:
```
sudo gedit /etc/fstab
```

Now to correct /boot/grub/menu.lst .....  if you manually edit it things will be fine until next time the update-grub utility is run.  When that is run grub will magically find the OLD uuid and replace it into menu.lst and your system will be broken again.  (update-grub is run automatically whenever update manager installs a new kernel update for example).    So what you should do instead of manually editing menu.lst is to delete it and recreate it.

Back it up and delete it in one move....  
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.20080824
```

Then have update-grub recreate it (and at the same time ensure that in future update-grub runs menu.lst will get the correct UUIDs):
```
sudo update-grub
```

---

### Post by ddarsow on 2008-08-24
> **tact said:**
> If /dev/sda1 is your boot drive i guess you cannot even boot the system.  Is that correct?

If thats the case you need to change /etc/fstab to the correct UUID as reported by blkid.  You will also need to change the entry in /boot/grub/menu.lst  or grub will not be able to find the correct partition and your system still will not boot.

PLEASE back up both files before editing!   Use something like:
```
sudo cp /etc/fstab /etc/fstab.20080824
```

Now you can edit /etc/fstab.  Don't use a wordprocessor.  Use a text editor like gedit.  example code:
```
sudo gedit /etc/fstab
```

Now to correct /boot/grub/menu.lst .....  if you manually edit it things will be fine until next time the update-grub utility is run.  When that is run grub will magically find the OLD uuid and replace it into menu.lst and your system will be broken again.  (update-grub is run automatically whenever update manager installs a new kernel update for example).    So what you should do instead of manually editing menu.lst is to delete it and recreate it.

Back it up and delete it in one move....  
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.20080824
```

Then have update-grub recreate it (and at the same time ensure that in future update-grub runs menu.lst will get the correct UUIDs):
```
sudo update-grub
```

That did it!
Thank you very much

---

