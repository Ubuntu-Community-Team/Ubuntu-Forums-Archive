---
title: "myfat 32 USB drive doesn't work"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by dimitry on 2007-01-10
Ok, after 2 days of trying i have to ask someone...
I just installed Ubuntu on my server, the system mounted the 200GB S-ATA but there was no way to write or delete files.. now after some search i fixed it (can write and delete but can't create folders..btw move a folder from the desktop to the hd)

my main problem:
after pluging in my 320GB WD it shows up on the desktop but ican't neighter write nor delete

> root@palast-desktop:~# mount 
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hdb5 on /media/hdb5 type ntfs (rw,nls=utf8,umask=007,gid=46)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/sda1 type ext3 (rw,noexec,nosuid,nodev)
/dev/sdb1 on /mnt/usb type vfat (rw)


ls -l on /dev/sdb1 

> root@palast-desktop:~# ls -l /dev/sdb1
brwxrwxrwx 1 palast palast 8, 17 2007-01-10 11:42 /dev/sdb1


ls -l on the mounted place

> root@palast-desktop:~# ls -l /mnt/usb
insgesamt 4086368
drwxr-xr-x 16 root root      32768 2006-01-13 15:28 Appz
-rwxr-xr-x  1 root root 4010490332 2006-11-28 15:55 dat.rar
drwxr-xr-x 13 root root      32768 2007-01-07 13:42 Games
drwxr-xr-x  5 root root      32768 2006-03-29 13:48 langames
?---------  ? ?    ?             ?                ? /mnt/usb/!filme
drwxr-xr-x 18 root root      32768 2007-01-07 13:50 Movies
drwxr-xr-x 50 root root      32768 2006-01-13 15:26 music
drwxr-xr-x  2 root root      32768 2007-01-07 15:08 Recycled
drwxr-xr-x  3 root root      32768 2007-01-07 15:08 System Volume Information
-rwxr-xr-x  1 root root       6144 2006-02-19 14:14 Thumbs.db
-rwxr-xr-x  1 root root  173668431 2006-11-28 17:49 uni.rar


trying  chown -R palast:palast /mnt/usb/  -->10000times read-only file system... 
help !!! im starting to cry every moment ](*,) ](*,) ](*,)

---

