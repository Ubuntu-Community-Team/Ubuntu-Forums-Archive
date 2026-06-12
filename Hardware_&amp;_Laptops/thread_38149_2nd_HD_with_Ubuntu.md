---
title: "2nd HD with Ubuntu"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by Mr_Tickles on 2005-05-30
Hey guys, i'm new to ubuntu, and could do with some help...

I've recently installed Ubuntu on my second hard disk, XP being on the first which I have used for ages.

The problem is, I can't seem to access the windows drive from ubuntu.
I've read the other threads where people had similar problems to this, however they were all involving partitions etc, which I do not have.  It's just a solely XP disk, and an Ubuntu disk.

with the command *fdisk -l* in the root terminal, I get these details
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       76552    38582176+  83  Linux
/dev/hdb2           76553       77545      500472    f  W95 Ext'd (LBA)
/dev/hdb5           76553       77545      500440+  82  Linux swap

```

and with *df -h* I get
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              37G  1.8G   33G   6% /
tmpfs                 252M     0  252M   0% /dev/shm
/dev/hda1              75G   51G   25G  68% /mnt/windows

```

Also, I have in */etc/fstab*
```
/dev/hda1	/home/dave/spikeii	ntfs	rw,auto,uid=1000,gid=1000,umask=0000	0	0
```

Now, i'm guessing that means that the disk is already mounted, however, I can't access it.  I've been through the other threads trying to work out where to go from here, but this is where they tend to diverge.
Can someone tell me what to do now please?

---

### Post by grim42 on 2005-05-30
Hi there,

Can you give the whole contents of your fstab file?

What happens when you try to access the mounted location at */home/dave/spikeii* or */mnt/windows*?

The following entry in fstab should allow all users to have read-only access to the Windows drive if it is mounted at /media/windows and this works for me.

/dev/hda1       /media/windows  ntfs    umask=0222      0       0

Greg

---

### Post by Mr_Tickles on 2005-05-30
Hey, thanks for the reply... I fell asleep and so didn't reply straight away :D

Here's my fstab.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


#Manual Mounted Drives
/dev/hda1	/home/dave/spikeii	ntfs	rw,auto,uid=1000,gid=1000,umask=0000	0	0

```

The *mount -a* command
```
root@SpikeIII:/home/dave # mount -a
mount: /dev/hda1 already mounted or /home/dave/spikeii busy
mount: according to mtab, /dev/hda1 is mounted on /mnt/windows
```

As far as I understand it, I have to create a folder at *home/dave/spikeii*, and if all goes right, the contents of my first HD should be in there?  Hmmm, it's not. :(

Ahh, ok, I didn't know about the *mnt/windows*.  I just tried it and it had the red cross emblem and told me I didn't have permission to access that folder...
Does this mean I have to reboot into Windows and share the entire HD?  I'm not sure if I want to do this as I am on a network.

---

### Post by grim42 on 2005-05-30
Firstly, DON'T share the drive in Windows. The reason you cant access it is because of the permissions being set when it's mounted.

It looks like your hard drive is being mounted at /mnt/windows but that's not in your fstab? Mmm, puzzling.

Try replacing the line in your fstab file with:

```
/dev/hda1 /mnt/windows ntfs umask=0222 0 0
```

then reboot and see if you can access /mnt/windows.

Also, what happens when you remove this line altogether? Ie. No reference to /dev/hda1 in fstab. Does it still say it's mounted at /mnt/windows?

Is the drive showing up under Places/Computer from the GNOME panel?

---

### Post by Mr_Tickles on 2005-05-30
Ahh! Brilliant! Thank you very much :D
The first hard disk is now accessible through */mnt/windows*.
However, the drive does not show up in *computer/disks*, i'm not sure why.
Also, would there be any chance of getting the drive to show in */home/dave/spikeii* aswell?
Would I just have to add another line to the fstab with that path, aswell as the line you told me to edit in?

---

### Post by grim42 on 2005-05-30
No don't add another line. I don't think a drive can be mounted in two places, but you could make a symlink to /mnt/windows.

Remove the *spikeii* directory from */home/dave* first, then:

```
cd /home/dave
ln -s /mnt/windows ./spikeii
```

I haven't tested this, but it should work.

Let me know.

---

### Post by Mr_Tickles on 2005-05-30
Yes, works brilliantly, thank you again :)

---

