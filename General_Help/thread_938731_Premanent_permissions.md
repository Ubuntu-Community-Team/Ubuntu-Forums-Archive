---
title: "Premanent permissions"
date: 2008-10-05
forum: General Help
---

### Post by Moezzie on 2008-10-05
Hey there. I have a little question regarding file permissions.

Im running a webserver on my old computer(Ubuntu 8.04 + apache2), which im using for allot of web designing. Ive shared the www directory though samba so i can do my work from my main computer, which too is running Ubuntu Hardy. Every time i edit and save the changes in a file, apache isn't able to display the page because the permissions have been changed. So i have to chmod 777 after every little edit.
This only happens on Ubuntu. With my Mac its problem does not appear, and nether does it when working from a Windows machine.  

Is there any way i can set permanent 777 permissions to theres files?

---

### Post by tonybaqain on 2008-10-05
could you please paste me the result of these commands on the shell :
apache server :
[list]
[*]ls -lht /var/www/html/  , if this is your Document root
[*]ps awwwux | grep apache | head -5
[*]whoami
[*]dpkg -l | grep nfs-common
[/list]

main server
[list]
[*]using nautilus, right-click a file in the shared folder, and then write down ownership and permissions
[*]whoami
[*]groups
[*]dpkg -l | grep nfs-common
[/list]

---

### Post by Moezzie on 2008-10-05
**Server**
ls -lht /var/www/
```
drwxrwxrwx 11 allusers smbusers 4.0K 2008-09-30 20:50 nyhamn
drwxrwxrwx  5 admin1   admin1   4.0K 2008-09-26 16:09 nyhamnslage
drwxrwxrwx  2 root     root     4.0K 2008-09-14 23:32 webalizer
drwxrwxrwx  9 admin1   admin1   4.0K 2008-09-09 14:17 cal
drwxrwxrwx  5 admin1   admin1   4.0K 2008-09-03 23:05 blog
drwxrwxrwx  2 allusers smbusers 4.0K 2008-08-28 18:38 heavon
drwxrwxrwx 15 allusers smbusers 4.0K 2008-08-24 12:27 Levande6
drwxrwxrwx  5 root     root     4.0K 2008-08-20 22:54 wordpress
drwxrwxrwx  3 allusers smbusers 4.0K 2008-08-06 15:26 player
drwxrwxrwx  3 root     root     4.0K 2008-07-17 16:28 files
-rwxrwxrwx  1 root     root      460 2008-07-17 16:12 test.php
drwxrwxrwx  2 root     root     4.0K 2008-07-16 19:47 uploads
drwxrwxrwx  8 root     web3     4.0K 2008-07-13 16:44 web3
drwxrwxrwx  2 root     root     4.0K 2008-07-12 18:11 sharedip
-rwxrwxrwx  1 root     root       45 2008-07-12 17:50 index.html
-rwxrwxrwx  1 allusers smbusers 218M 2008-07-12 15:20 htdocs.tar
drwxrwxrwx  2 root     root     4.0K 2008-06-25 15:59 apache2-default

```
ps awwwux | grep apache | head -5
```
root      6118  0.0  0.9  37876 12068 ?        Ss   Sep16   0:38 /usr/sbin/apache2 -k start
www-data  6188  0.0  1.3  45680 18040 ?        S    Sep16   0:15 /usr/sbin/apache2 -k start
www-data  6191  0.0  1.2  44396 16812 ?        S    Sep16   0:08 /usr/sbin/apache2 -k start
www-data  6192  0.0  1.2  43832 16384 ?        S    Sep16   0:09 /usr/sbin/apache2 -k start
www-data  6297  0.0  1.2  43640 16084 ?        S    Sep16   0:11 /usr/sbin/apache2 -k start

```
whoami
```
admin1

```
dpkg -l | grep nfs-common
```
(This commad does not return anything)
```

**Main Computer**
using nautilus, right-click a file in the shared folder, and then write down ownership and permissions
```
The permissions of "file/folder" could not be determined.
```
whoami
```
moezzie
```
groups
```
moezzie adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin delad
```
dpkg -l | grep nfs-common
```
(This commad does not return anything here eather)
```

---

### Post by tonybaqain on 2008-10-05
I would recommend you using NFS instead of samba share. since you have both linux machines.
NFS is easier and shares are mounted on boot time.

the problem there is permissions from samba not permissions itself, samba as it is an smb/cifs share, it changes permissions as possible to the other file systems.

please see this link [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo") and after installing and mounting the shares you can control more with linux ACL like adding users to groups so they have read/write access.

anyway, if you need anything about this please don't hesitate to post here for more help.

have fun :)

---

### Post by Moezzie on 2008-10-05
I was thinking of using nfs from the beginning to, but since im running a fileserver on the same machine as the webserver i thought samba is the better alternative.

Why dont i get these problems when working from my Mac or a Windows machine?

---

