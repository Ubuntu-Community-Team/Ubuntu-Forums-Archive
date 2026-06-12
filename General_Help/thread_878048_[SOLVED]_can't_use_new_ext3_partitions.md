---
title: "[SOLVED] can't use new ext3 partitions"
date: 2008-08-02
forum: General Help
---

### Post by wolfen69 on 2008-08-02
i re-partitioned a second hard drive for storage and backup. it is ext3 format. i have 2 partitions on the drive. sda1 and sda2. i have tried everything humanly possible to be able to write to the drive. there is nothing wrong with the drive, because it works fine formatted as ntfs or fat32. all i see when i open the partitions is a lost and found symbol. i've tried chown, and various fstab configurations.

it seems like this is the impossible dream. i wanted to rid myself of windows type file systems, but it appears i may have to format them ntfs to make them usable. does anyone know the magic spell to make this work? apparently, the devs dont want anyone with less than a degree in computer science to be able to mount and use an ext3 hard drive. please prove me wrong. thanks for any help.

here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=80d16226-b423-4188-9d99-99973280ebd8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=7866b39a-9241-49b3-b4c4-22a1e646556f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
**/dev/sda1       /media/music   ext3    auto,user,exec,rw 0 0**
#
**dev/sda2        /media/permanent    ext3     auto,user,exec,rw 0 0**
```

---

### Post by spiderbatdad on 2008-08-02
of course the mount point has to be a directory in your file system.
Have you created it...or tried /mnt/media  and  /mnt/permanent?

Also consider these examples:
/dev/hda2 / ext2 defaults 1 1
/dev/hdb1 /home ext2 defaults 1 2
where /dev/hda2 is mounted to /
and /dev/hda1 is mounted to /home

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by mc4man on 2008-08-02
I can't really understand why it seems  difficult to gain mount, unmount rw on additional drives, partitions ect. 
I have 11 partitions on 2 drives and no fstab entries (except for the current Os) (ext.2,3, ntfs, fat32)
simply going into system -> admin -> authorizations -> storage and granting myself explicit authorization to mount file systems on internal drives gave me immediate full everything on all of them. (d. click icon to mount, r.click to unmount)

---

### Post by wolfen69 on 2008-08-02
yes, i have mount points in media. i changed my fstab to this and still no go.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=80d16226-b423-4188-9d99-99973280ebd8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=7866b39a-9241-49b3-b4c4-22a1e646556f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
**/dev/sda1       /media/music  ext3  defaults 0     0**
#
**/dev/sda2       /media/music  ext3  defaults 0     0**
```
i still have the lost and found symbols when i open the partitions.

how does one go about adding an internal hard drive, format it ext3, make 2 partitions, and use it?

---

### Post by drs305 on 2008-08-02
I'm sorry to see you are still having difficulty. Gparted would be the way to partition and format a hard drive. Just make sure you select the correct hard drive from the upper right side of the app.

```
sudo gparted
```

It will look at the partitions. Click on the hard drive/partition you want to work on, select Partition, Unmount. Then you can format it to ext3 and size the two partitions.

**Added:** However, if you are seeing the lost+found folder on the partition it should mean you have an ext2/3 partition and it's mounted. Otherwise you wouldn't see it. If you formatted it to ext3 it would have erased any existing data on the partition and it would be empty. All you would have would be the lost+found folder until you added something to it.

---

### Post by spiderbatdad on 2008-08-02
```
#
/dev/sda1       /media/music  ext3  defaults 0     0
#
/dev/sda2       /media/music  ext3  defaults 0     0
```

I see examples of the above type with ext2, but with ext3 generally something like:
```
/dev/sda1       /media/music   ext3    relatime,errors=remount-rw 0       0

```

---

### Post by wolfen69 on 2008-08-02
> **drs305 said:**
>  All you would have would be the lost+found folder until you added something to it.
that's where i'm stuck. i can't add anything to it. i looked at properties and it said root is the owner. is there a chown command that actually works?

---

### Post by spiderbatdad on 2008-08-02
I'm wondering since you've chosen /media instead of /mnt  as your directory if you might want auto as the file type instead of ext3

```
/dev/sda1       /media/music   **auto**    auto,user,exec,rw 0 0
#
dev/sda2        /media/permanent   **auto**    auto,user,exec,rw 0 0
```

auto is generally chosen where the filesystem is on media like cdrom...or floppy. I know this isn't the case, but it may prefer where the mount point is /media. Otherwise try /mnt/music...

---

