---
title: "Installed 8.04.01 onto 50gb... no space afterwards"
date: 2008-08-25
forum: General Help
---

### Post by h4lfl1ng on 2008-08-25
I installed ubuntu 8.04.1 onto my second partition that was 50gb, and i selected the 4gb install. Now I was trying to install kubuntu-kde4-desktop and it gave me a error saying theres not enough disk space.. now i cant uninstall it. The thing is that this is a fresh install... i havent added anything except ruby/rails. 

```

ilya@desktop:~$ sudo apt-get remove kubuntu-kde4-desktop
Reading package lists... Error!
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
ilya@ilya-desktop:~$ 

```

All help is much appreciated, gimme something juicy :D


edit: gparted says both partitions have free space.. the ubuntu part has like 42gb free..

---

### Post by phidia on 2008-08-25
I believe this error is really about the 4GB ssd where everything wants to install to-not your amount of partition space. Try > sudo apt-get autoclean
after that completes update and try again.

---

### Post by h4lfl1ng on 2008-08-25
Same error, unfortunatly

---

### Post by ugm6hr on 2008-08-25
> **h4lfl1ng said:**
> I installed ubuntu 8.04.1 onto my second partition that was 50gb, **and i selected the 4gb install.** 

What do you mean by this?

Ubuntu does not allow you to choose the install size.

---

### Post by h4lfl1ng on 2008-08-25
When you select install inside windows.. it gives you the 4gb option, from 4 to 15gb are the choices. Not really sure what that means though..

---

### Post by phidia on 2008-08-25
This is a wubi install?
Open a terminal and enter this: > sudo fdisk -l post the output.

---

### Post by h4lfl1ng on 2008-08-26
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cbb0cbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8286    66557263+   7  HPFS/NTFS
/dev/sda2            8287       14593    50660977+   7  HPFS/NTFS

```

i reinstalled with the 5gb option.. looks like its headed for the same thing. I cant install it without wubi.. it either gives like a faulty disk/hdd error or it produces initramfs screen. Ive done several burns, fast, slowest, medium with buffer protection but still bad, ive burned v6 and 7 before and never had problems.. maybe its the cds..

---

### Post by h4lfl1ng on 2008-08-27
bump, help is appreciated

---

### Post by ugm6hr on 2008-08-28
I'll move this to the Wubi section.

Hopefully some users with experience will be able to help.

---

### Post by Orlsend on 2008-08-28
Okay when you choose with the wubi install, you choose the maximun space that wubi can use, In your case I believe you chose the 4GB which is the minimum space that Wubi needs to work.

So next time choose 50GB instead of 4GB in the wubi installer.

They migth be a way to resize your wubi disk, but I am not familiar with it

---

### Post by blommethomas on 2008-08-28
are you really sure you did not mess things up during your partitioning?

I saw the output of your fdisk and you do indeed have a 50 G partition but that one has an NTFS filesystem, which is for windows.  I don't think you can install ubuntu on that...

it does however mention a first partiton of +60G(which I suppose is your Windows partition).  If you count those 2 together, you have less than 6 gig left.

Problem is that that third partition isn't mentioned so it must be unallocated space.  Is it possible to run the fdisk command again and give the output?

fdisk /dev/sda

and then type p
to quit fdisk, type q

---

### Post by ugm6hr on 2008-08-28
I've never used Wubi, but I believe it allows you to install Ubuntu without re-partitioning.

Hence it can install in an NTFS partition.

It would make sense that if you chose a "4GB" install, then that is all the space you have allocated from within that partition.  KDE would therefore not fit.

Of course, I have no idea whether these presumptions about Wubi are correct or not.

---

### Post by Orlsend on 2008-08-28
> **ugm6hr said:**
> I've never used Wubi, but I believe it allows you to install Ubuntu without re-partitioning.

Hence it can install in an NTFS partition.

It would make sense that if you chose a "4GB" install, then that is all the space you have allocated from within that partition.  KDE would therefore not fit.

Of course, I have no idea whether these presumptions about Wubi are correct or not.
Thats what I believe it happend

---

### Post by h4lfl1ng on 2008-09-02
So selecting a bigger size install wont take up all of the space? just let it be used?.. also thru wubi you cant partition it as ext3 or anything else.. only ntfs :( because it doesnt see other partitions that arent ntfs..

---

### Post by ugm6hr on 2008-09-02
> **h4lfl1ng said:**
> So selecting a bigger size install wont take up all of the space? just let it be used?.. also thru wubi you cant partition it as ext3 or anything else.. only ntfs :( because it doesnt see other partitions that arent ntfs..

Wubi will not allow you to do much more than just dabble with Ubuntu.  It is not a complete installation.  It does not partition anything - it installs within Windows partitions (as far as I know).

If you are serious about using Ubuntu, I would suggest a proper dual-boot installation.

There are plenty of How-Tos about dual-booting (see the Start here... link below).

If not - just continue to dabble with Wubi - and read a little more about Wubi.

---

### Post by h4lfl1ng on 2008-09-03
The problem is that it wont install directly from cd.. it just gives problems either initramfs or other stuff.. I made several burns on slowest and still. I had no problems with ubuntu 6 and 7, and centos4, gentoo, fedora and other distros.. this is the only one im having problems with.

---

### Post by h4lfl1ng on 2008-09-18
Still no luck.. cant install it. Even with the alternate iso(text installer), ive tried ext3, ext2,reiserfs.. nothing. with and without swap. Multiple disks, from wubi and just a normal install. Also tried oem, acpi off.. This is getting ridiculous. Really thinking of just putting fedora on this partition..

---

