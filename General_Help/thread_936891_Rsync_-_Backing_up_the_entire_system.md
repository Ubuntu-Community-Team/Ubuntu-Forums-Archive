---
title: "Rsync - Backing up the entire system?"
date: 2008-10-03
forum: General Help
---

### Post by Roasted on 2008-10-03
I was doing some research on Mac cloning because I'm using carbon copy cloner to clone a series of iBooks for work, so while I sit here as they clone I was doing some informative research. Mac suggested on one page that a good idea is to rsync. Well, I already rsync. I have two 500gb drives in my system and I rsync my home directory to the 2nd drive. But Mac suggested if you rsync everything, it'll make a bootable copy of your other drive.

Question is this. If I rsync my entire drive, meaning /, I'll copy over my home directory + root. Will that seriously make my other drive bootable, therefore if I have a drive failure, I can pull that drive out, boot up and boot to my secondary drive? What if I have root on a different partition? I've got root on a 16gb partition and my home directory on another partition. Would I just have to run 2 lines of commands and have my 2nd backup drive have separate partitions as well? (Meaning, rsync / to root, then separately rsync home to home?)

---

### Post by meanburrito920 on 2008-10-03
I was under the impression that something like that would fail, probably because it would screw with the guids and such. but you could probably find a way about it if you manage to find the right config files to update.

---

### Post by Roasted on 2008-10-03
Thing is, rsync copies everything... and changes only files that change. So... in theory... I'm starting to have a hard time believing that it would indeed fail... 

I mean, think about it. Root is a series of files. The files cause the system to boot.

If you copy those files to another resource, wouldn't it still have the same bootable traits? 

Regardless, worst case scenario is I have my data backed up on a 2nd drive! It's sooo nice knowing I can type sudo backup and my simple script takes off, copying all my music, pictures, etc to a 2nd hard drive. But hey, it's the same size as my main drive. If I can copy the OS, why not? :guitar:

---

### Post by koenn on 2008-10-03
rsync works on files. to clone a disk and have it bootable, you need to clone the boot sector as well, which you can't do with rsync. So this is not going to work, i think, unless you copy the boot sector (use dd) or manage to fix the boot record afterwards.

as for having stuff on different disks : as rsync works on files, and the unix filesystem is unified (everything is under /, regardless of how many disks/partitions/... are are being used), rsync will happily copy /home or whatever additional disks you have mounted - but it will not automatically use a separate target disk, because it can only see files and has no way of knowing which (source) files are on what disk. 
see man rsync for options that deal with links and mountpoints
see also [http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm](http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm)

---

### Post by wkulecz on 2008-10-03
I clone systems with rsync all the time.

Mount the target drive partition and fromat as you want, thoses $25 USB to IDE/SATA adaptor gizmos really come in handy here.

assume your target mounts as /dev/sdd1 on /media/sdd1 If your source system and target system is not partitioned the same, you will have to edit /boot/grub/menu.lst and /etc/fstab on the target after the rsync for it to boot.


clone the system with:

rsync -ax --exclude *.gvfs / /media/sdd1

The exclude option is for the fuse filesystem which otherwise generates rsync error messages that have been harmless, but the exclude eliminates these.

The only remaing problem is to install grub on the cloned system disk.  There are a lot of ways to do this.  I find the easiest is put the clone drive into the target system and boot your Ubuntu install CD.  Open a root shell and do the following commands

grub
find /boot/grub/stage1

this returns something line hd(0,0) depending on how you partitioned,
then do:

root (hdx,y) where x&y are what was returned in the hd(x,y) from the find above.
setup (hd0)
reboot.

Sounds harder than it is, especially if you don't change the partitioning other than the sizes.

--wally.

---

### Post by hyper_ch on 2008-10-03
you can force rsync to keep uids and gids :)

---

### Post by Roasted on 2008-10-03
> **hyper_ch said:**
> you can force rsync to keep uids and gids :)

Which would accomplish what... retain the bootable option on the cloned copy??

---

### Post by hyper_ch on 2008-10-03
-a will preserver uids/gids... but no clue about boot sector.. I tend to think it wont't keep that.

---

