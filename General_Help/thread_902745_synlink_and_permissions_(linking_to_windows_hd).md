---
title: "synlink and permissions (linking to windows hd)"
date: 2008-08-27
forum: General Help
---

### Post by Pyro.699 on 2008-08-27
Hello,

I currently have a dual boot going (Windows XP and Ubuntu Hardy). I have installed the [XAMPP](http://www.apachefriends.org/en/xampp-linux.html) Apache server on both my Windows and Linux shares and wanted to have the same htdocs folder for each running version. I was talking with one of my friends about this and he suggested i use the command **sudo ln -s /windows/xampp/htdocs/web /opt/lampp/htdocs** and the output of that was succussful. I was able to access the windows htdocs from the linux folder. The next problem came when i was viewing the folder in the browser, the url i typed was **[http://localhost/web](http://localhost/web)** and it returned **Error 403** which is permission denyed. I atfirst thought this was a slight overlook by myself and proceeded to go fix it. At the terminal i typed in **sudo chown cody /opt/lampp/htdocs/web** which i believe should have fixed the problem,but it didnt. I then went and typed **sudo natulius **which opend up a browser which had root access, i went to **/opt/lampp/htdocs** and went **right click->properties->permissions** and any time when i tried to change the permissions it would revert back to root being the only one that could access it. Finally i went to **/windows/xampp/htdocs** and tried to change it there and got the same results.

When i installed Linux, i mounted the windows partition as **/windows** so that is the real folder where windows is installed.

Thankyou for any help you may offer
~Cody Woolaver

---

### Post by mssever on 2008-08-27
What is the output of typing [FONT=Courier New]mount[/FONT] at a command prompt? You can't set the permissions on a Windows partition the same way as you do for a Linux partition because the permissions schemes for the two types are completely different and incompatible.

EDIT: also, things like chown don't work for Windows partitions. You should have gotten an error message when you tried to use chown.

---

### Post by Pyro.699 on 2008-08-27
Mount
> 
root@Jolteon:/windows/xampp/htdocs# mount
/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/500GB type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cody/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cody)
root@Jolteon:/windows/xampp/htdocs# 


Linux synlink
> 
root@Jolteon:/opt/lampp/htdocs# chown cody web
root@Jolteon:/opt/lampp/htdocs# 
Windows Partition
> 
root@Jolteon:/windows/xampp/htdocs# chown cody web
root@Jolteon:/windows/xampp/htdocs# 
There were no errors and it seemed to work fine, but i still get the permission revert.

---

### Post by bodhi.zazen on 2008-08-27
Windows file systems (vfat and ntfs) do not support ownership or permissions, thus chown and chmod do not work.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

You set them at the time of mounting them. This will set the permissions of ALL directories and ALL files on the windows partition the same.

Why are you using a windows partition on a Linux server ???

Copy your data to a Linux native file system.

---

### Post by Pyro.699 on 2008-08-27
Its not a server, im using linux for this because it is a much easier system to program.

After reading that document i understand that mounting the partition would mount the entire windows file system. How would i go about JUST mounting the folder C:/xampp/htdocs/web because that is the only folder i want to mount.

---

### Post by bodhi.zazen on 2008-08-27
You can not mount just a directory , you must mount the entire partition.

You can then mount --bind, but I am not sure if that works with windows partitions. I doubt you can change the permissions of the directory using mount --bind

---

### Post by mssever on 2008-08-27
> **Pyro.699 said:**
> How would i go about JUST mounting the folder C:/xampp/htdocs/web because that is the only folder i want to mount.
You can't do that. It's all or nothing.

---

### Post by Pyro.699 on 2008-08-27
But the windows partition is already mounted to /windows cant i do something with that?

heres my fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=20bf856f-9ef9-4b86-b7e0-2f6c99757095 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=645D-E6BF  /media/30GB     vfat    utf8,umask=007,gid=46 0       1
# /dev/sdc2
UUID=06F8048CF8047BE5 /media/500GB    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=C07C83027C82F308 /windows        ntfs    defaults,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


---

### Post by mssever on 2008-08-27
> **Pyro.699 said:**
> But the windows partition is already mounted to /windows cant i do something with that?
You can make a symlink that points to where you want. Your fstab is correct. What is the output of ```
ls -l /windows/some/file
```
Also, make sure your username is a member of the plugdev group.  That's set in /etc/group and you have to log out and back in for changes to take effect.

---

### Post by Pyro.699 on 2008-08-27
[quote=/etc/group]
plugdev:x:46:cody
[/quote]
> 
cody@Jolteon:~$ ls -l /windows/xampp/htdocs
total 101
-rwxrwx--- 2 root plugdev  2160 2007-12-20 22:00 apache_pb2_ani.gif
-rwxrwx--- 2 root plugdev  2414 2007-12-20 22:00 apache_pb2.gif
-rwxrwx--- 2 root plugdev  1463 2007-12-20 22:00 apache_pb2.png
-rwxrwx--- 2 root plugdev  2326 2007-12-20 22:00 apache_pb.gif
-rwxrwx--- 2 root plugdev  1385 2007-12-20 22:00 apache_pb.png
drwxrwx--- 1 root plugdev  4096 2008-08-26 21:02 contrib
-rwxrwx--- 1 root plugdev 30894 2007-12-20 22:00 favicon.ico
drwxrwx--- 1 root plugdev  4096 2008-08-26 21:02 forbidden
-rwxrwx--- 2 root plugdev   202 2007-12-20 22:01 index.html
-rwxrwx--- 1 root plugdev   267 2007-12-20 22:01 index.php
drwxrwx--- 1 root plugdev     0 2008-08-26 21:02 modperl
drwxrwx--- 1 root plugdev  4096 2008-08-26 21:02 modperlasp
drwxrwx--- 1 root plugdev  4096 2008-08-26 21:02 web
drwxrwx--- 1 root plugdev     0 2008-08-26 21:02 restricted
-rwxrwx--- 1 root plugdev 12288 2008-08-20 19:23 Thumbs.db
drwxrwx--- 1 root plugdev 20480 2008-08-26 21:02 xampp
> 
cody@Jolteon:~$ ls -l /windows/xampp/htdocs/web
total 12
drwxrwx--- 1 root plugdev 12288 2008-08-26 21:02 forums
drwxrwx--- 1 root plugdev     0 2008-08-26 21:02 uploaded
Thanks alot guys
~Cody Woolaver

---

### Post by mssever on 2008-08-27
I just realized I've been sending you down the wrong path. The problem isn't that you can't access the files, it's that Apache can't. You have two options here:

[LIST=1]
[*]Find out which user Apache is running as (for normal Ubuntu packages, it's www-data, but I have no idea what XAMPP might have done). Then add that user to the plugdev group. The consequence is that Apache will have full write access to your files, which isn't recommended (but neither is using XAMPP).
[*]Edit your fstab to set the umask of your windows partition to 002. This will give all users read access to all your Windows files.
[/LIST]

---

