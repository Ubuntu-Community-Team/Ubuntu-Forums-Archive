---
title: "Ubuntu doesn´t detects a hard drive partition"
date: 2008-09-21
forum: General Help
---

### Post by DeepSeaNautilus on 2008-09-21
Hello I have four partitions on my system. Inside three of them I have windows, in the other I only have files. I installed ubuntu inside one of the windows partitions. All of them have NTFS filesystem. 
The problem I have is that ubuntu detects all partitions except that with my files. I looked at /dev/media, but there aren´t any sd* drives mounted there. It should be sd* as it is a sataII hard drive.

Thanks for all the help anyone can give me.

---

### Post by caljohnsmith on 2008-09-21
Ubuntu has to use a linux file system like ext2 or ext3 for instance; it can't use NTFS because NTFS does not have all the capabilities that it needs. You can access NTFS partitions easily in Ubuntu, but the Ubuntu install itself must use a linux file system. If you are able to boot into Ubuntu though, how about posting:
```
sudo fdisk -lu
```
And that will help clear up some of the confusion.

---

### Post by DeepSeaNautilus on 2008-09-21
> **caljohnsmith said:**
> Ubuntu has to use a linux file system like ext2 or ext3 for instance; it can't use NTFS because NTFS does not have all the capabilities that it needs. You can access NTFS partitions easily in Ubuntu, but the Ubuntu install itself must use a linux file system. If you are able to boot into Ubuntu though, how about posting:
```
sudo fdisk -lu
```
And that will help clear up some of the confusion.

That would be correct for normal installations, but there is a special install option in Hardy which lets a user install ubuntu inside windows using the later´s file systems.
I installed ubuntu on a NTFS partition and I can use that partition very well. The problem is not the partition in which I installed ubuntu, but another partition which I only use to store my files and doesn´t have any OS or program.
Any ideas?

---

### Post by caljohnsmith on 2008-09-22
> **DeepSeaNautilus said:**
> That would be correct for normal installations, but there is a special install option in Hardy which lets a user install ubuntu inside windows using the later´s file systems.
I installed ubuntu on a NTFS partition and I can use that partition very well. The problem is not the partition in which I installed ubuntu, but another partition which I only use to store my files and doesn´t have any OS or program.
Any ideas?
I see, so you did a Wubi install instead of a "normal" install. :) That's fine, but it would still greatly help if you would post the output of:
```
sudo fdisk -lu
```
Then I will know what drives/partitions your Ubuntu detects.

---

### Post by DeepSeaNautilus on 2008-09-28
> **caljohnsmith said:**
> I see, so you did a Wubi install instead of a "normal" install. :) That's fine, but it would still greatly help if you would post the output of:
```
sudo fdisk -lu
```
Then I will know what drives/partitions your Ubuntu detects.

Hello again, this is the output for sudo fdisk -lu:
255 cabezas, 63 sectores/pista, 30401 cilindros, 488397168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xad13ad13

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63    41945714    20972826    7  HPFS/NTFS
/dev/sda2        41945715   488375999   223215142+   f  W95 Ext'd (LBA)
/dev/sda5        41945778   287708084   122881153+   7  HPFS/NTFS
/dev/sda6       287708148   410589269    61440561    7  HPFS/NTFS
/dev/sda7       410589333   488375999    38893333+   7  HPFS/NTFS

The tags are in spanish, In english they should be something like this:

255 headers, 63 sectors, 30401 cylinders, 488397168 total sectors
Units = sector of 1 * 512 = 512 bytes
disk identifier: 0xad13ad13

Device     Boot        Start      End    Blocks      Id  System
/dev/sda1   *          63    41945714    20972826    7  HPFS/NTFS
/dev/sda2        41945715   488375999   223215142+   f  W95 Ext'd (LBA)
/dev/sda5        41945778   287708084   122881153+   7  HPFS/NTFS
/dev/sda6       287708148   410589269    61440561    7  HPFS/NTFS
/dev/sda7       410589333   488375999    38893333+   7  HPFS/NTFS

Thanks

---

### Post by caljohnsmith on 2008-09-28
OK, since I don't know which of your NTFS partitions has the files you want to access in Ubuntu, here is the way to mount sda1 (as an example) while you are in Ubuntu:
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
```
That will mount the sda1 partition on /media/sda1. You can change sda1 above for any of your other NTFS partitions and mount them that way. Then you should be able to browse the files in that partition, assuming you didn't get any errors when mounting it. Let me know how it goes and if you run into problems.

---

### Post by DeepSeaNautilus on 2009-01-03
> **caljohnsmith said:**
> OK, since I don't know which of your NTFS partitions has the files you want to access in Ubuntu, here is the way to mount sda1 (as an example) while you are in Ubuntu:
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
```
That will mount the sda1 partition on /media/sda1. You can change sda1 above for any of your other NTFS partitions and mount them that way. Then you should be able to browse the files in that partition, assuming you didn't get any errors when mounting it. Let me know how it goes and if you run into problems.

Ok, I think I found the problem. When I was using knoppix, it detected my files in 4 separate partitions which it mounted automatically and placed in /dev/media directory. But since I used a wubi installation, it only place 3 of them in such directory, but the fourth is mounted in /host, which was the partition that I was looking for. Thanks for the help.

---

