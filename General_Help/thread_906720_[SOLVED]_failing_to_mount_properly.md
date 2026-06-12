---
title: "[SOLVED] failing to mount properly?"
date: 2008-08-31
forum: General Help
---

### Post by fallen seraph on 2008-08-31
when my laptop running hardy boots up I'm not sure that my second partition (the non-boot one) mounts properly.

Any links I have to anything on it appear broken and it won't show up if I try to navigate to it in a terminal, until I access the partition using the places bar. At which point it'll return completely to normal :\

I find this most frustrating; can anyone help?

---

### Post by Elfy on 2008-08-31
Is it mounting through fstab - can you run these and post the outputs please

```
sudo fdisk -l
cat /etc/fstab
sudo blkid
```

---

### Post by porchrat on 2008-08-31
Sounds like it isn't mounting on boot.  You can see it in "places" as ubuntu knows the drive exists, then when you click on it in "places" it mounts and lets you read from it.  Probably an fstab issue, just edit fstab and add the drives to the end of it.

forestpixie is right, post the ouputs of those commands so we can be sure.

---

### Post by fallen seraph on 2008-09-03
okay


> sudo fdisk -l returns

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1953    15687441   83  Linux
/dev/sda2            1954        9729    62460720   83  Linux


> cat /etc/fstab returns
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1953    15687441   83  Linux
/dev/sda2            1954        9729    62460720   83  Linux
padraic@laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=457597c5-dcb6-405e-ba09-af699f3fd843 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



and 

> sudo blkid
returns
> /dev/sda1: UUID="457597c5-dcb6-405e-ba09-af699f3fd843" TYPE="ext3" 
/dev/sda2: UUID="0d8912fc-db21-4928-9a5b-8eaffa8e911f" TYPE="ext2"

thanks for the help; and, indeed, what do I need to change to fix this?

---

### Post by Elfy on 2008-09-03
Hi - it's not in fstab so we can do that quite easily. In the following I will call the partition "disc" - you can change it to whatever you like as long as you do so everywhere it's in [COLOR="Red"]red[/COLOR].

If you want the partition to show on the desktop leave commands as they are, if you don't want to see it on the desktop change /media for /mnt (in [COLOR="Blue"]blue[/COLOR]) - this also, it appears, stops it showing in computer

We'll make a backup of fstab before we start - 

```
sudo cp /etc/fstab /etc/fstab.0309
sudo mkdir /[COLOR="Blue"]media[/COLOR]/[COLOR="Red"]disc[/COLOR]
gksudo gedit /etc/fstab
```

The file is now open to edit - don't change anything that already exists, add these 2 lines to the bottom of the file, then save and close

```
#dev/sda2
UUID=0d8912fc-db21-4928-9a5b-8eaffa8e911f /[COLOR="#0000ff"]media[/COLOR]/[COLOR="Red"]disc[/COLOR] ext3 relatime 0 2
```

Once the file has been saved and closed run these 3 in a terminal - replace [COLOR="DarkOrange"]user[/COLOR] with your username

```
sudo mount -a
```

There should have been no output from that command, if there is an error has occurred - set permissions aas required.
```
sudo chown [COLOR="#ff8c00"]user[/COLOR].[COLOR="DarkOrange"]user[/COLOR] /[COLOR="Blue"]media[/COLOR]/[COLOR="#ff0000"]disc[/COLOR]
sudo chmod 770 /[COLOR="#0000ff"]media[/COLOR]/[COLOR="Red"]disc[/COLOR]
```

---

### Post by fallen seraph on 2008-09-03
ah yes, that worked indeed. thank you very much :)

---

