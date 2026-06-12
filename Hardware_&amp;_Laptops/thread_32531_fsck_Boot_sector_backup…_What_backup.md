---
title: "fsck: Boot sector backup… What backup?"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by elmimmo on 2005-05-08
On the LiveCD forum I posted a question about running fsck from a LiveCD, in order to try to recover what's left of a corrupted Hard disk drive. I canot plug that hard disk, from a notebook PC, into another computer, since the other one I have is an iMac (which does not accept 2 hard drives. Hence the use of a LiveCD.

But since the question revolves more around recovering a hard disk than using the LiveCD and the thread got stalled at a fsck issue, I thought about asking for help here.

This is the output of running fsck```
 root@ubuntu:/home/ubuntu # fsck /dev/hda1
fsck 1.35 (28-Feb-2004)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup .
Differences: (offset:original/backup)
  65:03/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
Read 32 bytes at 683470848:Input/output error
``` Backup? Does a FAT32 system back itself up? Should I try (at my own responsability of course) action 2, or is it deemed to give the final hit to whatever might have been recoverable?

I did not do a backup, that's for sure. What is to be expected if I run action 2?

---

### Post by MegaBill on 2006-05-08
I need to know how to fix this as well, as I have this exact same problem.  However on mine, there are even more differences listed...

So /bump

---

### Post by felipefoz on 2006-05-09
this also happened to me, does anyone have a solution? i didn't choose any of the two first options, 'cause i've important data on hda1, so i need to be sure what i'm doing!
the strang is: i have dapper and the breezy installed, but only in dapper this happens at the boot time, in breezy it goes smoothly!

---

### Post by ipa on 2006-05-22
Same here.

Installed dapper on my daughters k7 to hda2, no problem.
Installed xp to hda1.
Booted into dapper install cd restore, ran grub-install /dev/hda.
Now when I boot into dapper it drops out of the boot splash to inform me that there are differences between the boot sector and its backup. All is well apart from this disturbing message.

I ran grub-install again, hoping that grub would over-write the boot sector backup, but the message remains.

Ivan

---

### Post by felipefoz on 2006-05-23
[QUOTE=ipa]Same here.

Installed dapper on my daughters k7 to hda2, no problem.
Installed xp to hda1.
Booted into dapper install cd restore, ran grub-install /dev/hda.
Now when I boot into dapper it drops out of the boot splash to inform me that there are differences between the boot sector and its backup. All is well apart from this disturbing message.

I ran grub-install again, hoping that grub would over-write the boot sector backup, but the message remains.

