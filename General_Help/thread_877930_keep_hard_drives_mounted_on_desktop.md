---
title: "keep hard drives mounted on desktop ?"
date: 2008-08-02
forum: General Help
---

### Post by smooth3006 on 2008-08-02
id like to have my windows partitions / hard drives stay mounted on my desktop all the time even after a reboot or shutdown. how can i do that ? :confused:

---

### Post by mikewhatever on 2008-08-02
Can you post the output of **cat /etc/fstab** here.

What you probably mean is you want the icons on the desktop. They should show there all the time for partitions mounted under /media.

---

### Post by coffeecat on 2008-08-02
Just to add to what **mikewhatever** posted, we need the contents of /etc/fstab so that we can see whether you need extra lines in that file in order to mount your Windows partitions on bootup.

Please also post the output of:

```
sudo fdisk -l
```

... so that someone can advise you on what to put into fstab if you need to.

---

### Post by smooth3006 on 2008-08-02
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=0b81fa8b-e069-4275-b596-e9e29ebfe00d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=52fefccf-13fa-47db-a479-74160eff17d3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by smooth3006 on 2008-08-02
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x997959e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78147584    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee98ee98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15869   127459320    7  HPFS/NTFS
/dev/sdb2           29673       30401     5855692+  82  Linux swap / Solaris
/dev/sdb3           15870       29672   110872597+  83  Linux

Partition table entries are not in disk order

---

### Post by smooth3006 on 2008-08-02
> **mikewhatever said:**
> Can you post the output of **cat /etc/fstab** here.

What you probably mean is you want the icons on the desktop. They should show there all the time for partitions mounted under /media.

i posted the requested info. yes i meant i would like the icons to show up all the time. after every reboot the icons dissapear.

---

### Post by mikewhatever on 2008-08-02
You should edit fstab so that the two ntfs partitions get mounted at boot.

First create directories:

sudo mkdir /media/windows
sudo mkdir /media/ntfs

Now, backup with **sudo cp /etc/fstab /etc/fstab-backup**, 
then open for editing with **gksudo gedit /etc/fstab** and add the following lines:

/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sdb1 /media/ntfs ntfs nls=utf8,umask=0222 0 0

save and exit.

---

### Post by coffeecat on 2008-08-02
> **mikewhatever said:**
> /dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sdb1 /media/ntfs ntfs nls=utf8,umask=0222 0 0

Two comments. The OP would probably be better off using the ntfs-3g driver to get read-write access. Also, with the ntfs-3g driver, you simply need 'defaults' in the options field. So those two lines would become:

```
/dev/sda1    /media/windows     ntfs-3g    defaults   0 0
/dev/sdb1    /media/ntfs        ntfs-3g    defaults   0 0
```In fact, that's how the Ubuntu installer set it up for me (with ntfs-3g and defaults), so who am I to argue with the Ubuntu installer? :wink: And it works fine for me.

---

### Post by mikewhatever on 2008-08-02
Well, I think ntfs-3g is applied by default to ntfs partitions and umask part is there to set permissions. Hope both ways work.

---

### Post by coffeecat on 2008-08-02
> **mikewhatever said:**
> and umask part is there to set permissions.

Yes, I've never quite understood how it all works. Files and folders are marked as being owned by root in an NTFS partition with ntsf-3g, but I've never had any problems reading, writing, deleting, modifying, etc. But I've seen threads where people have had issues and try all sorts of things in the options field to get it to work. Very odd.

But as it works for me, I'm happy. :wink:

---

### Post by smooth3006 on 2008-08-02
so if i try any of those 2 above options it won't harm anything in ubuntu ? i mean if it doesn't work for some reason.

---

### Post by mikewhatever on 2008-08-02
> **smooth3006 said:**
> so if i try any of those 2 above options it won't harm anything in ubuntu ? i mean if it doesn't work for some reason.

No. If it doesn't work, use a live cd or recovery mode to restore fstab to its original state.

---

### Post by smooth3006 on 2008-08-02
> **mikewhatever said:**
> No. If it doesn't work, use a live cd or recovery mode to restore fstab to its original state.

how to you restore from the live cd / recovery mode ? is there a certain command i would have to use ?

---

### Post by mikewhatever on 2008-08-02
> **smooth3006 said:**
> how to you restore from the live cd / recovery mode ? is there a certain command i would have to use ?

First, you can simply navigate to xorg's location in /etc/X11, open it with gedit and delete the two lines. That would be the easiest way from the live cd. If you prefer CLI and recovery mode, the following would restore the file from backup you'd very prudently created (have you?):
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf

---

