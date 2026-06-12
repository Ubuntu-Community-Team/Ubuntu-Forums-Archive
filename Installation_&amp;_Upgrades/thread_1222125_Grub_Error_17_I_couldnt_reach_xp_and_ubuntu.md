---
title: "Grub Error 17: I couldnt reach xp and ubuntu"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by 1963 on 2009-07-24
I have a long story about the installation problems and since I dont know which one is critical for the solution, I will tell them all.

I had vista and ubuntu on my computer. Due to some problems, I replaced vista with xp  and this caused a problem. while booting, it directly started with xp and ubuntu option wasnt available. To solve this, I used the method in this link:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
(first post)

when I typed "find /boot/grub/stage1" command, the result was (hd0,0) and I completed the method without any doubt. However, I faced a bad surprise in booting process. I couldnt reach any of the operating systems!! It was saying "cannot mount selected partition". I looked the partition and it was installed in (hd0,1) not (hd0,0) as the result of command said. 

I tried to repeat the procedure for (hd0,1) but I got the same error. I tried to change menu.lst but it was already seen in (hd0,1) so it didnt solve my problem. 

Also, xp part gave an error about kernel file. Now. I am writing this post from the live CD. I may not be clear in my post because of my english. sorry about that. I appreciate all the help.

---

### Post by merlinus on 2009-07-24
You might try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

If that does not solve the problem, post results of

```
sudo fdisk -l
```

---

### Post by 1963 on 2009-07-24
I dont have any of the required materials for supergrub right now.

```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# fdisk -l

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86b7a0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              12        6538    52428127+  83  Linux
/dev/sda2            6539       14017    60075067+   7  HPFS/NTFS
/dev/sda3   *       14018       14409     3148740   db  CP/M / CTOS / ...

```

---

### Post by merlinus on 2009-07-24
According to this, ubuntu is in (hd0,0), and menu.lst is probably there as well.

Try this first, from a terminal whilst running from the live cd:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```and restart.

If that does not fix things, then mount your ubuntu partition from the live cd (you can probably do this by clicking on it in Places).  Then navigate to /media/disk, or something like that, and look for /boot/grub/menu.lst, rightclick on it to open it with a text editor, and copy-and-paste the contents here.

---

### Post by oldfred on 2009-07-24
This thread has some more info:
[http://ubuntuforums.org/showthread.php?t=1203368](http://ubuntuforums.org/showthread.php?t=1203368)

According to your fdisk linux is in hd0,0. Also you have no swap and have the boot flag on your cp/m(?)  partition. Your boot flag should be on your windows partition if that is what you want to boot for windows.

---

### Post by 1963 on 2009-07-24
Thanks for your replies. I solved the problem. I checked menu.lst again and edit root part. I learnt from the other forums, I need to write not the sda number but one less of it. ex: Ubuntu is seen on sda1, thus I write root part (hd0,0) instead of (hd0,1)

Thanks again.

---

### Post by merlinus on 2009-07-24
Excellent!  BTW, did you need to change the boot flag?  IIRC, having makeactive in the menu.lst stanza for windows does the same thing.

---

