---
title: "Can't reach GRUB"
date: 2008-11-03
forum: General Help
---

### Post by virtualgod on 2008-11-03
This one is beyond my knowledge (which I must say are quite limited when it comes to linux), but I have a serious problem with my girlfriend install of Ubuntu Studio.

For an unknown reason her system completely froze the other day. So much that we had to force shutdown her computer. However the real trouble started after that. We can't even get to GRUB to launch the system. We always get a permanent 'GRUB loading' (but it never actually load) and sometimes it comes with an 'error 18' or 'error 25'.

I would not mind doing a new install of the system, but she has some important document that she can't really afford to start anew.

By the way her install is a 8.10 Ubuntu Studio Beta if that can help.

If anyone out there has ANY idea, it would be much appreciated.

Thanks

---

### Post by eddietours on 2008-11-03
you could use the live cd to backup her info to a external HD

---

### Post by inportb on 2008-11-03
But GRUB doesn't disappear for no reason. If there a dedicated home partition, it's typically alright to reinstall without formatting home.

---

### Post by cariboo on 2008-11-03
It sounds like the partition that Ubuntu is installed on is corrupted. I would suggest using going here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and downloading Super Grub CDROM, I've used this a couple of times to get through grub problems.

Jim

---

### Post by inportb on 2008-11-03
It's quite possible to reconfigure GRUB using the Ubuntu disc. SGD is good, but it might be extra effort imo.

---

### Post by virtualgod on 2008-11-03
I tried using SUPER GRUB, but I wasn't able to have it start the system. I tried the numerous option that SUPER GRUB gave me but to no avail.

WEll thanks for your help, and if some ideas do come by please let me know.

Thanks

---

### Post by caljohnsmith on 2008-11-03
Have you done an "fsck" on the Ubuntu partition yet? From your Live CD, if you open a terminal (applications > accessories > terminal), you can do:
```
sudo fsck -y /dev/sdaX
```
And replace sdaX with the Ubuntu partition. If you're not sure which is the Ubuntu partition, you can use:
```
sudo fdisk -lu
```
And look for the partition of type "linux" under the "system" heading. Let me know if fsck finds any errors, and then you can try and mount the partition with:
```
sudo mount /dev/sdaX /mnt
```
And then it should be mounted on /mnt if all goes well. You can retrieve any files, and if you get this far, you can most likely get Grub working too. Let me know how it goes. :)

---

### Post by virtualgod on 2008-11-03
Ok, I tried what you suggested. The data seems to be good, however when I tried to mount it, it as ask me to specify the filesystem type. I have no idea how to find that, so again it would nice if you could get me a hand.

Thanks

---

### Post by caljohnsmith on 2008-11-04
If mount asks you to specify the file system type, usually the partition you are trying to mount is corrupt in some way, because under normal circumstances mount can figure out the file system type on its own. How about first posting:
```
sudo fdisk -lu
```
And what was the output of the "fsck" command on your Ubuntu partition?

---

### Post by virtualgod on 2008-11-04
Ok it seems that this command line:

*sudo fdisk -lu*

does not give information anymore also the other command line:

*sudo fsck -y /dev/sdaX* (no matter what number I give X)

always give me the same answer:

[I]fsck 1.40.8 (13-mar-2008 )
e2fsck 1.40.8 (13-mar-2008 )
fsck.ext2: Attempt to read block from fylesystem resulted in short read while trying to open /dev/sdaX
Could this be a zero-lenght partition?[/I]

I don't know why I can't see the info I could see last time, but if you have an idea please pass them along.

Also my girlfriend as now accepted the fact the she as lost her data and I will soon do a clean install. In the meantime I'll wait a little longer for an answer.

Thanks

---

### Post by tarps87 on 2008-11-04
The file system for Ubuntu is ext3
```
sudo mount -t ext3 /dev/sdaX /mnt
```
If it is a desktop you can try checking the hard drive cables as it is possible the problem is being cased by a lose connection

---

