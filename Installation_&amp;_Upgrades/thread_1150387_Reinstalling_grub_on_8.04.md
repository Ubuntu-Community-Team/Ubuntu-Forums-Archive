---
title: "Reinstalling grub on 8.04"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by livinloud on 2009-05-06
Hi everyone, I just reinstalled my Windows XP Pro SP3 on my laptop.

It's a LenovoN100 with a SATA hard drive

I'm trying to resintall grub with my 8.04 live CD but I'm always having errors

```

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

grub> 


```this is the first error I get

I used this tutorial te help me out 

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I tried also to use the grub-install but I get this error

```

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# grub-install --root-directory=/mnt/root /dev/sda
The file /mnt/root/boot/grub/stage1 not read correctly.
root@ubuntu:/home/ubuntu# 


```my device.map file 

```

(fd0)   /dev/fd0
(hd0)   /dev/sda

```fdisk -l

```

root@ubuntu:/boot/grub# fdisk -l
omitting empty partition (5)

Disque /dev/sda: 100.0 Go, 100030242816 octets
255 heads, 63 sectors/track, 12161 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xcccdcccd

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        9224    74091748+   7  HPFS/NTFS
/dev/sda2            9225       12161    23591452+   f  W95 Etendu (LBA)
/dev/sda3           11785       12161     3028221   82  Linux swap / Solaris
/dev/sda5            9225       11784    20563137   83  Linux
root@ubuntu:/boot/grub# 


```I hope someone can help 

Thanks

---

### Post by triunenature on 2009-05-06
```

sudo grub-update

```

Im not sure if that will work, or if thats what your looking for.  I know when i have grub issues thats how i resolve them, but i don't know it that will make your situation better

---

### Post by zvacet on 2009-05-06
Did you followed insrtuctions from link you are used?I ask you this because I don't believe that you will get (hd0,5) as partition for root.it is (hd0,4).Read [this.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by livinloud on 2009-05-06
Yes I tried grub-update, it worked without any error, but it didn't install grub on the MBR

For the hd(0,4) This is empty.

For the link you sent me, I tried it already with no success.

I found somewhere around 5 people with similar problem and didn't found any way to reinstall grub.

And my old menu.lst list my root to the hd0,5 too so I think this is good, I think.

---

### Post by caljohnsmith on 2009-05-06
> **livinloud said:**
> 
```

root@ubuntu:/boot/grub# fdisk -l
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disque /dev/sda: 100.0 Go, 100030242816 octets
255 heads, 63 sectors/track, 12161 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xcccdcccd

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        9224    74091748+   7  HPFS/NTFS
/dev/sda2            [COLOR="Red"]9225       12161[/COLOR]    23591452+   f  W95 Etendu (LBA)
/dev/sda3           [COLOR="Red"]11785       12161[/COLOR]     3028221   82  Linux swap / Solaris
/dev/sda5            9225       11784    20563137   83  Linux
root@ubuntu:/boot/grub# 


```
Just for your future reference, any time fdisk reports "omitting empty partition (X)", unfortunately that is a sure sign that your HDD's partition table is corrupt. As shown highlighted in red above, your sda3 primary swap partition is inside of your sda2 extended partition; therefore sda3 should be a logical partition instead. Grub is quite sensitive to problems with a HDD's partition table, so that is why you are having problems reinstalling Grub. If you would like help fixing your partition table, how about posting:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

John

---

### Post by livinloud on 2009-05-06
Hi, thanks for the information, I never thought that my partition table could have been corrupted

here are the results of the 2 commands

```

root@ubuntu:/# fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   148183559    74091748+   7  HPFS/NTFS
/dev/sda2       148183560   195366464    23591452+   f  W95 Ext'd (LBA)
/dev/sda3       189310023   195366464     3028221   82  Linux swap / Solaris
/dev/sda5       148183686   189309959    20563137   83  Linux
root@ubuntu:/# sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=148183497, Id= 7, bootable
/dev/sda2 : start=148183560, size= 47182905, Id= f
/dev/sda3 : start=189310023, size=  6056442, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=148183686, size= 41126274, Id=83


```

---

### Post by caljohnsmith on 2009-05-06
OK, how about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt
```
And please post the output. Then reboot and post the output of all the following commands:
```
sudo fdisk -lu
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
If the Grub commands complete without error this time, go ahead and reboot to see if you get the Grub menu on start up. Let me know how it goes or if you run into problems.

John

---

### Post by livinloud on 2009-05-06
Thanks you're the best.

```

root@ubuntu:/home/ubuntu# sfdisk --no-reread -f /dev/sda < /home/ubuntu/Desktop/partition_table.txt

Disk /dev/sda: 12161 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   9223    9224-  74091748+   7  HPFS/NTFS
/dev/sda2       9224   12160    2937   23591452+   f  W95 Ext'd (LBA)
/dev/sda3      11784+  12160     377-   3028221   82  Linux swap / Solaris
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       9224+  11783    2560-  20563137   83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 148183559  148183497   7  HPFS/NTFS
/dev/sda2     148183560 195366464   47182905   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     148183686 189309959   41126274  83  Linux
/dev/sda6     189310023 195366464    6056442  82  Linux swap / Solaris
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   148183559    74091748+   7  HPFS/NTFS
/dev/sda2       148183560   195366464    23591452+   5  Extended
/dev/sda5       148183686   189309959    20563137   83  Linux
/dev/sda6       189310023   195366464     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

