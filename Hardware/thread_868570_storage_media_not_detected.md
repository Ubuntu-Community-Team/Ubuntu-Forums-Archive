---
title: "storage media not detected"
date: 2008-07-24
forum: Hardware
---

### Post by Leonasha on 2008-07-24
Hi all, 

First, I am a newcomer to Linux, so I don't have all the lingo down, or any experience with coding.

I just recently reinstalled Hardy after screwing up my original installation by messing around with things I don't understand (LOL)

Now I find that the new OS does not detect my second hard drive, which I use only as file storage.  There is no OS in any of the 3 partitions of the drive.  It's a 200GB Maxtor diamondmax... the BIOS sees it just fine.

I'd appreciate any advice on how to draw Ubuntu's attention to this other hard drive :)

Thanks,
Leona

---

### Post by Dark_Stang on 2008-07-24
If you go to Places > Computer you don't see the other partitions? I take it that this is an internal drive.

---

### Post by Rocket2DMn on 2008-07-24
Can you please open a terminal, run these commands, then copy and paste the output back here?
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
This will give us the necessary information to see what's up.

---

### Post by Leonasha on 2008-07-24
yes it's an internal drive.

terminal says:   
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1744    14008648+  83  Linux
/dev/sdb2            1745        1826      658665    5  Extended
/dev/sdb5   ?      199851      284494   679892207   53  OnTrack DM6 Aux3
gena@gena-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=78f79a91-f850-45c3-b681-3e97587d9340 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=dbe4caed-1685-4931-904f-bd959f10c2b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
gena@gena-desktop:~$ sudo blkid
/dev/sda1: UUID="78f79a91-f850-45c3-b681-3e97587d9340" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="dbe4caed-1685-4931-904f-bd959f10c2b7" 
gena@gena-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/gena/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gena)

---

### Post by inkrypted on 2008-07-24
Just real quick you say the drive has no OS on it has it been formatted? and is there an active partition on the drive if so is it NTFS and if so have you enabled NTFS support?

---

### Post by Leonasha on 2008-07-24
yes there is such a partition ... how to I enable NTFS?

---

### Post by inkrypted on 2008-07-24
First enable the medibuntu repository unless you already have easiest way is to type sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list into a terminal and press enter. Then go to add/remove under Applications and then type NTFS in search and install the NTFS configuration tool then choose it from System Tools under Applications from there it's pretty easy a few clicks like yes enable read/write support and set a mount point.:)

---

### Post by Leonasha on 2008-07-24
command not found?

---

### Post by inkrypted on 2008-07-24
Perhaps i worded it wrong here is the official page.

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)
:)

---

### Post by Leonasha on 2008-07-24
thanks for all your help!

now the add/remove app is telling me:
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by inkrypted on 2008-07-24
Ok Try doing this one at a time pressing enter after each command better to copy and past them if you have to and if asked any questions type y and press enter again

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade

Let me know.

---

### Post by Leonasha on 2008-07-24
well I've done all that and still can't detect the drive ... will check back tomorrow.

zzzzzzzzzzzzzzzzzzzzzzzzzzz...

---

### Post by Leonasha on 2008-07-24
still no sighting of the storage drive.

on startup my computer is giving a "A:/ error, press F1 to continue" message, but boots ok after that ...

---

### Post by Leonasha on 2008-07-26
is there anything else I can try to resolve this?

---

### Post by Leonasha on 2008-07-27
hello?

---

### Post by Leonasha on 2008-07-27
OK, I have posted the output ... and tried a couple other suggestions for good measure ... still no joy.

I searched around a bit and found [this guide]("http://www.psychocats.net/ubuntu/mountlinux") for creating a mount point ... not sure if that is appropriate to this problem ... upon istalling GParted I got this message :

sudo aptitude install gparted gksu
Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.
Input/output error during read on /dev/fd0
Invalid partition table on /dev/sdb -- wrong signature 5506.


GParted does not see any of the partitions on the 2nd drive, but only sees one big 189GB unallocated space.  there are actually 3 partitions on the drive, but they were created while the drive was installed in a different computer, running XP. 

I would really rather not reformat the whole drive.

any feedback you could give me would be appreciated ... or, if I am bringing up this topic in the wrong place, could you please direct me to where I can get some answers?  

thanks,
Leona

---

### Post by cariboo on 2008-07-27
Your second hard drive is formatted using a non-standard partition and format. it is formatted to OnTrack DM6 Aux, the only place I've ever seen this in the partition type list in fdisk. It probably needs some type of wrapper to make it work in both Windows and Ubuntu. I would suggest, if you have the room, to backup the data and reformat to a format the both Windows and Ubuntu can read eg: vfat or ntfs.

I can't even find any howto's with regards to mounting this type of partition.

Jim

---

### Post by Leonasha on 2008-07-28
it was accessible for the first 3 months with Hardy ... I had to mount it each time I used it, but aside from that it worked fine.  but I guess I will go ahead and reformat if there's no other option ... hope I remembered to back everything up!  

I even plugged it in to my other machine running XP, and it didn't see the storage drive either.

ok, here goes.

---

