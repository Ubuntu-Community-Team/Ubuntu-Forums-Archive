---
title: "Cannot upgrade anything.. not enough HD free space??"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by Meiji on 2009-05-16
It says so, but actually I got more than enough free space..

Well, this is my problem:
I just installed Ubuntu, but when I want to make upgrades it shows me a warning message of not enough space. I wanted to Print Screen it, but can't save the file since it also says again I don't have enough free space in disk. So, I'm typing it enterly:

**"There's no enough space in disk.**

***The upgrade needs a total of 110M free space in disk "/". Please, release an aditional space in disk of at least 110M in "/". Empty your trash bin and delete temporal packages from past upgrades using "sudo apt-get clean".***

Aditionally, when I try to surf in the Internet, I open Mozilla Firefox, but it show me another message saying security upgrades aren't installed; therefore, I can't surf the Internet due to that. Also, if I try to open the Pidgin Messenger, it just stop working or close itself suddenly and I can't use it.

I have a HD of 60gb, and a slave of 120gb, partitioned in three of 40gb. All of them have at least 3gigs of free space. My computer is a bit old, though I don't think that's the problem, right?

If anyone can help me solve this problem, I'll be really really thankful! Otherwise I'll have to go back to Windows which I don't want. Since my comp is old, Windows takes light-years to load..

Thanks in advance!
Meiji

---

### Post by taurus on 2009-05-16
Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by Meiji on 2009-05-16
Thanks! This is the output:

```

S.files                 Size  Used  Disp Use% Monted on
/dev/sdb7             2.3G  2.3G     0 100% /
tmpfs                 123M     0  123M   0% /lib/init/rw
varrun                123M  104K  123M   1% /var/run
varlock               123M     0  123M   0% /var/lock
udev                  123M  164K  123M   1% /dev
tmpfs                 123M   76K  123M   1% /dev/shm
lrm                    123M  2.4M  121M   2% /lib/modules/2.6.28-11-generic/volatile
overflow             1.0M   16K 1008K   2% /tmp

```

---

### Post by taurus on 2009-05-16
> **Meiji said:**
> Thanks! This is the output:

```

S.files                 Size  Used  Disp Use% Monted on
**[COLOR="Red"]/dev/sdb7             2.3G  2.3G     0 100% /[/COLOR]**
tmpfs                 123M     0  123M   0% /lib/init/rw
varrun                123M  104K  123M   1% /var/run
varlock               123M     0  123M   0% /var/lock
udev                  123M  164K  123M   1% /dev
tmpfs                 123M   76K  123M   1% /dev/shm
lrm                    123M  2.4M  121M   2% /lib/modules/2.6.28-11-generic/volatile
overflow             1.0M   16K 1008K   2% /tmp

```

Apparently, you only have 2.3GB on a logical partition of the second harddrive as root--/.  Therefore, it will run out of space for sure if you install Ubuntu (Gnome) since that would take up about the whole disk space on /dev/sdb7.

What are the outputs of these commands?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Meiji on 2009-05-16
Thanks for your help! Here are the other outputs:

(sorry, I have the configuration in Spanish, but I'm trying to translate it =P)

**sudo fdisk -l:**
```

meiji@meiji-desktop:~$ sudo fdisk -l

Disk /dev/sda: 61.4 GB, 61475807232 bytes
255 heads, 63 sectores/pista, 7474 cilinders
Units = cilinders of 16065 * 512 = 8225280 bytes
Identifiers of disk: 0xd1a5d1a5

Disposit. Start    Begin      End      Blocks    Id  System
/dev/sda1   *           1        7474    60034873+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectores/pista, 14593 cilinders
Units = cilinders of 16065 * 512 = 8225280 bytes
Identifiers of disk: 0xb661de26

Disposit. Start    Begin        End      Blocks   Id  System
/dev/sdb1   *           1        4962    39857233+   7  HPFS/NTFS
/dev/sdb2            4964       14593    77352975    f  W95 Ext'd (LBA)
/dev/sdb5            4964       10164    41777001    7  HPFS/NTFS
/dev/sdb6           10165       14267    32957316    7  HPFS/NTFS
/dev/sdb7           14268       14571     2441848+  83  Linux
/dev/sdb8           14572       14593      176683+  82  Linux swap / Solaris

```**cat /etc/fstab:**
```

meiji@meiji-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=ca0b73d8-b31d-43df-9708-7b3b1f0a9c30 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=54fc7072-c19b-4b6c-932e-2bdbc8b54e22 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by taurus on 2009-05-16
Looks like most of your disk space is either tight up in fat32 or ntfs.  Unless you want to delete /dev/sdb6 and give that space to /dev/sdb7, there is nothing you can do about your Ubuntu since you only gave yourself a small amount of disk space when you installed it.

---

### Post by Meiji on 2009-05-16
Oh, I see... did't realise when I installed it since I'm a newbie in all this.. but ok, some technical questions before going ahead so I can understand what I'm gonna delete =P ...

- Whats '/dev/sdb6' and '/dev/sdb7' ?
- Will I delete information of some partitioned HD I have?
- Will I delete a partition?
- Finally... how do I do that? :o

Very much thanks for your help!

---

### Post by taurus on 2009-05-16
I am probably using the wrong terminology here (but what the heck) but think of your harddrive is divided into sections and each section is call a partition.  Currently, you have /dev/sdb1 as the first primary partition (you can only have 4 primary partitions to a harddrive and if you need more than 4, you need to make one of those primaries to extended partition.  Then, you can create logical partitions under that extended partition) and 4 logical partitions:  /dev/sdb5, /dev/sdb6, /dev/sdb7, & /dev/sdb8 under an extended partition--/dev/sdb2.

Your first harddrive has only one primary partition, /dev/sda1, and it is formatted as fat32/vfat filesystem.

---

### Post by Meiji on 2009-05-16
Ok... I think O.o ... lol Kind of clear actually. I really want Ubunto to work properly, so I can sacrifice /dev/sdb6. How can I delete it and assign that space to /dev/sdb7 ?

---

### Post by taurus on 2009-05-17
If you want to remove /dev/sdb6 and expand /dev/sdb7 to take up that unallocated space, you can use gparted for it.  But you must use gparted from either Ubuntu LiveCD or GParted LiveCD since you cannot resize a partition (/dev/sdb7) while you are using it.

Therefore, boot your machine with Ubuntu LiveCD.  Then go into System -> Administration -> Partition Editor to start gparted.  Now, delete /dev/sdb6 and that space would become unallocated.  Now, expand /dev/sdb7 to take up that new unallocated space.  Save the changes and reboot.

Of course, _ALWAYS_ backup your important files first before you do anything to your harddrive just in case.

---

### Post by Meiji on 2009-05-17
Ok, got it. I'll check what I have in /dev/sdb6 to see if I want to keep something and will try then to assing that space to /dev/sdb7. I'll be back if I keep getting problems.

Thank you very much taurus! Your help was much appreciated!

---

