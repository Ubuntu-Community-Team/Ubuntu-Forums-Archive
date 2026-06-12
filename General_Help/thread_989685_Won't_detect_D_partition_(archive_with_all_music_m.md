---
title: "Won't detect D partition (archive with all music movies etc)"
date: 2008-11-21
forum: General Help
---

### Post by gaalaaant on 2008-11-21
Okay, so bear with me because I'm a linux noob. Intrepid Ibex is my first try at using linux.

So I have a toshiba laptop with three partitions

C: Ubuntu install
D: Data ie music,movies, pics
E: Windows XP install ( just in case I still need it)

so for some reason when I open the Computer window, it sees the partition with windows on it, but it won't show my D partition.

So what I want to know is how can I fix it not seeing it?

advice like "just store all your stuff on the C" is not needed. I don't really know what these forums are like so hopefully that was an unneeded addition :)

thanks in advance.

---

### Post by taurus on 2008-11-21
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

p.s.  In Unix, we don't call them C:, D:, E: drives.  Instead, we call them /dev/sda1, /dev/sda2, /dev/sda3, etc.

---

### Post by mdurham on 2008-11-21
> so for some reason when I open the Computer window
Which window do you refer to? If you open Nautilus (the file manager) and click on the 'Computer' icon you should see all your drives.

---

### Post by gaalaaant on 2008-11-22
daniel@Dans-Laptop:~$ sudo fdisk -l
[sudo] password for daniel: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbadfab80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sda2            1531       19456   143990595    f  W95 Ext'd (LBA)
/dev/sda5            1531        2550     8193118+  83  Linux
/dev/sda6            2551       19456   135797413+  82  Linux swap / Solaris
daniel@Dans-Laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=3c7e2e9d-0297-4b75-870b-fa74d3773b19 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=44098241-088d-428e-84e0-7f555db46c53 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
daniel@Dans-Laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             7.7G  2.2G  5.2G  31% /
tmpfs                 948M     0  948M   0% /lib/init/rw
varrun                948M  104K  948M   1% /var/run
varlock               948M     0  948M   0% /var/lock
udev                  948M  2.8M  946M   1% /dev
tmpfs                 948M  760K  948M   1% /dev/shm
lrm                   948M  2.0M  946M   1% /lib/modules/2.6.27-7-generic/volatile






thats what I got. the for the info on what you guys call them, I am sort of new at this so all info is welcome.
as to the second reply, yes when I open Nautilus and click on Computer, my d partition (/dev/sda2?)  doesn't show up. 

other than that problem I am really loving this, its awesome everything needed is preloaded, runs smooth, nice looking, its great.

Now I just want to store my stuuf on the other partition (/dev/sda2)

---

### Post by bodhi.zazen on 2008-11-22
Partition terminology is different in Linux then windows.

See :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by KeyserSoze93 on 2008-11-22
Try this:

```

sudo mkdir /media/data

cp /etc/fsab fstab_backup

sudo echo "/dev/sda2 /media/data ntfs-3g defaults,locale=en_GB.UTF-8,uid=daniel,gid=daniel 0 1" >> /etc/fsab

sudo mount /media/data

```

---

### Post by gaalaaant on 2008-11-22
Thanks I'll be sure to check out those two links. But do you have any idea why that's happening? Because when I run Windows, it sees my D partition/ /dev/sda2 and I can store files on it, but from Ubuntu, I can neither see it in Nautilus nor store anything on it.

---

### Post by taurus on 2008-11-22
You need to mount it first before you can use (or "see") it.  The easiest way is to add an entry in /etc/fstab so it would be mounted automatically each time you boot.  Then, you don't have to worry about mounting if you want to access it.

---

### Post by gaalaaant on 2008-11-22
okay I understood that I have to do something, but I don't understand what, could you spell it out for me? I don't really know how to "mount" it, is there a guide somewhere?

---

### Post by bodhi.zazen on 2008-11-22
Take a look at the links I gave you. When you install Ubuntu you can configure your drives to mount automatically. If you did not do this, you need to edit /etc/fsatb manually and the links I gave you will review this information.

---

### Post by gaalaaant on 2008-11-22
thanks man, you guys are alot politer and more helpful than other OS forums.

---

### Post by gaalaaant on 2008-11-22
Hrm, I took a look at both the guides and some links on them, and I gotta say, I really don't understand.  When I tried using the NTFS Configuration Tool it only showed one partition and only let me check the "external" check box.  I tried doing it through the terminal, but every time I got an error message somewhere along the way.  I know that I have to mount the partition, but I really do not understand how, because I tried alot of those methods and they either gave me error messages, or they did work but they didn't show the partition that I need.

---

### Post by bodhi.zazen on 2008-11-22
You make a directory and then mount the partition to it

In a terminal ;```
sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows -o uid=1000,gid=100,umask=000
```

See the fstab for examples of enteries to /etc/fstab

In a terminal ```
gksu  gedit /etc/fstab
```and add an entry at the bottom.

---

### Post by gaalaaant on 2008-11-22
I'll try it, but now the directory has dissapeared from windows. w/e i'll give it a try

---

### Post by bodhi.zazen on 2008-11-22
what partition are you trying to mount ? I see only sda1 from your output of fdisk -l. Do you have a second HD that is not showing up ?

---

### Post by gaalaaant on 2008-11-22
oh shoot, I figured out whats wrong. I am such an idiot. When I left my friend to repartition both our harddrives (he was at my house installing ubuntu and reformatting too so we decided to do it at the same time). He forgot to make a 3rd partition on my computer. He left 130 gigs as unpartitioned! sorry for bothering you guys. :( didnt mean to waste your time.

---

### Post by bodhi.zazen on 2008-11-22
> **gaalaaant said:**
> oh shoot, I figured out whats wrong. I am such an idiot. When I left my friend to repartition both our harddrives (he was at my house installing ubuntu and reformatting too so we decided to do it at the same time). He forgot to make a 3rd partition on my computer. He left 130 gigs as unpartitioned! sorry for bothering you guys. :( didnt mean to waste your time.

:lolflag: No bother, welcome to the forums.

---

### Post by blackened on 2008-11-22
> **gaalaaant said:**
> oh shoot, I figured out whats wrong. I am such an idiot. When I left my friend to repartition both our harddrives (he was at my house installing ubuntu and reformatting too so we decided to do it at the same time). He forgot to make a 3rd partition on my computer. He left 130 gigs as unpartitioned! sorry for bothering you guys. :( didnt mean to waste your time.

You're not wasting anyones time. We're here because we choose to be.

To set up a partition in the unallocated space, first:
```
sudo apt-get install gparted
```
then go to System->Administration->Partition Manager.

If you are wanting to use the partition as shared data storage for both Windows and Ubuntu, then I would suggest formatting it as FAT32 simply for ease of configuration. From there you can use the regular mount commands or add that partition to /etc/fstab as mentioned before.

Good luck and post back if you have more questions.

---

