---
title: "Help mounting NTFS ext partition please"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by BiGx5MurF on 2005-04-17
I'm a complete linux noob, ubuntu 5.04 is my first experience with linux.  So far I think I'm still having winxp withdrawal.  But here's my problem.  The NTFS partitions I want to mount are on a sata hard drive, that communicates to my system through a pci sata controller.  I managed to mount the first partition ("/dev/sda1)" using a tutorial on the site.  But I can't seem to get the second partition (/dev/sda2") to mount, I get the error message saying I must me trying to mount an extended partitions (which I am), but I have no idea what I have to do different.

Also does anyone know of a good and detailed article on how to go about installing applications on linux?  I'm still not sure if I've updated to the latest nvidia drivers or not.

---

### Post by GrumpySmurf on 2005-04-18
Hello,

An extended partition doesn't contain a filesystem. Your hard drive can only contain four primary partitions, but it can contain more logical partitions within an extended partition.  The extended partition is created as the last primary partition (/dev/sda4) and spans the remainder of the disk.  One or more logical partitions can be created in the extended partition, /dev/sda5, /dev/sda6, and so on.  You can use the sfdisk command to display a list of the partitions on the disk.  Here's an example from my system.

```

$ sudo sfdisk -l /dev/sda
Disk /dev/sda: 9039 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   6427    6428-  51632878+   7  HPFS/NTFS
/dev/sda2       6428    6489      62     498015   82  Linux swap / Solaris
/dev/sda3       6490    6501      12      96390   83  Linux
/dev/sda4       6502    9038    2537   20378452+  8e  Linux LVM

```

Note that I do not have an extended partition.  If I did, it would be /dev/sda4 and any logical partitions would be listed after.  

Your second partition from Windows is probably /dev/sda5.  Try the following to mount the partition:

```

$ sudo mount -t ntfs -o umask=0222 /dev/sda5 /mnt/windows2

```

I will assume your partition is formatted with ntfs. Good luck.

As for your other question, there are many ways to install applications.  The primary method on Ubuntu is to use the Synaptic package manager, which is a GTK GUI front-end to the APT tool.  I prefer using APT directly via command-line.  There's a number of pointers here:

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

Particularly, you'll want to set up additional repositories in your apt configuration, then you can use apt-get upgrade to make sure all your packages are the latest available versions.  

I strongly recommend sticking to installing software via APT (Synaptic or command line).  Many people don't realize the inherent benefits to using distribution-provided packages, and recommend that new Linux users go about downloading source code tarballs and try compiling software.  Most end users have never heard of a compiler let alone know what compiling means.  Nor should they.  Ubuntu is desktop oriented and to tell people they need to download and compile software is ludicrous.

No sir.  Stick to Synaptic.  Figure out what kind of software applications you want to run on your computer and see if they're already there.  If not, check ubuntuguide.  It covers many of the usual suspects: internet multimedia formats, instant messaging, and more.  You can always search the apt repositories to see if the packages you want to install are available via APT.

---

### Post by BiGx5MurF on 2005-04-19
Thanks for the help, I got the ext partition mounted. But when its mounted, the other partitions doesn't mount, is there a way to have them both mounted? Or even both mounted automatically as soon as ubuntu starts?

---

### Post by Soleil-Raid on 2005-04-19
[QUOTE=BiGx5MurF]Thanks for the help, I got the ext partition mounted. But when its mounted, the other partitions doesn't mount, is there a way to have them both mounted? Or even both mounted automatically as soon as ubuntu starts?[/QUOTE]

As long as you're not trying to mount a given partition in two different places at once, or two partitions in the same directory, it should be perfectly able to read both directories.

---

### Post by GrumpySmurf on 2005-04-26
[QUOTE=BiGx5MurF]Thanks for the help, I got the ext partition mounted. But when its mounted, the other partitions doesn't mount, is there a way to have them both mounted? Or even both mounted automatically as soon as ubuntu starts?[/QUOTE]
Sorry for the delay in response, I've been busy over the last week.

To have a partition mount when Ubuntu boots, you need to add it to your /etc/fstab.  Using the mount command above, the syntax in /etc/fstab would look like this:

```
/dev/sda5       /mnt/windows2   ntfs    umask=0222      0 0
```
Good luck.

---