Ivan[/QUOTE]
so, i think i solved this problem! dapper installs different the disks and lists  the disks different as well. That was my /etc/fstab before:
```
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=000,gid=46	0       1
```
So, i changed, and put almost the same as in breezy, put also the permission to any user to mount, and to not mount automatically at boot, and also changed the end which was the number 1, and now is back 0 (which is the only thing that it's  important for our problem with "differences between boot sector and...") :
```
/dev/hda1       /media/hda1     vfat    users,noauto,utf8,umask=000	0       0
```
Now during the boot, it doesn't complain about differences anymore. it just goes smoothly and faster, preety much faster than in breezy! Let the problem with FAT systems with Windows, it is working nice in Ubuntu, and in Windows, and the problem with "the differences between the boot sector and its backup" doesn't annoy me anymore! =D

---

### Post by ipa on 2006-05-23
[QUOTE=felipefoz]so, i think i solved this problem! dapper installs different the disks and lists  the disks different as well. That was my /etc/fstab before:
```
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=000,gid=46	0       1
```
So, i changed, and put almost the same as in breezy, put also the permission to any user to mount, and to not mount automatically at boot, and also changed the end which was the number 1, and now is back 0 (which is the only thing that it's  important for our problem with "differences between boot sector and...") :
```
/dev/hda1       /media/hda1     vfat    users,noauto,utf8,umask=000	0       0
```
Now during the boot, it doesn't complain about differences anymore. it just goes smoothly and faster, preety much faster than in breezy! Let the problem with FAT systems with Windows, it is working nice in Ubuntu, and in Windows, and the problem with "the differences between the boot sector and its backup" doesn't annoy me anymore! =D[/QUOTE]

Thanks for this,
I changed the final number from 1 to 0 for hda in fstab as you suggested, and that stops the message during boot :-) 

It seems that this option turns off fsck file system checking during boot, so I guess the offset between the boot sector and its backup remains.

Cheers
Ivan

---

### Post by jdw on 2006-07-05
If you want to fix this problem, just do:

(assuming your windows fat32 partition is on /dev/hdc1)

sudo dosfsck -ar /dev/hdc1

Choose to make the original the backup (option 1 I think), and then choose "Y".

---

### Post by treris on 2006-07-06
changing those 1's into 0's in fstab did the trick here as well, thanks for solving that people because it was really bugging me everytime I rebooted kubuntu (which is not all that often ofcourse but still)

---

### Post by fusiontu on 2006-07-12
> **felipefoz said:**
> so, i think i solved this problem! dapper installs different the disks and lists  the disks different as well. That was my /etc/fstab before:
```
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=000,gid=46	0       1
```
So, i changed, and put almost the same as in breezy, put also the permission to any user to mount, and to not mount automatically at boot, and also changed the end which was the number 1, and now is back 0 (which is the only thing that it's  important for our problem with "differences between boot sector and...") :
```
/dev/hda1       /media/hda1     vfat    users,noauto,utf8,umask=000	0       0
```
Now during the boot, it doesn't complain about differences anymore. it just goes smoothly and faster, preety much faster than in breezy! Let the problem with FAT systems with Windows, it is working nice in Ubuntu, and in Windows, and the problem with "the differences between the boot sector and its backup" doesn't annoy me anymore! =D


actually, this trick is not a solution! it just forces ubuntu not to mount this system...

But, in my case, I need this drive as long as it contains shared projects between windows and linux...

would you tell me exactly please how can I make the backup = original?

---

### Post by State on 2006-07-13
the solution from jdw worked for me

**sudo dosfsck -ar /dev/your_fat32**
original -> backup

---

### Post by teet on 2006-07-21
This is the error I'm getting:
> 
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  430:4e/52, 431:54/65, 432:4c/6d, 433:44/6f, 434:52/76, 435:20/65, 436:69/20
  , 437:73/64, 438:20/69, 439:6d/73, 440:69/6b, 442:73/20, 443:69/6f
  , 444:6e/72, 445:67/20, 446:ff/6f, 447:0d/74, 448:0a/68, 449:44/65
  , 450:69/72, 451:73/20, 452:6b/6d, 453:20/65, 454:65/64, 455:72/69
  , 456:72/61, 457:6f/2e, 458:72/ff, 459:ff/0d, 460:0d/0a, 461:0a/44
  , 462:50/69, 463:72/73, 464:65/6b, 465:73/20, 466:73/65, 467:20/72
  , 468:61/72, 469:6e/6f, 470:79/72, 471:20/ff, 472:6b/0d, 473:65/0a
  , 474:79/50, 475:20/72, 476:74/65, 477:6f/73, 478:20/73, 479:72/20
  , 480:65/61, 481:73/6e, 482:74/79, 483:61/20, 484:72/6b, 485:74/65
  , 486:0d/79, 487:0a/20, 488:00/74, 489:00/6f, 490:00/20, 491:00/72
  , 492:00/65, 493:00/73, 494:00/74, 495:00/61, 496:00/72, 497:00/74
  , 498:00/0d, 499:00/0a, 506:bf/cb, 507:cc/d8


I recently reformatted my Windows XP Partition.  Of course this screwed up my MBR since windows overwrote it and I ended up having to reinstall Dapper (not a big deal really since I had a seperate /home partition).  Note:  During my reinstall of Windows I somehow deleted my /boot partition...whoops...that's why I had to totally reinstall Dapper instead of just using the grub-install trick.

I'll give this fix a shot and report back here :)

-teet

Update:  It seems to have fixed the error message.  However, it still pauses and bails out of the usplash screen where this error used to be, but then continues to boot just fine.  Not a problem really...just don't get to see the pretty usplash.

---

### Post by fusiontu on 2006-07-23
> **jdw said:**
> If you want to fix this problem, just do:

(assuming your windows fat32 partition is on /dev/hdc1)

sudo dosfsck -ar /dev/hdc1

Choose to make the original the backup (option 1 I think), and then choose "Y".


if my partition is called sda7 in /media/sda7

what should it be called in /dev/ ?? I just can't find hdc7 or anything starting with hdc
please help

**EDIT: oups... It's /dev/sda7 ... sorry for this silly post**

---

### Post by tisarus on 2006-07-25
I thougth I am alone!! I just installed and ever tried for 
sudo dosfsck -parameters
you know, I lost my other windowsXP OS (dual boot), so I get back to 5.10, it worked well.. anyway now! I work on 6.06 and wait for the next 6.10!!

---

### Post by fusiontu on 2006-07-25
Guys, when i followed this technique (sudo dosfsck -ar /dev/sda7), the booting speed remained the same...
but instead of showing the error, it's doing dosfsck... my ntfs drive loads very fast.

can I make it faster?

---

### Post by teet on 2006-07-25
> **fusiontu said:**
> Guys, when i followed this technique (sudo dosfsck -ar /dev/sda7), the booting speed remained the same...
but instead of showing the error, it's doing dosfsck... my ntfs drive loads very fast.

can I make it faster?

It does the same thing for me...it got rid of the error, but it still bails at of usplash and pauses at the dosfsck thing for a few seconds.  It really isn't that much of an issue for me since I hibernate my laptop 90% of the time.

-teet

---

### Post by fusiontu on 2006-07-25
> **teet said:**
> It does the same thing for me...it got rid of the error, but it still bails at of usplash and pauses at the dosfsck thing for a few seconds.  It really isn't that much of an issue for me since I hibernate my laptop 90% of the time.

-teet

yup... but I'd rather find a solution for that! is there any?

---

### Post by punkrockguy318 on 2006-09-01
> **jdw said:**
> If you want to fix this problem, just do:

(assuming your windows fat32 partition is on /dev/hdc1)

sudo dosfsck -ar /dev/hdc1

Choose to make the original the backup (option 1 I think), and then choose "Y".

Thank you! that fixed my problem :)

---

### Post by zensor on 2006-10-21
Hi

how can I find out, which part was corrupted, the boot-sector or the backup.

What happened:
I used windows. It frooze. It had to shut-down the Laptop by pressing the IO-Key ten seconds. 
Starting Ubuntu showed me many corruüted files all in hda1/windows/...
Ubuntu told me everytime from then:

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00

Now I'm very unsure, if the boot-sector or the backup is corrupted. Can I backup both somehow and try each?
Is there any possibility to read the boot-sector and its backup?

This happened before and Windows didn't work for a long time...

Thanks

---

### Post by paradroid on 2006-11-12
> **State said:**
> the solution from jdw worked for me

**sudo dosfsck -ar /dev/your_fat32**
original -> backup

this worked fine for me! thanks, pal.

I tried some further investigations and used the hex numbers from the boot sector differences message as input for php-cli:

[PHP]php -r "echo chr(0x53).chr(0x48).chr(0x41).chr(0x52).chr(0x45).chr(10);" // chr(10) is for new-line ;)[/PHP]         

what results: **SHARE**

This was the name I gave this partition during installation process.

> 
Differences: (offset: original/backup)
  71:53/00, 72:48/00, 73:41/00, 74:52/00, 75:45/00, 76:20/00, 77:20/00, 78:20/00, 79:20/00, 80:20/00, 81:20/00


Maybe this helps you to find the reason of your problem.

Cheers!

---

### Post by iqplay on 2007-01-06
but, additional problem occurs.
```
~$ sudo dosfsck -ar /dev/hda5
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  90:33/8c, 91:c9/c8, 93:d1/d0, 95:f4/ff, 97:8e/fb, 98:c1/8e, 99:8e/d8
  , 100:d9/8e, 101:bd/c0, 102:00/fc, 103:7c/bf, 104:88/20, 105:4e/00
............
............
  , 485:74/39, 486:0d/39, 487:0a/00, 505:ac/00, 506:bf/00, 507:cc/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
/:7zH:7hP:4uQ:5AX
  Bad file name.
1) Drop file
2) Rename file
3) Auto-rename
4) Keep it
? 

```

The " Bad file name." prompt raised again and again(more than 100 times) for different files](*,) , how can i do?

