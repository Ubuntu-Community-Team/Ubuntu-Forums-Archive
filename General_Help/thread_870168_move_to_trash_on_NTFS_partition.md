---
title: "move to trash on NTFS partition"
date: 2008-07-25
forum: General Help
---

### Post by le_vainqueur on 2008-07-25
I have an NTFS partition that I use to store all of my documents, music, etc.  Presently, whenever I go to remove a file, I do not have the option to move it to trash. I assume this is an issue that Linux has with NTFS partitions.  Is there a way to solve this?  I have accidentally deleted a couple of files and was not able to recover them since they were not moved to the trash.  


Thanks,

LV

---

### Post by coffeecat on 2008-07-25
Well, this is very interesting. I'm actually posting from Linux Mint Elyssa atm on my laptop, but Mint Elyssa is only Hardy with a few bells and whistles. So...

I hadn't noticed what you described before, but on this laptop I have my Windows C: partition (NTFS) and a shared data partition formatted FAT32. You are quite right. Whether I try and drag and drop a file into the trash, or highlight a file and press delete I get the dialogue that I presume you're seeing. I can only delete the file completely. That's true for both filesystem types.

Which is very strange because I am sure I have moved things into the trash from a mounted FAT32 usb drive before. In fact, I seem to remember that I had to wait to unmount it when I elected to empty the trash and it took some time doing this.

I'll experiment with another machine and other distros and see whether or not this is an Ubuntu quirk. I'll post back, but probably not today.

**Edit**: the plot thickens. I've set this laptop up as a multiboot and made sure that my UID in each distro is the same, so what I am about to describe is nothing to do with permissions. I've just navigated into /home/myusername in another distro (on an ext3 partition) and I get exactly the same. I can only delete, not move a file into the trash.

**But** - I've also just plugged in a fat32-formatted usb drive and my memory was correct. I could move a file into the trash.

So this is an issue with mounted internal partitions generally, not just NTFS ones. Curious.

---

### Post by drs305 on 2008-07-25
For ntfs and vfat partitions, trash deleted in ubuntu is generally not recoverable (sent to trash). The exception is if you mount the partition via  fstab and included uid=1000 and/or gid=1000 (or whatever your number is) in the settings. 

If the uid/gid setting exists in fstab, a .Trash-1000 (or userid) is created after the next boot when you delete a file or folder. From that point forward, deleted trash will remain in that folder until the trash is emptied.

---

### Post by Benic on 2008-09-22
You can read this [_thread_]("http://ubuntuforums.org/showthread.php?t=921404&highlight=mount+fat32+partition") that will show how to mount your partition and edit fstab to make a ntfs/fat32 partition visible. I was still unable to use the trash can, so I went back to fstab and added the partition's UUID as shown here (last line):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=aed4ed6f-b1a2-4f85-a5e8-e43fc068e98b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=66cef2c2-0145-4e4b-a092-b7c2be23836e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda2	
UUID=48B1-8A4F	/home/bm vfat	iocharset=utf8,umask=000,uid=1000	0	0

After that, it worked out fine !

---

