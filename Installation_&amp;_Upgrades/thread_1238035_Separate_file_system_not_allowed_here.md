---
title: "Separate file system not allowed here"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by mlilien on 2009-08-12
I just got a new Lenovo T400 laptop.  I'm trying to install 64bit ubuntu on it, but am running into some issues when preparing the partitions.

After shrinking my Vista install, the drive looks like this:
/dev/sda1 ntfs
/dev/sda2 ntfs (vista)
free
/dev/sda3 ntfs (recovery partition)

I'd like to create a root, a /home, a swap, and a /media partition, to keep my music, videos, and whatnot on.

I have two issues.  The first being that if I try to create the root partition as a primary, it lists the rest of the disk as unusable.

The second issue is that if I give my media partition any name other than one of the standard (/var, /boot, etc) it pops up an error message saying "you assigned a separate file system to /media, but in order for the system to start correctly this directory must be on the root file system."

I've looked around and can't find a solution.

Thanks in advance for any help

---

### Post by Zack McCool on 2009-08-12
You can only have 4 primary partitions on a disk.  Once you create your first partition, the rest of the disk becomes unusable.

The solution would be to move sda3 to the beginning of the free space, then create an extended partition.  Now, you can create the partitions you need.

Your disk would then look like this: 

```

/dev/sda1 ntfs
/dev/sda2 ntfs (vista)
/dev/sda3 ntfs (recovery partition)
/dev/sda4 EXTENDED
 free space (for sda5, sda6, and so on...)

```

---

### Post by mlilien on 2009-08-12
Thanks.

I tried that and still got the same error about my /media partition being assigned to a different filesystem.  Any ideas on how to fix that?

---

### Post by mlilien on 2009-08-12
Actually, scratch that.  I was wrong, moving the third partition doesn't allow me to create a 4th primary and several logical partitions, but I think I have a better grasp on the whole logical/primary thing now and I understand why that is.  So, I'll just install ubuntu on a logical partition.

But I'm still having issues with it not letting me mount a custom partition.

---

### Post by Zack McCool on 2009-08-12
If you're having a problem mounting the partitions, post your /etc/fstab here.  Also, give me the mount command you are using, along with the exact results that come up.

---

### Post by mlilien on 2009-08-12
These are issues I'm getting during install, through the install program off the live cd.

---

### Post by nerdzero on 2009-08-12
Hi mlilien,

Based on the error message, it looks like you cannot mount a device to the media folder directly.  This folder is where your cdrom and other removable media get mounted to as subfolders (i.e. /media/cdrom, /media/floppy, etc.)

Maybe you can try entering /mnt/data or /media/shared as the mount location for your custom partition?

---

### Post by Zack McCool on 2009-08-13
Then you should really not have any issues, unless something you are doing is a little off.

Once you set /dev/sda4 as extended, you'll start setting the logical partitions.

For instance:
/dev/sda5 - /boot - ext3 - 150M
/dev/sda6 - /     - ext3 - 10G
/dev/sda7 - /var  - ext3 - 4G
/dev/sda8 -       - swap - 2G
/dev/sda9 - /home - ext3 - remaining space

Should work.  Choose the mountpoints from the drop down boxes for consistency (no typos).

---

### Post by mlilien on 2009-08-13
Nerdzero had it right.  There was a naming conflict with the /media folder.  I should've realized this earlier, but it just didn't occur to me and the error message wasn't very helpful.

Thanks a lot.

---

