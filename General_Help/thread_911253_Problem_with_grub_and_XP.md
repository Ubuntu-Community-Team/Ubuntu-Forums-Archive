---
title: "Problem with grub and XP"
date: 2008-09-05
forum: General Help
---

### Post by hiKen on 2008-09-05
Hi! I don't know if anyone has already posted something like this, but i searched and i didnt find this exact problem.

I have been a ubuntu user for some months but recently i decided to install Windows Xp in an empty partition.

After installing XP GRUB didn't show up, but i found out in some site that you can restore grub by booting with the ubuntu CD. I did so, and now GRUB is the default boot-loader.

The problem is that i want to add a XP entry to GRUB, and i'm having some problems doing so.

From what i know about GRUB, i would have to modify /boot/grub/menu.lst and add some code with the XP entry

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff620747

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10444    83886080    7  HPFS/NTFS
/dev/sda2   *       10444       13055    20971520    7  HPFS/NTFS [COLOR="Red"]-> XP[/COLOR]
/dev/sda3           13055       28067   120586240    7  HPFS/NTFS
/dev/sda4           28068       30401    18747855    5  Extended
/dev/sda5           28068       30298    17920476   83  Linux
/dev/sda6           30299       30401      827316   82  Linux swap / Solaris

```

Windows XP is installed on sda2, therefore i would have to add something like this to menu.lst:

```

title		Microsoft Windows XP SP3
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```

...right? because sda2 -> hd0,1


But it doesn't work !(says something a missing NTLDR)

Obviously I'm doing something wrong, but i'm a newbie in linux :confused: so i'm kind of lost.....

Help please!!

cumpz

---

### Post by nacho32 on 2008-09-05
Have you tried the super grub boot loader it is a must have for dual triple quad boot
[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

---

### Post by hiKen on 2008-09-05
> **nacho32 said:**
> Have you tried the super grub boot loader it is a must have for dual triple quad boot
[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

Isn't that a bootable disk? I mean, it may be useful, but i don't want to recover to the cd every time i want to boot windows.... or can it change the grub permanently?

---

### Post by caljohnsmith on 2008-09-05
> **hiKen said:**
> 
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff620747

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       [COLOR="Red"]10444[/COLOR]    83886080    7  HPFS/NTFS
/dev/sda2   *       [COLOR="Red"]10444[/COLOR]       [COLOR="Red"]13055[/COLOR]    20971520    7  HPFS/NTFS 
/dev/sda3           [COLOR="Red"]13055[/COLOR]       28067   120586240    7  HPFS/NTFS
/dev/sda4           28068       30401    18747855    5  Extended
/dev/sda5           28068       30298    17920476   83  Linux
/dev/sda6           30299       30401      827316   82  Linux swap / Solaris

```

It looks to me like the crux of your problem is a partitioning issue; your start/stop points for the partitions above are on exactly the same cylinder, meaning they overlap. From Ubuntu, try the following:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by hiKen on 2008-09-05
```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
* FAT32 LBA                0   1  1 12160 254 37  195366376 [FD_BETA9SR2]
P HPFS - NTFS          13054  75 14 28066 149 51  241172480 [DADOS]
P Linux                28067   0  1 30297 254 56   35841008
L Linux Swap           30298   1  1 30400 254 47    1654616

```

(I don't know what this means)

What do you think?

---

### Post by nacho32 on 2008-09-05
> **hiKen said:**
> Isn't that a bootable disk? I mean, it may be useful, but i don't want to recover to the cd every time i want to boot windows.... or can it change the grub permanently?

yes it can correct problems :)

---

### Post by caljohnsmith on 2008-09-05
> **hiKen said:**
> ```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
* FAT32 LBA                0   1  1 12160 254 37  195366376 [FD_BETA9SR2]
P HPFS - NTFS          13054  75 14 28066 149 51  241172480 [DADOS]
P Linux                28067   0  1 30297 254 56   35841008
L Linux Swap           30298   1  1 30400 254 47    1654616

```

