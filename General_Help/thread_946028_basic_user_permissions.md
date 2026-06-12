---
title: "basic user permissions"
date: 2008-10-12
forum: General Help
---

### Post by ohnonotme on 2008-10-12
ok ive been looking online and trying to figure this out for hours but i cant seem to get it

i want to create a user that cant view anything above their home folder and not be able to mount my usb hard drive

if nothing else they can see above their home folder but not mount my usb hard drive

thanks in advance
-kraig

---

### Post by jamesrl on 2008-10-13
When you type ls -l you get a list of permissions which are groups of three letters is a letter that is either - or d (depending on whether file or not) then three groups of "rwx", the first being the users permissions,
the second being the groups permissions, and the third being other users on the systems permissions.
```

-rw-------  1 jamesrl jamesrl  9051 2008-10-01 00:26 unison.log
-rw-r--r--  1 jamesrl jamesrl 59189 2008-10-10 04:06 Untitled.xcf
drwxr-xr-x  2 jamesrl jamesrl  4096 2008-08-20 04:24 Videos
drwxr-xr-x 19 jamesrl jamesrl  4096 2008-09-23 13:21 work

```
So if you want users besides yourself to not be able to see inside directories, simply remove the read/write/execute privileges for other users to some base directory.
E.g., running this:
```

chmod o-rwx /home/jamesrl

```
would make another account (say my_guest) not be able to get into the directory /home/jamesrl  or any of its subdirectories (even if I know what they are).  The command is chmod (change (permission) mode) adn the o-rwx has o for Other permissions, - for removing permissions, and rwx to remove rwx permissions of the directory /home/jamesrl.

Note make sure the new user doesn't have sudo privileges or they can get around that by using sudo -i.  If you want to have several people access the same files, you can create a group that has specific privileges.  Be careful with limiting read and execute privileges to files that they might need to execute or have access to for the system to work (e.g., stuff in /bin /usr /lib /var /etc).

For more info read ```
man chmod
man chown
man chgrp

```

---

### Post by jamesrl on 2008-10-13
For the second part read up on fstab and user permissions.  You probably need to list the usb drive in fstab.  For info read the manpage (man fstab and man mount) or here's a handy guide:
[http://linux4research.blogspot.com/2007/08/fstab-and-user-permission.html](http://linux4research.blogspot.com/2007/08/fstab-and-user-permission.html)
For what you want I see two basic ways of going at it, either having it mounted with a specific user/group (e.g. uid = 1001) to get your user name id and group id numbers do ```
echo $UID
echo $GROUPS
``` and specifically umask=007 (this is permissions to remove so 007 gives others no permissions).  Or just only allow root to mount in the first place (nouser), though you'll have to input a password when you want to mount it then.

---

### Post by ohnonotme on 2008-10-13
thanks i got it

---

### Post by Sam on 2008-10-13
Side note, to mark your thread solved, please follow [this guide](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6). Sadly only mods can rename a thread once it's posted, so changing the title is not sufficient.

---