------
The file name show in Window$ correctly, 
LANG=zh_CN.UTF-8

---

### Post by iqplay on 2007-01-06
> **iqplay said:**
> but, additional problem occurs.
```
~$ sudo dosfsck -ar /dev/hda5
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  90:33/8c, 91:c9/c8, 93:d1/d0, 95:f4/ff, 97:8e/fb, 98:c1/8e, 99:8e/d8
  , 100:d9/8e, 101:bd/c0, 102:00/fc, 103:7c/bf, 104:88/20, 105:4e/00
............
............
  , 485:74/39, 486:0d/39, 487:0a/00, 505:ac/00, 506:bf/00, 507:cc/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
/:7zH:7hP:4uQ:5AX
  Bad file name.
1) Drop file
2) Rename file
3) Auto-rename
4) Keep it
? 

```

The " Bad file name." prompt raised again and again(more than 100 times) for different files](*,) , how can i do?

------
The file name show in Window$ correctly, 
LANG=zh_CN.UTF-8

i got it!
CHANGE all line contain 'vfat' which like&#65306;
UUID=50FC-77D8  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
TO&#65306;
UUID=50FC-77D8  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       0

as my local is zh_CN, also add "iocharset=utf8,codepage=936" to show file name correctly:
UUID=50FC-77D8  /media/hda5     vfat    defaults,utf8,iocharset=utf8,codepage=936,umask=007,gid=46 0       0