(I don't know what this means)

What do you think?
Something definitely seems to be wrong, because testdisk is not showing sda1 and sda2, but instead shows that FAT32 partition above that doesn't quite include the entire disk space used by sda1 and sda2. 

Go back into testdisk and proceed to the point where you get the screen above, and then do "proceed", "n" to find Vista partitions, hit enter and select "search!" so it does a deeper search which will take a while. After it is done with its deeper search, please post the output.

---

### Post by unutbu on 2008-09-05
hiKen, it does look like there is something wrong with the partition table. Try caljohnsmith's advice.  

Also, your problem has some resemblance to this one: [http://ubuntuforums.org/showthread.php?t=838469](http://ubuntuforums.org/showthread.php?t=838469)
especially when you say the NTLDR is missing.

Perhaps try meierfra.'s instructions in post #16: [http://ubuntuforums.org/showpost.php?p=5247162&postcount=16](http://ubuntuforums.org/showpost.php?p=5247162&postcount=16)
It will place a copy of NTLDR in your Windows partition.

Where he says
```

sudo mount /dev/sda1 /windows
```
instead type 
```

sudo mount /dev/sda2 /windows
```
since sda2 is your Windows partition.

---

### Post by hiKen on 2008-09-05
> **caljohnsmith said:**
> Something definitely seems to be wrong, because testdisk is not showing sda1 and sda2, but instead shows that FAT32 partition above that doesn't quite include the entire disk space used by sda1 and sda2. 

Go back into testdisk and proceed to the point where you get the screen above, and then do "proceed", "n" to find Vista partitions, hit enter and select "search!" so it does a deeper search which will take a while. After it is done with its deeper search, please post the output.

Sorry

The output I posted is from after Testdisk analyses the partitions:

This is what I get from Intel>Analyse :

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P HPFS - NTFS              0  32 33 10443 117 42  167772160
 2 * HPFS - NTFS          10443 117 43 13054  75 13   41943040 [XP]
 3 P HPFS - NTFS          13054  75 14 28066 149 51  241172480 [DADOS]
 4 E extended             28067   0  1 30400 254 63   37495710
 5 L Linux                28067   1  1 30297 254 63   35840952
   X extended             30298   0  1 30400 254 63    1654695
 6 L Linux Swap           30298   1  1 30400 254 63    1654632




*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

```

In the other post I posted what happens after "[Proceed]"

Although, I don't have the "N" option in that screen, only have **A** (add partition); **L** (load backup); **T** (change type); **P** (list files)

---

### Post by unutbu on 2008-09-05
What do you get when you type
```

sudo fdisk -lu
```
This will show you the partition table with Start and End numbers given in sectors. Maybe your partition table is okay, but the partitions do not end at cylinder boundaries.

---

### Post by hiKen on 2008-09-05
> **unutbu said:**
> What do you get when you type
```

sudo fdisk -lu
```
This will show you the partition table with Start and End numbers given in sectors. Maybe your partition table is okay, but the partitions do not end at cylinder boundaries.

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff620747

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   167774207    83886080    7  HPFS/NTFS
/dev/sda2   *   167774208   209717247    20971520    7  HPFS/NTFS
/dev/sda3       209717248   450889727   120586240    7  HPFS/NTFS
/dev/sda4       450896355   488392064    18747855    5  Extended
/dev/sda5       450896418   486737369    17920476   83  Linux
/dev/sda6       486737433   488392064      827316   82  Linux swap / Solaris

```

What to you think?

---

### Post by caljohnsmith on 2008-09-05
> **hiKen said:**
> ```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff620747

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   167774207    83886080    7  HPFS/NTFS
/dev/sda2   *   167774208   209717247    20971520    7  HPFS/NTFS
/dev/sda3       209717248   450889727   120586240    7  HPFS/NTFS
/dev/sda4       450896355   488392064    18747855    5  Extended
/dev/sda5       450896418   486737369    17920476   83  Linux
/dev/sda6       486737433   488392064      827316   82  Linux swap / Solaris

```

What to you think?
Yes, Unutbu was right, your partitions look fine. :)

I think your best bet would be to follow post #16 in that first thread that Unutbu recommended. That should make sure your Windows boot files are OK and that your Windows partition boot sector is OK too. That second link that Unutbu gave is the direct link to post #16, so you can just use that. Let us know how it goes.

---

### Post by hiKen on 2008-09-05
```

root@joao-laptop:~# sudo mkdir /windows
root@joao-laptop:~# sudo mount /dev/sda2 /windows
root@joao-laptop:~# ls /windows
Documents and Settings  MSNCleaner    RaidTool       System Volume Information
Fraps                   pagefile.sys  RECYCLER       WINDOWS
Intel                   Programas     splendid.info


```

From what I understood, there should be some boot.ini, NTLDR, NTDETECT.COM files in here, but the thing is that I don't remember having any of these files in this directory (well, at least not NTLDR or NTDETECT.COM).
Are you sure this is the right directory where these files should be?

---

### Post by caljohnsmith on 2008-09-05
> **hiKen said:**
> ```

root@joao-laptop:~# sudo mkdir /windows
root@joao-laptop:~# sudo mount /dev/sda2 /windows
root@joao-laptop:~# ls /windows
Documents and Settings  MSNCleaner    RaidTool       System Volume Information
Fraps                   pagefile.sys  RECYCLER       WINDOWS
Intel                   Programas     splendid.info


```

From what I understood, there should be some boot.ini, NTLDR, NTDETECT.COM files in here, but the thing is that I don't remember having any of these files in this directory (well, at least not NTLDR or NTDETECT.COM).
Are you sure this is the right directory where these files should be?
It looks to me like you have the wrong partition. Try the following:
```
sudo mkdir /mnt/sda1
sudo mkdir /mnt/sda3
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda3 /mnt/sda3
ls -l /mnt/sda1
ls -l /mnt/sda3
```
Please post the output.

---

### Post by hiKen on 2008-09-05
here it is:

```

root@joao-laptop:~# sudo mkdir /mnt/sda1
root@joao-laptop:~# sudo mkdir /mnt/sda3
root@joao-laptop:~# sudo mount /dev/sda1 /mnt/sda1
root@joao-laptop:~# sudo mount /dev/sda3 /mnt/sda3
root@joao-laptop:~# ls -l /mnt/sda1
total 0
root@joao-laptop:~# ls -l /mnt/sda3
total 85
drwxrwxrwx 1 root root  4096 2008-06-10 01:49 [...]
drwxrwxrwx 1 root root  8192 2008-08-29 15:47 [joao]
drwxrwxrwx 1 root root     0 2008-03-27 22:42 [audio]
-rwxrwxrwx 1 root root   572 2008-06-15 23:44 autorun.inf
drwxrwxrwx 1 root root  4096 2008-08-29 16:05 backup
drwxrwxrwx 1 root root 12288 2008-09-05 16:33 [filmes]
drwxrwxrwx 1 root root  4096 2008-08-16 15:57 [imagens]
drwxrwxrwx 1 root root 40960 2008-09-05 16:34 [jogos]
drwxrwxrwx 1 root root     0 2008-07-29 23:46 $RECYCLE.BIN
drwxrwxrwx 1 root root     0 2008-08-17 15:54 RECYCLER
drwxrwxrwx 1 root root  4096 2008-08-30 17:30 [series]
drwxrwxrwx 1 root root  4096 2008-08-17 22:42 [software]
drwxrwxrwx 1 root root  4096 2008-08-16 19:23 System Volume Information
drwxrwxrwx 1 root root     0 2008-06-17 23:12 [um]

```

sda1 was recently formatted, so it is still empty, and sd3 is a data partition, so there is not any boot files in there....

---

### Post by caljohnsmith on 2008-09-05
Yes, I wasn't looking closely enough at your directory listing for sda2, but that looks like it is indeed your Windows partition. You are definitely missing your boot files, so go to [the post Unutbu gave you]("http://ubuntuforums.org/showpost.php?p=5247162&postcount=16") and click on the link in that post to download the Windows boot files. I think you will have to edit the "boot.ini" file though, since your Windows is actually on the second partition. Just save those files you download into your sda2 root directory, and then post the contents of the "boot.ini" file. If you need any more details/info let me know.

---

