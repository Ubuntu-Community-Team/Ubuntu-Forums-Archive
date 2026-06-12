---
title: "added 2nd drive, need help"
date: 2005-11-04
forum: General Help
---

### Post by fozzieb on 2005-11-04
hi i've added a 2nd drive, but it does not show as a drive, i can mount it under /storage but i thought it would show as a volume

any ideas?

---

### Post by Kyral on 2005-11-04
EDIT: Stupid me, you said you can mount it, so it must have a FS on it

What do you mean as a "drive"?

---

### Post by fozzieb on 2005-11-04
in the menu under Places, Computer i see my dvd, dvd rw, hda1 and my usb drive

hdb1 is not there as a physical drive

---

### Post by Kyral on 2005-11-04
Hmm, now that I think about it I don't see my 160 GB SATA like that, not that it worries me. You may want to try to change the mountpoint to something under /media or /mnt though

---

### Post by fozzieb on 2005-11-04
i mounted it under /media/storage and it shows as a physical volume now

cheers mate

---

### Post by fozzieb on 2005-11-04
one other thing, when i try to copy files to it, it says i don't have permision

how do i give myself rights?

cheers again

---

### Post by Kyral on 2005-11-04
This one I'm gonna need to see your /etc/fstab for :D

---

### Post by fozzieb on 2005-11-04
here you go

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1	/media/storage  ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

cheers

---

### Post by linbetwin on 2005-11-04
You need to mount it by editing your fstab, not by enabling it in System > Administration > Disks.

---

### Post by Kyral on 2005-11-04
It looks like he did

Hmm, try adding "users, rw" after defaults,

---

### Post by fozzieb on 2005-11-04
fstab now looks like so

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1	/media/storage  ext3    defaults,users,rw,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       

still no permissions

any ideas?

---

### Post by Kyral on 2005-11-04
Hmm (Reads through the manpage for Mount)

try putting the "owner" option in htere

---

### Post by fozzieb on 2005-11-04
will do, do i need to run anything after saving fstab or just do a reboot?

cheers for all this

---

### Post by Kyral on 2005-11-04
Unmount/Remount the drive

---

### Post by fozzieb on 2005-11-04
still no joy mate

---

### Post by landotter on 2005-11-04
With breezy just go into system--disks and you'll get a gui for dealing with this.

Then you can use Gparted to format the new HDD.

---

### Post by Kyral on 2005-11-04
hmmm.....

ext3 I hate mounting like this. Its easy for a FAT32 system because you can declare on the fstab in blunt terms.

I think its have to do with who "owns" the mountpoint itself.

Mind showing me the fstab one more time?

---

### Post by Kyral on 2005-11-04
landotter there is a problem with the way the GUI operates. It doesn't modify fstab, or so I have heard

---

### Post by fozzieb on 2005-11-04
I think its the folder /media/storage that is the issue

how do i set permissions on that?

---

### Post by Kyral on 2005-11-04
I wouldn't....it has root for a reason.

May I see your fstab one more time (Sorry to keep asking)

---

### Post by fozzieb on 2005-11-04
here you go

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1	/media/storage  ext3    defaults,owner,users,rw,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

---

### Post by Kyral on 2005-11-04
Hmm, you have free r/w access to the device on usb0 right?

Hmm.....this may sound stupid, but change "users" to "user"

---

### Post by fozzieb on 2005-11-04
i can create folders on usb

changed users to user, still no luck

is it maybe usrs?

---

### Post by Kyral on 2005-11-04
Okay, I didn't want to have to try this, but unmount the device and chmod the mountpoint over to your user, or enable EVERYONE r/w/e access on it

R = Read
W = Write
E = Execute

You are supposed to be able to mount it without doing this though....

---

### Post by fozzieb on 2005-11-04
do i do
chmod -v +rw storage

---

### Post by fozzieb on 2005-11-04
i started again, using the disk program i created a folder to mount it to and it still does not work

---

### Post by ofek on 2005-11-04
you should try "sudo chmod 777 /media/storage" that should work.

---

### Post by fozzieb on 2005-11-04
@ofek

now i get i dont have permission to write to folder

---

### Post by pickarooney on 2005-11-04
add a -R?
sudo chmod -R 777 /media/storage

---

### Post by fozzieb on 2005-11-04
got it, after re-install chmod 777 unmount then mount

it works

cheers for all the help

---

### Post by fozzieb on 2005-11-04
did a re-install and partition everything manualy

still no joy

---

