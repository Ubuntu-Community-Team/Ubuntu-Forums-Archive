---
title: "Change Owner?"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by FiskFisk33 on 2007-12-30
I have two harddrives, one 160gig and one 500gig. i installed ubuntu on the 160 gig one.
I want my home folder to be in the 500 gig one though, so i changed that in "users and groups".
Now, when i log in, it says that the users home folder has to be owned by the user. i checked, and the whole drive is owned by root. How do i change this?

---

### Post by Mze on 2007-12-30
Check this [thread]("http://ubuntuforums.org/showthread.php?t=250104") out

/home is owned by root by default;

however subfolders under home are owned by the individual user with read/write permissions and access to files by group and others

You can run this command: > gksudo nautilus  this allows root access to folders and you can change permissions

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=287043") too

---

### Post by FiskFisk33 on 2007-12-30
I tried everything in those threads, and i tried that command you gave me, no luck.

When i use the command you gave me, and tried to change something (owner, permissions) and select one from the drop down menu, it just gets changed back automatically. :mad:

---

### Post by FiskFisk33 on 2007-12-30
(sry for double post)
It seems like i cant change the permissions on that harddrive at all.

---

### Post by nick_h on 2007-12-30
What filesystem is it using?  What is the output from:
```
cat /etc/fstab
```
?

---

### Post by FiskFisk33 on 2007-12-30
Its using ntfs (formatted on a windows machine)

output of ```
cat /etc/fstab
``` is
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                       0  0  
# /dev/sda1
UUID=a1b92cdb-694a-459b-a08a-64ced3ab7e49  /                ext3         defaults,errors=remount-ro     0  1  
# /dev/sda5
UUID=7a8ff8e6-2969-4491-b4e8-15d412b6acff  none             swap         sw                             0  0  
/dev/hda                                   /media/cdrom0    udf,iso9660  user,noauto,exec               0  0  
#Added by diskmounter utility
/dev/sdb1                                  /media/Dokument  ntfs         defaults                       0  0  
/dev/sdc1                                  /media/Halvdan   ntfs         ro,user,fmask=0111,dmask=0000  0  0  
```


(its the sdb1 disk and its a Samsung Spinpoint)

---

### Post by murmel on 2007-12-30
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8804eeea-8fc0-43b5-83fa-189afa5b2641 /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
# /dev/sdb1
UUID=227de26b-6748-45a2-b6ac-cfbe3080496d /home           ext3    defaults
```
That's how it looks on my server.

---

### Post by Yellow Pasque on 2007-12-30
> /dev/sdb1 /media/Dokument ntfs defaults 0 0 

Using "defaults" means an ordinary user can't mount the drive. Try changing defaults to user,exec,auto

---

### Post by FiskFisk33 on 2007-12-31
Nope, didnt work.

this is starting to annoy the crap out of me :/

---

### Post by nick_h on 2007-12-31
NTFS doesn't support file permissions like ext2/3 filesystems do.  By default, files in NTFS filesystems are owned by root and only readable by root.  To change this you need to specify the uid, gid and umask options in the fstab entry for this filesystem.

Try adding:
```
umask=007,gid=46
```

This will put all files on the filesystem in the plugdev group with group permissions of read, write and execute.  Your users should be in the plugdev group by default.

For further details type:
```
man mount
```
and scroll down to the NTFS specific options.

---

### Post by FiskFisk33 on 2008-01-01
but can i change the owner?

---

### Post by nick_h on 2008-01-01
> but can i change the owner?
Yes, just add the option:
```
uid=1000
```
Change the id from 1000 to the id of the user you want to own the files.
Look in the /etc/passwd file to find the userid or use the following:
```
grep `whoami` /etc/passwd | cut -d : -f 3
```

---

### Post by FiskFisk33 on 2008-01-01
Yayy, it worked :D, im the owner! :DD
let's see what happens when i put it as my home :)

---

### Post by FiskFisk33 on 2008-01-01
hmm, it still wants the "644" rights, what do i type in?

---

### Post by nick_h on 2008-01-01
umask=133

---

### Post by FiskFisk33 on 2008-01-01
when i added that it said that the path didnt exist, i had to log in in safe mode and change it back :(

---

### Post by nick_h on 2008-01-01
Paste your fstab and I'll look at it for you.

---

### Post by FiskFisk33 on 2008-01-01
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=72c9d3b8-b473-4469-9be3-fe4e449ed7c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7a8ff8e6-2969-4491-b4e8-15d412b6acff none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sdb1                                  /home/jonathan/Mina_Dokument  ntfs         umask=133,uid=1000                       0  2
```

actually right now its:
```
/dev/sdb1                                  /home/jonathan/Mina_Dokument  ntfs         uid=1000                       0  2
```

---

### Post by nick_h on 2008-01-01
That looks OK.  Did it work before you added the umask=133 ?

Try it with umask=022 you don't need to reboot just unmount it with:
```
sudo umount /dev/sdb1
```
and when you have made the change remount again with:
```
sudo mount /dev/sdb1
```

---

### Post by FiskFisk33 on 2008-01-01
OMGOMGOMGOMGOMGOGMOGMOMGMOGMOG IT WORKED!!!!

Ive moved my home folder there, and NO ERRORS :D 

YOU ROCK, THANX

big thanx to everyone else who helped too :D

---

### Post by nick_h on 2008-01-01
I'm glad you got it working.  I think that the umask=133 caused problems because you would have removed all search permissions for the directories as well as execute permissions for the files.

---