---

### Post by manen on 2007-07-20
> **fusiontu said:**
> actually, this trick is not a solution! it just forces ubuntu not to mount this system...

But, in my case, I need this drive as long as it contains shared projects between windows and linux...

would you tell me exactly please how can I make the backup = original?

Well, that file system won't be mounted, of course, because of the "noauto" option.

This trick works well even if you only change the <pass> field of fstab file from 1 to 0.

From this:
```
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=000,gid=46	0       1
```
To this:
```
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=000,gid=46	0       0
```
At least it worked for me.

---

### Post by Neobuntu on 2008-02-06
I think the -a and the -r options for dosfsck are opposites, are they not?

---

### Post by hartnegg on 2008-03-31
Fat32 has a backup of the boot sector in sector 6,  the boot sector is in sector 0
(see [http://support.microsoft.com/kb/247575/EN-US/](http://support.microsoft.com/kb/247575/EN-US/)).

The bytes at offset 71 contain the volume label.
Four bytes starting at 67 contain the volume serial number.
(see [http://hjem.get2net.dk/rune_moeller_barnkob/filesystems/fat32.html](http://hjem.get2net.dk/rune_moeller_barnkob/filesystems/fat32.html))

If only bytes in this range differ, it probably doesn't matter which version one selects to copy over the other.

Byte 65 is reserved and should be unused.

If you don't want to risk problems, make a copy of both sectors, then try both alternatives.

regards,
Klaus

---

### Post by deustech on 2008-06-22
> **hartnegg said:**
> 

If you don't want to risk problems, make a copy of both sectors, then try both alternatives.



how i can make this sectors backup??? 

10x

---

