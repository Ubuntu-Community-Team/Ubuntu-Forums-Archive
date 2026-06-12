---
title: "Ubuntu 7.10 Won't show NTFS partition !!!"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by beko on 2008-02-18
Hi.. I have a vista PC with 2 partitions  in NTFS format  and I decided to   remove vista then install Ubuntu on it .
I inserted UBUNTU CD then deleted the VISTA partition then created swap , root and home partitions .
I can see that the second drive is already mounted under Ubuntu.
Everything went smooth until the first boot and when I opened my computer I couldn't find the D drive (NTFS) I tried   sudo fdisk -l    and here is the results :
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       19457   156288321    5  Extended
/dev/sda5            9794       19457    77618488+   7  HPFS/NTFS
/dev/sda6               1         486     3903700+  82  Linux swap / Solaris
/dev/sda7             487        2918    19535008+  83  Linux
/dev/sda8            2919        9793    55223406   83  Linux

Partition table entries are not in disk orderAlso I can see that there is a folder under media called sda5 but it's empty !!!

Any help will be appreciated

---

### Post by kaginken on 2008-02-18
You stated that you, "removed the Vista partition"...so unless I'm misunderstanding your post...you deleted all your stuff!!!  :confused:

---

### Post by beko on 2008-02-18
No, I  just deleted one partition which is C drive and kept the D drive for my documents and files.

---

### Post by kaginken on 2008-02-18
Ubuntu 7.10 supports ntfs read and read/write, so that's not the problem.

If you've successfully mounted it but cannot see anything - could be a permissions prob.

What's your /etc/fstab show?

Can you boot into winblows and see your stuff?

Try umounting it and then mounting it again, any difference?

---

### Post by Bruce S on 2008-02-18
I think that deleting C drive was not a good idea. Windows OS is on that and  you will no longer have any access to it.
  You will have to reinstall Windows OS.
  Good luck

---

### Post by beko on 2008-02-18
> **kaginken said:**
> Ubuntu 7.10 supports ntfs read and read/write, so that's not the problem.

If you've successfully mounted it but cannot see anything - could be a permissions prob.

What's your /etc/fstab show?

Can you boot into winblows and see your stuff?

Try umounting it and then mounting it again, any difference?

Here is my fstab :
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=bda3c88a-5c19-47d7-b330-8034ee79ca43 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=37c7d476-b5a5-48ae-9b4c-092001f53e59 /home           ext3    defaults        0       2
# /dev/sda5
UUID=EED89983D8994B2B /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=33694013-c85f-465f-a7ae-6b72fee0291f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by beko on 2008-02-18
> **Bruce S said:**
> I think that deleting C drive was not a good idea. Windows OS is on that and  you will no longer have any access to it.
  You will have to reinstall Windows OS.
  Good luck
Why I need to reinstall windows again ?

---

### Post by kaginken on 2008-02-18
Contrare, my good friend, blowing away vista was the smartest thing I've read in the forum tonight!  :D

However, I forgot that you did that when I mentioned above to try booting into microsloths OS to see if it could see the D drive...now I've got a better idea.  Boot on your ubuntu cd, run it in live cd mode, and see if THAT can see your D Drive.  Better yet, use a knoppix cd/dvd if you have one.  If not, get one!  That's the best cd/dvd to boot on to check things out and fix things...

If you MUST use a microsloth product - try windows 98.  I did that on one machine that I needed some basic winblows stuff on, it only uses about 300 megs of disk space...

---

### Post by kaginken on 2008-02-18
My fstab lists my ntfs mount as so:

/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,umask=000     0  0  

maybe try something similiar with yours - but back it up first and don't try it unless you know how to fix it if it breaks!  :D

---