### Post by wolfen69 on 2008-08-02
> **spiderbatdad said:**
> ```
#
/dev/sda1       /media/music  ext3  defaults 0     0
#
/dev/sda2       /media/music  ext3  defaults 0     0
```

I see examples of the above type with ext2, but with ext3 generally something like:
```
/dev/sda1       /media/music   ext3    relatime,errors=remount-rw 0       0

```

i put in : ```
/dev/sda1       /media/music   ext3    relatime,errors=remount-rw 0       0
```
but it said that line is incorrect and cant mount it. i also went into authorizations and added myself to mount internal hard drives, but still nothing. this is becoming an exercise in futility. any other ideas?

---

### Post by spiderbatdad on 2008-08-02
last time I tried mounting in hardy I was having trouble with /media...it may have been the commands. I ended up using /mnt And the problem was solved. This was where I was trying to mount my installed filesystem from the booted live cd.

---

### Post by wolfen69 on 2008-08-02
> **spiderbatdad said:**
> I'm wondering since you've chosen /media instead of /mnt  as your directory if you might want auto as the file type instead of ext3

```
/dev/sda1       /media/music   **auto**    auto,user,exec,rw 0 0
#
dev/sda2        /media/permanent   **auto**    auto,user,exec,rw 0 0
```

auto is generally chosen where the filesystem is on media like cdrom...or floppy. I know this isn't the case, but it may prefer where the mount point is /media. Otherwise try /mnt/music...

tried that. still get a lost and found icon in the partitions.

---

### Post by silkstone on 2008-08-02
There is a guide here which I think will help...

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

You don't need to change anything in Lost&Found - that's just for file recovery if there's a disk corruption.

You do need to change the ownership of the Ext3 partitions (which are owned by root by default, since you run gparted as root). How to do that is also in the guide.

Please let's know if that works for you.

---

### Post by wolfen69 on 2008-08-02
could someone that has a storage drive formatted as ext3 please post their fstab? or give me a chown command that works?

---

### Post by Elfy on 2008-08-02
I don't quite see why you are having the problems you are with the lines you have in fstab

> UUID=000cf730-bffc-4ab6-bd8d-3305b4218fcf /media/data ext3 defaults 0 2worked fine for me, obviously I used UUID instead of the /dev/ method - I might have had to chmod chown it though can't remember.

Not getting granny to suck eggs but have you checked the folders you're trying to mount to...

I'm pretty sure that this did it for me

sudo chown user.users /mount/point
sudo chmod 770 /mount/point/


Edit - my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=c88bfb07-6758-4ada-a213-a0cf10a0b7a2 /home           ext3    relatime        0       2
# /dev/sda3
UUID=f2a6d843-410d-4511-914b-0196eec78f1e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#dev/sdb2
UUID=6cebc2cf-6ba9-4c38-bdd8-5abf91ebf7d3 /media/media ext3 user 0 2

#dev/sda5
UUID=000cf730-bffc-4ab6-bd8d-3305b4218fcf /media/data ext3 defaults 0 2

#intrepid
UUID=cf22b05f-fe78-4e34-bd54-d62862350755 /media/intrepid ext3 defaults 0 2
#movieskid
UUID=30dc3efa-1b6d-4a70-b0ab-88ece596a554 /media/movieskid ext3 defaults 0 2
#vbox
#UUID=330c7dbe-2751-4be2-8ad2-a3dfbb541b05 /media/vbox ext3 defaults 0 2

none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
```

---

### Post by wolfen69 on 2008-08-02
thanks silkstone for the info. i finally got it to work. the info in that guide wasnt quite correct. the fstab entry that was mentioned was to add: ```
/dev/hda5 /storage ext3 defaults 0 0
``` it should be ```
/dev/hda5 ***/media***/storage ext3 defaults 0 0
``` and after i chowned and rebooted, all is right in the world. you guys are the best. thanks for all the help.

---

### Post by Elfy on 2008-08-02
shouldn't 

media/storage

be /media/storage :confused:

but if it works it works.

---

### Post by drs305 on 2008-08-02
> **wolfen69 said:**
> tried that. still get a lost and found icon in the partitions.

The lost+found folder is not an error. It is a system folder where fsck sticks bits and pieces if it finds a problem. There are ways to hide it if you wish to.

When you see the lost+found folder, can you right click in an empty space underneath it and create a new folder or file?

---

### Post by silkstone on 2008-08-02
Glad to hear it worked with a bit of juggling!

In case you didn't know, if you mount on /media there will be an icon for the drive/partition on the desktop. If you mount on /mnt there is no icon.

---

