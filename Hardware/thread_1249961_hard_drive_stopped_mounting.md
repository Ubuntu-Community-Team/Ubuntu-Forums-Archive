---
title: "hard drive stopped mounting"
date: 2009-08-26
forum: Hardware
---

### Post by rhythmiccycle on 2009-08-26
There is a long story about what happened, but i'm just going to give the results.

i'm running ubuntu 9 desktop. i have 2 internal hardrives.

when everything was working find i sda used as storage, and the o.s. installed on sdb.

both drives are detected in the bios (before os is loaded)

but when ubuntu loads i get some errors. 

if i type reboot or shutdown now, everything starts up, and it seems to be working. but sda won't mount. the system then ends up freezing out of no where. 

i'm on a liveCD now.

here is some code i got:

```


ubuntu@ubuntu:/hdStore/var/www$ sudo mkdir /hd2
ubuntu@ubuntu:/dev$ sudo mount sda1 /hd2/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/dev$ dmesg | tail
[ 2200.328322] ext3_orphan_cleanup: deleting unreferenced inode 2072582
[ 2200.328336] ext3_orphan_cleanup: deleting unreferenced inode 2072581
[ 2200.328349] ext3_orphan_cleanup: deleting unreferenced inode 2072580
[ 2200.328361] EXT3-fs: sdb1: 7 orphan inodes deleted
[ 2200.328365] EXT3-fs: recovery complete.
[ 2200.341631] EXT3-fs: mounted filesystem with ordered data mode.
[ 2214.702921] EXT3-fs error (device sda1): ext3_check_descriptors: Inode table for group 37 not in group (block 219316226)!
[ 2214.703297] EXT3-fs: group descriptors corrupted!
[ 2345.588295] EXT3-fs error (device sda1): ext3_check_descriptors: Inode table for group 37 not in group (block 219316226)!
[ 2345.588705] EXT3-fs: group descriptors corrupted!
ubuntu@ubuntu:/dev$ 

```

can anyone help

---

### Post by rhythmiccycle on 2009-08-29
can anyone help me?

---

### Post by rhythmiccycle on 2009-09-02
please help,

---

### Post by Cato2 on 2009-09-02
Your /dev/sda1 filesystem (probably the root filesystem) is corrupted and needs an additional fsck.  From your live CD, just type "sudo fsck /dev/sda1" and answer yes to all the scary questions ...  However, if you have valuable data on that drive, and enough spare disk space to back up the whole drive, I'd recommend you first make a copy of the whole drive with GNU ddrescue (apt-get install gddrescue) into a file on a second drive.  ddrescue can cope with failing disks which seems likely here.

You might also want to try Parted Magic, a live CD that's specialised for PC recovery.

---

### Post by rhythmiccycle on 2009-09-02
thank you, Cato2.

i'm going to try your advice.


i've been asking for help with my hard drive problems for like a month, you are the first person to respond.

i installed gddrescue, but i don't understand how it works? i googled it, but i can't find any thing useful. i tried the code (gddrescue) but the command was not reconised

---

### Post by rhythmiccycle on 2009-09-03
i found this:
[http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)

i'll post what happens after i'm done trying it out

---

### Post by rhythmiccycle on 2009-09-03
i couldn't get the gddrescue to work but the link i posted on the last post showed me how to us ddrescue. 

then i did the fsck, 

and everything seems to be working now.

thanks

---

