---
title: "Lost swap"
date: 2008-08-29
forum: General Help
---

### Post by MangasColoradas on 2008-08-29
According to Conky and the system monitor I have no swap. When I installed Ubuntu I did create a swap, how can I let Ubuntu know it is there?

Doing fdisk -l shows it is there.

```
stone@ubuntu:~$ sudo fdisk -l
[sudo] password for stone: 


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c3f7c3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9857    58693477+   7  HPFS/NTFS
/dev/sda3            9858       11681    14651280   83  Linux
/dev/sda4           11682       14593    23390640    5  Extended
/dev/sda5           11682       14356    21486906   83  Linux
/dev/sda6           14357       14593     1903671   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8cb3ca15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

stone@ubuntu:~$ sudo mount /dev/sda6
mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab

```

---

### Post by Too Late on 2008-08-29
Post your /etc/fstab file and the output of "sudo blkid" command.

---

### Post by MangasColoradas on 2008-08-29
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=10b7e5ec-a013-4747-acb3-703b3570f1d1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=842d5f56-c9da-47c6-9477-1af12059e8cc /home           ext3    relatime        0       2
# /dev/sda2
UUID=05DE-C6ED  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=8cbba75e-91c2-4735-ab08-36490b034932 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

```
stone@ubuntu:~$ sudo blkid
/dev/sda1: UUID="A69C119F9C116B57" TYPE="ntfs" 
/dev/sda2: UUID="57E01AF9371D3F59" TYPE="ntfs" 
/dev/sda3: UUID="10b7e5ec-a013-4747-acb3-703b3570f1d1" TYPE="ext3" 
/dev/sda5: UUID="842d5f56-c9da-47c6-9477-1af12059e8cc" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda6: TYPE="swap" 
/dev/sdb1: UUID="25FFE92D42C3DF38" TYPE="ntfs" 
stone@ubuntu:~$ 

```

Thanks.

---

### Post by Too Late on 2008-08-29
Umm... Why your swap partition (sda6) doesn't have the UUID (in the blkid output)? How's that possible? :D I have no idea.

However, it's obvious that it won't be mounted, because in the fstab file it's identified by its UUID number. If you want, you can replace the UUID thing with the classic device name, like this:
```
# /dev/sda6
/dev/sda6 none swap sw 0 0
```
That should work, but before doing that I would like to know why the UUID is missing.

Edit: When editing the fstab file, the changes won't take effect until you reboot or run "sudo mount -a" command.

---

### Post by MangasColoradas on 2008-08-29
Thanks Toolate. :)

I decided to follow this post [http://ubuntuforums.org/showpost.php?p=1773316&postcount=3](http://ubuntuforums.org/showpost.php?p=1773316&postcount=3)

I got my swap file back and blkid now gives

```
stone@ubuntu:~$ sudo blkid
[sudo] password for stone: 
/dev/sda1: UUID="A69C119F9C116B57" TYPE="ntfs" 
/dev/sda2: UUID="57E01AF9371D3F59" TYPE="ntfs" 
/dev/sda3: UUID="10b7e5ec-a013-4747-acb3-703b3570f1d1" TYPE="ext3" 
/dev/sda5: UUID="842d5f56-c9da-47c6-9477-1af12059e8cc" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda6: TYPE="swap" UUID="e74151d1-b776-4891-9987-356ffcf91419" 
/dev/sdb1: UUID="25FFE92D42C3DF38" TYPE="ntfs" 
```

fstab looks like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=10b7e5ec-a013-4747-acb3-703b3570f1d1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=842d5f56-c9da-47c6-9477-1af12059e8cc /home           ext3    relatime        0       2
# /dev/sda2
UUID=05DE-C6ED  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=e74151d1-b776-4891-9987-356ffcf91419 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by MangasColoradas on 2008-08-29
This is weird.

```
stone@ubuntu:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/05DE-C6ED does not exist

```



Another thing is, my swap never seems to be used....

---

### Post by caljohnsmith on 2008-08-29
> **MangasColoradas said:**
> ```

stone@ubuntu:~$ sudo blkid
[sudo] password for stone: 
/dev/sda1: UUID="A69C119F9C116B57" TYPE="ntfs" 
[COLOR="Red"]/dev/sda2: UUID="57E01AF9371D3F59" TYPE="ntfs" [/COLOR]
/dev/sda3: UUID="10b7e5ec-a013-4747-acb3-703b3570f1d1" TYPE="ext3" 
/dev/sda5: UUID="842d5f56-c9da-47c6-9477-1af12059e8cc" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda6: TYPE="swap" UUID="e74151d1-b776-4891-9987-356ffcf91419" 
/dev/sdb1: UUID="25FFE92D42C3DF38" TYPE="ntfs"
```
```

# /dev/sda2
[COLOR="Red"]UUID=05DE-C6ED[/COLOR]  /windows        [COLOR="Red"]vfat[/COLOR]    utf8,umask=007,gid=46 0       1

```
That's your problem. :) The UUID is incorrect and so is the file system; it looks like what happened is you once had a FAT32 partition (sda2) and then reformatted it as NTFS. Is that what maybe happened? 

Anyway to correct it:
```
UUID=57E01AF9371D3F59 /windows ntfs defaults,uid=0,gid=46,auto,rw,nouser,umask=007 0 1  
```
Let me know how that goes or if you need more details/info. :)

---

### Post by Too Late on 2008-08-29
> **MangasColoradas said:**
> Another thing is, my swap never seems to be used....
Oops, I'm not sure if the "sudo mount -a" will mount the swap partition. I think it won't. But there's an other command for enabling swap without a reboot:
```
sudo swapon -U e74151d1-b776-4891-9987-356ffcf91419
```
or simply
```
sudo swapon /dev/sda6
```

---

### Post by MangasColoradas on 2008-08-30
Thanks guys I will try those things later today. :)

---

### Post by craetech on 2008-09-03
> **Too Late said:**
> or simply
```
sudo swapon /dev/sda6
```

Having the exact same problem as Mangas. The above worked like a charm. Though is a temporary fix for me. Every time I reboot, I still lose my swap.

So back to the question; why didn't blkid display the UUID of the swap device? Where does blkid pull data from? Is there a file to edit to get the swap UUID to appear in blkid output?

In any case, thanks much to Mangas and Too Late for getting us this far. :)

---

### Post by Elfy on 2008-09-03
The link in post 5 was about remaking the swap so I guess that's what was done to get the uuid back.

It's not so much editing a file to make the uuid appear but the partiton having one which can be read - I assume :)

---

