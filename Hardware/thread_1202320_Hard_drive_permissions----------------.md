---
title: "Hard drive permissions----------------"
date: 2009-07-02
forum: Hardware
---

### Post by npm1 on 2009-07-02
hello guys -----
i have a 650gb western digital hard drive which is a fat 32, i just did a clean ubuntu install and know pluged it in but the permissions are not as expected i.e. group is root and owner is me------i want to change these permissions so that can write on drive as well as read----

i've used gksu nautilus run it from ALT + F2 and terminal

---

### Post by npm1 on 2009-07-02
my fstab looks like this:

[I]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a3e95b8a-9daa-45bd-b056-399c8f0113a6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca1126e6-a476-4ac1-b0c5-620091587f3d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/I]

and on the hard when i plug it in windows it has a file called "[SIZE=6]enes.lit[/SIZE]"

---

### Post by npm1 on 2009-07-02
Help pleaseee----------------

---

### Post by hal10000 on 2009-07-02
In your fstab file there is no entry for your fat32 partition. First of all you should use the command [COLOR="Red"]sudo fstab -l[/COLOR] from a terminal window to get a list of all your drives and partitions.
On my system it looks like this:
> 
Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x8ca11739

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1        1530    12288000   27  Unbekannt
/dev/sda2   *        1531        6657    41182627+   7  HPFS/NTFS
/dev/sda3            6658       10481    30716280   83  Linux
/dev/sda4           10482       19457    72099720    5  Erweiterte
/dev/sda5           10482       10736     2048256   82  Linux Swap / Solaris
/dev/sda6           10737       13286    20482843+   b  W95 FAT32
/dev/sda7           13287       19457    49568526   83  Linux


You can see that here /dev/sda6 is the partition with fat32.

Then you should use te command [COLOR="Red"]blkid[/COLOR], you will get an output like this:
> 
/dev/sda1: UUID="F276795C76792311" LABEL="WinRE" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="190dc19a-324a-40cb-8849-522e9c7fbf32" 
/dev/sda6: UUID="48BC-CC43" TYPE="vfat"                            
/dev/sda7: UUID="0b0c06fa-52f7-40bc-9a95-f45b1837e557" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="d1f950b4-c5c6-45c1-8f99-535767e6b4c5" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb2: TYPE="swap" UUID="34e120ed-b0cd-4720-adeb-b2275957b12f"
/dev/loop0: TYPE="squashfs"
/dev/sda2: UUID="9A6C7BD26C7BA821" LABEL="SYSTEM" TYPE="ntfs"
/dev/sda3: UUID="1a8cdf2e-e6f9-4020-a751-30f83844bc82" TYPE="ext3"


Here you can see the UUID for my fat32 partition.

Next you should make an entry in your /etc/fstab file (use > sudo gedit or any editor you like). On my system it looks like this:
> 
# This is /dev/sda6
UUID=48BC-CC43  /media/sda6_fat32 vfat    utf8,umask=007,gid=46 0       1


With this entry you'll get it mounted permanently during boottime and you are able to read and write it.

Of course you have to make changes according to you own system.

I hope this can help you.

---

### Post by npm1 on 2009-07-02
sorry but it comes up as this:

on my terminal
@:~$ sudo fstab -l
[sudo] password for m: 
sudo: fstab: command not found
@:~$ sudo fstab -l
sudo: fstab: command not found
@:~$ sudo fstab -l
sudo: fstab: command not found
@:~$ 
:roll:

---

### Post by npm1 on 2009-07-02
what is the umask === number usually

			 				# This is /dev/sda6
UUID=48BC-CC43  /media/sda6_fat32 vfat    utf8,umask=007,gid=46 0       1 			 		
ok so i understand where the uuid comes from but where does the
/media/sda6_fat32 come from-is that simply the location of that drive and the name
and finally utf8, and umask =007 how do i determine these for my own pc

---

### Post by hal10000 on 2009-07-02
> 
sorry but it comes up as this:

on my terminal
@:~$ sudo fstab -l
[sudo] password for m:
sudo: fstab: command not found


I'm sorry, but i gave you the wrong command name. Instead of sudo fstab -l you have to do [COLOR="Red"]sudo fdisk -l[/COLOR].

> 
what is the umask === number usually


umask=007 means, that you (and only you) get read,write and excute permissions for the partition.

> 
but where does the
/media/sda6_fat32 come from-is that simply the location of that drive


This is the location, where my partition is mounted, i forgot to tell you, that you first have to create a directory with that name so before mounting it you should do [COLOR="Red"]sudo mkdir /media/name_of_your_partition[/COLOR] (you can choose any name you like, e.g. on my system i named it /media/sda6_fat32)

> 
and finally utf8

this is the codepage-style, on modern systems it's best to use utf8.

Here, in short the steps again:
1. sudo fdisk -l      ====> find out the name of your fat32 partition

2. blkid      ====> find out the UUID for your fat32 partition

3. sudo mkdir /media/your_partition_name

4. sudo gedit /etc/fstab and make the following entry at the end of the file:
> 
UUID=your_uuid /media/your_partition_name vfat utf8,umask=007,gid=46 0 1


Take in mind that the entry in your /etc/fstab file must be exactly in that way, including spaces, commas etc.

---

### Post by npm1 on 2009-07-02
o so the umask=007 can be kept as it is then


ok so for learning purposes:
why would i need to create a dir for my external hard drive
especially when the hard drive is plug and play (loads auto matically)
[IMG]file:///home/nazim/Desktop/Screenshot.png[/IMG]
does all my stuff in my external hard drive load directly into that created folder????
can i keep with the name already given to the hard drive??
[IMG]file:///home/nazim/Desktop/Screenshot.png[/IMG]i.e. /DESKTOP/left click the hard drive icon/PROPERTIES/ a window with the following:
[I]Name:
Type:
Contents:
Location:
...etc[/I]
what happens if i want to un mount it



thnxs in advance

---

### Post by npm1 on 2009-07-02
hi i've done exactly as u've done but i still don't hae full permissions
is there any i'm missing out:    
my fstab file nowlooks like this look like this:
[I]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a3e95b8a-9daa-45bd-b056-399c8f0113a6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca1126e6-a476-4ac1-b0c5-620091587f3d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
###########new to linux
UUID=7929-f69c /media/Elements vfat utf8,umask=007,gid=1000[/I]

---

### Post by npm1 on 2009-07-02
and know i have an empty folder named elements and the actual external hard drive that is renamed as elements_ again no permissions have been changed

---

### Post by npm1 on 2009-07-03
hello guys who suffers from the same thing-------u can also change the hard drive permissions in in windows
especially if the file system on the hard drive is fat32,,,

---

