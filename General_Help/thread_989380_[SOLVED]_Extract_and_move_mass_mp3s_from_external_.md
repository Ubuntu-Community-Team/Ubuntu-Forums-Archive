---
title: "[SOLVED] Extract and move mass mp3s from external hdd"
date: 2008-11-21
forum: General Help
---

### Post by Ripfox on 2008-11-21
Ok so I have a 500 gb mybook external usb drive that has a bunch of crap like photos, documents, exe files AND a TON of music on it. Whats the best way to run a program to extract the mp3s from that disk on to my laptop without having to go in and sift through the whole thig folder by folder? I know most music players like RB and Exaile ect will add them to their LIBRARY, but I want them physically moved onto my laptops hdd in the fastest most efficient way possible.

Thanks for suggestions

Ripfox

---

### Post by Wayne_V on 2008-11-21
I believe Amarok, maybe RB, maybe Banshee, will scan a disk for MP3's and then copy them to it's local mp3 directory.

Or you could do something like:

$ mkdir ~/myMusic
$ cd /old_disk
$ find . -name \*.mp3 | cpio -pdm ~/myMusic

This would scan the entire disk for any .mp3 files and copy them (with directory structure) to the new disk.  Lots of variations you could do on that ....

---

### Post by Ripfox on 2008-11-21
What if I already have a folder named Music and the disk is called Mybook. Sorry I need to learn more command line :(

---

### Post by Wayne_V on 2008-11-21
Then

$ df
(see where Mybook is mounted)
$ cd /path/to/Mybook
$ find . -name \*.mp3 | cpio -pdm ~/Music

This assumes all mp3's are named <name>.mp3  - if not, you'll have to adjust the find command and run it multiple times.

---

### Post by Ripfox on 2008-11-21
/dev/sde1            312492320  67290336 245201984  22% /media/My Book
/dev/sdb               4012624        84   4012540   1% /media/disk
**@AMD-laptop:~$ cd /dev/sde1
bash: cd: /dev/sde1: Not a directory

---

### Post by Ripfox on 2008-11-21
Never mind I used
>  cd /media/My\ Book

---

