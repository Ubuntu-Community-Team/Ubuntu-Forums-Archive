---
title: "How do you unmount sda1 partition"
date: 2008-07-27
forum: Hardware
---

### Post by vze57gc8 on 2008-07-27
i have ubuntu installed on my laptop and i want to do a dual boot with ubuntu and backtrack3. i installed partition editor to allocate space for bk3 but when unmounting the main partition (/dev/sda1) file system ext3 i get a messege saying...

"Could not unmount /dev/sda1. The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually."

Now im stuck and have no idea what to do. Can some1 plz coach me through?

---

### Post by tamoneya on 2008-07-27
you cant unmount "/".  In order to do this partitioning though you should use either the ubuntu live CD or the backtrack liveCD.  Run gparted or whatever you were planning on using from there since they dont need to mount any of your harddrives.

---

### Post by jbrown96 on 2008-07-27
could you tell us how your partitions are currently setup and how you would like them to be setup? Note that you cannot be running ubuntu from /dev/sda1 and try to resize /dev/sda1 because there is no way to unmount it. Use a live CD. Ubuntu comes with gparted on the livecd. The command would be ```
sudo umount /dev/sdaX
``` where X is the partition number. You can check your how your device is partitioned with ```
fdisk -l /dev/sdX
``` where X is a letter (the first hard drive is "a", second is "b", etc)

---

### Post by vze57gc8 on 2008-07-27
actually the live cd that i have is 6.04 which dont have gpart. is it possible to run the cd and install gpart

---

### Post by tamoneya on 2008-07-27
yes it is```
sudo apt-get update
sudo apt-get install gparted
sudo gparted
```

---

### Post by coffeecat on 2008-07-27
> **vze57gc8 said:**
> actually the live cd that i have is 6.04 which dont have gpart.

Actually it does, but it doesn't call it that - at least I'm 99% sure it does. I'm going from memory here - Dapper is 2 years ago - look in System > Administration > Gnome Partition Editor (or something like that) on your live environment desktop. That is Gparted.

BUT... Dapper is 2 years old with an older version of Gparted. If I was in your situation, I would much rather use a later version which should have had bugs fixed. Can you download Ubuntu 8.04, or perhaps even the Gaprted live CD? Both are well-worth having if you can download them.

---

### Post by acompay on 2010-10-16
[COLOR=black][FONT=Verdana][SIZE=3]Hello There,[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I print out the Softpedia instructions to install Ubuntu 9.10 on the same partition it is installed now, but it is not working. I don't find answer to this question: "Do you want to unmount partitions?" I said not but later it could not proceed. I have XP Professional running in one partition and want to have dual booting as before. What are the consequences of unmounting partitions?[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I would appreciate very much your help![/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]Regards,[/SIZE][/FONT][/COLOR]
[FONT=Calibri] [/FONT]

---

### Post by cbemerine on 2010-10-16
@acompay you will find the information about FSTAB, mounting different file systems, whether permanent or temporary very, very helpful.  Here is the link:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

I have not dual booted for years, so I will leave that for someone who is more recent.  If you unmount the wrong partition, your file system will not be usable.  Windows likes to overwrite the MBR which can cause Linux not to boot up as well.  Check that link you will find it very helpful.

---

### Post by firefox834 on 2011-05-17
?

---

