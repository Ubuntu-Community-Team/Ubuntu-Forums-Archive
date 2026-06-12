---
title: "Mounting failed with fat on laptop"
date: 2008-08-15
forum: General Help
---

### Post by greghead on 2008-08-15
Hi everyone,

i have a problem with my FAT-Filesystem on my laptop (Desktop works perfectly)
My Ubuntu found my FAT-Partition automatically, when i try to mount it it's read only, i don't know why. Here are the infos you maybe need:

greg@lappi:~$ ls -al /media/DATA/
...
drwx------  8 greg root     16384 2007-06-02 21:16 Transfer
...

when i try to touch a file i get the following answer
root@lappi:/home/greg# touch /media/DATA_/Transfer/test.txt
touch: kann „/media/DATA_/Transfer/test.txt“ nicht berühren: Read-only file system

as normal user as well

greg@lappi:~$ touch /media/DATA_/Transfer/test.txt
touch: kann „/media/DATA_/Transfer/test.txt“ nicht berühren: Read-only file system

greg@lappi:~$ mount
...
/dev/sda8 on /media/DATA_ type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
...

when i mount the volume manually with the root user:
root@lappi:/home/greg# mount -t vfat /dev/sda8 /media/DATA/ -o rw,umask=000

i can touch my files:
greg@lappi:~$ touch /media/DATA/Transfer/test.txt
greg@lappi:~$ ls -al /media/DATA/Transfer/test.txt 
-rwxrwxrwx 1 root root 0 2008-08-15 16:15 /media/DATA/Transfer/test.txt

but when i try to mount the volume with fstab:
/dev/sda8       /media/DATA     vfat rw,defaults,users,exec,uid=1000,gid=100,umask=000,auto  0       0
i get the same 'read-only-filesystem' error ... 
i thried:
/dev/sda8       /media/DATA     vfat rw,defaults,users,umask=000,auto  0       0
as well ...

on my desktop PC all works perfectly ... only my laptop seems to have the problem.
Does anyone have any idea where the problem could be ... 

Thanks 
Greg

---

### Post by Pijits_1 on 2008-08-15
Looks like you'll have to modify your fstab (sudo vim /etc/fstab) so that the drive is rw.

If I remember correctly you should be able to just type in default under the options header for the hard drive you want in the list.

Hope this helps

---

### Post by greghead on 2008-08-16
Hi,

i entered the drive in my fstab with the rw option (see above post or the quote). Or did i write something wrong.

> **greghead said:**
> 
but when i try to mount the volume with fstab:
/dev/sda8       /media/DATA     vfat **rw**,defaults,users,exec,uid=1000,gid=100,umask=000,auto  0       0
i get the same 'read-only-filesystem' error ... 
i thried:
/dev/sda8       /media/DATA     vfat **rw**,defaults,users,umask=000,auto  0       0
as well ...


---

