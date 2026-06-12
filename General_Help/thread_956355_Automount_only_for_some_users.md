---
title: "Automount only for some users"
date: 2008-10-23
forum: General Help
---

### Post by flyingstar16 on 2008-10-23
Hi all.
On my PC I have a 400GB NTFS partition that contains all my data, but this computer is shared and I don't want other people to be able to log in with their users and see my files... For now, as I am the only sudoer, I manually mount the partition at every log in, but I'm looking for a faster method..
I've tried to add "uid=1000" to my /etc/fstab, but it didn't work; I also tried to chown my /media/disk directory for disallowing any other user but me to browse it, but neither this worked :(:(
Is there any way o do this?
Thanks (and sorry for my bad English xD)
Claudio

---

### Post by vanadium on 2008-10-23
Setting you as the owner and disabling permissions for groups and others should allow you to exclude others from accessing your files. You must have done something wrong in attempting to do so.

Next to chowning your /media/disk, you also must set the permissions of the mount point to 700. If permissions stay 755 (default) others can always look at the disk.

In addition, if you would mount it under /mnt/disk instead of under /media/disk, other users would not have an icon on their desktop for a drive they should not access anyway. You can easily create an icon for yourself using gnome launchers, or, better yet, create a symlink to the partition in your home directory for fast and convenient access to it from within your home directory.

After all these measures, only users looking very hard in the file system (instead of on their desktop) will be able to go to the drive. However, they will not be able to access it.

---

### Post by flyingstar16 on 2008-10-23
> **vanadium said:**
> Setting you as the owner and disabling permissions for groups and others should allow you to exclude others from accessing your files. You must have done something wrong in attempting to do so.

Next to chowning your /media/disk, you also must set the permissions of the mount point to 700. If permissions stay 755 (default) others can always look at the disk.

In addition, if you would mount it under /mnt/disk instead of under /media/disk, other users would not have an icon on their desktop for a drive they should not access anyway. You can easily create an icon for yourself using gnome launchers, or, better yet, create a symlink to the partition in your home directory for fast and convenient access to it from within your home directory.

After all these measures, only users looking very hard in the file system (instead of on their desktop) will be able to go to the drive. However, they will not be able to access it.
I've already trie that, but I retried and found out that it doesn't work :S
Heres the list of what I've done (as root):
1) umount /media/disk
2) chown claudio:claudio /media/disk
3) checked the owner via non-root nautilus: Correct
4) mount /dev/sda1 /media/disk
5) opened /media/disk properties via nautilus: it showed "Claudio" as owner
6) tried to set "Others" permissions as "None": the same moment I clicked on "None"(its italian equivalent), Owner and Group changed to "root" and I was unable to change permissions.

So, I unmounted my disk again and clicked on "400GB Media" in nautilus: it automounted on /media/disk-1 :S:S:S

Help? ç__ç

---

### Post by vanadium on 2008-10-23
You would better post the commands you issued and their output. Otherwise there is no way to see what is wrong. Also post the output of the commands "sudo fdisk -l" and "mount".

---

### Post by flyingstar16 on 2008-10-23
> **vanadium said:**
> You would better post the commands you issued and their output. Otherwise there is no way to see what is wrong. Also post the output of the commands "sudo fdisk -l" and "mount".

Commands are the ones I posted above; those:
> 1) **umount /media/disk**
2) **chown claudio:claudio /media/disk**
3) checked the owner via non-root nautilus: Correct
4) **mount /dev/sda1 /media/disk**
5) opened /media/disk properties via nautilus: it showed "Claudio" as owner
6) tried to set "Others" permissions as "None": the same moment I clicked on "None"(its italian equivalent), Owner and Group changed to "root" and I was unable to change permissions.
Actions not higlighted were made from Nautilus. None of those commands printed output.
```
root@claudio-desktop:~# sudo fdisk -l

Disco /dev/sda: 500.1 GB, 500107862016 byte
255 testine, 63 settori/tracce, 60801 cilindri
UnitÃ* = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0xba47d83c

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       55702   447426283+   7  HPFS/NTFS
/dev/sda2           55703       60801    40957717+   5  Esteso
/dev/sda5           55703       60613    39447576   83  Linux
/dev/sda6           60614       60801     1510078+  82  Linux swap / Solaris
root@claudio-desktop:~# mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/claudio/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=claudio)
gvfs-fuse-daemon on /home/francy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=francy)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
root@claudio-desktop:~#

```

---

### Post by jerome1232 on 2008-10-23
If you trying to do these operations on the ntfs disk that would be the fail, ntfs doesn't support unix style permissions, you need to mount it with certain options to make you the owner and the only one able to view the contents. I believe the options would go like this (correct me if I'm wrong I've never set the owner on ntfs disks before)

edit: Here's some good info about umask vaules [http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

By default the first user created on an Ubuntu system is 1000. You can check yours under System->Users and Groups->Properties->Advanced
```
/dev/sdxy /mnt/disk ntfs-3g umask=077,uid=<your users uid here> 0 0
```

For a description see the ntfs-3g man page

```
 uid=value and gid=value
              Set the owner and the group of files and directories. The values
              are numerical.  The defaults are the uid and gid of the  current
              process.

       umask=value
              Set  the  bitmask of the file and directory permissions that are
              not present. The value is given in octal. The default value is 0
              which means full access to everybody.

       fmask=value
              Set  the   bitmask of the file permissions that are not present.
              The value is given in octal. The default value is 0 which  means
              full access to everybody.

       dmask=value
              Set  the   bitmask  of  the  directory  permissions that are not
              present. The value is given in octal. The  default  value  is  0
              which means full access to everybody.
```

---

### Post by flyingstar16 on 2008-10-23
> **jerome1232 said:**
> If you trying to do these operations on the ntfs disk that would be the fail, ntfs doesn't support unix style permissions, you need to mount it with certain options to make you the owner and the only one able to view the contents. I believe the options would go like this (correct me if I'm wrong I've never set the owner on ntfs disks before)

edit: Here's some good info about umask vaules [http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

By default the first user created on an Ubuntu system is 1000. You can check yours under System->Users and Groups->Properties->Advanced
```
/dev/sdxy /mnt/disk ntfs-3g umask=077,uid=<your users uid here> 0 0
```

For a description see the ntfs-3g man page

```
 uid=value and gid=value
              Set the owner and the group of files and directories. The values
              are numerical.  The defaults are the uid and gid of the  current
              process.

       umask=value
              Set  the  bitmask of the file and directory permissions that are
              not present. The value is given in octal. The default value is 0
              which means full access to everybody.

       fmask=value
              Set  the   bitmask of the file permissions that are not present.
              The value is given in octal. The default value is 0 which  means
              full access to everybody.

       dmask=value
              Set  the   bitmask  of  the  directory  permissions that are not
              present. The value is given in octal. The  default  value  is  0
              which means full access to everybody.
```

It worked ^_^
Thank you very much :)

---

