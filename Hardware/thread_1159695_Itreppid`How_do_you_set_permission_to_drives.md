---
title: "Itreppid`How do you set permission to drives?"
date: 2009-05-14
forum: Hardware
---

### Post by KEE on 2009-05-14
I have a drive that some how locked up because of permissions, when I try to set this to "I" as owner it switches back to root =S need help and thank you.

---

### Post by KEE on 2009-05-14
I think its ```
$sudo -i chmod 600 some_file
```or i want to do ```
$sudo -i chmod 700 some_file
``` but i dont think im doing it right
=S

---

### Post by KEE on 2009-05-15
anyone have any ideas i could use?

---

### Post by hobo14 on 2009-05-15
Do you mean you have a whole drive mounted somewhere and can't change the permissions?

Edit /etc/fstab, put "uid=1000" and "umask=022" (or "umask=000" if you really want to)  in the options for that drive.

---

### Post by KEE on 2009-05-15
> **hobo14 said:**
> Do you mean you have a whole drive mounted somewhere and can't change the permissions?

Edit /etc/fstab, put "uid=1000" and "umask=022" (or "umask=000" if you really want to)  in the options for that drive.
yea but I cant find /etc/fstab ? 


ok this what I want to do but ```
sudo -i
```
```
chown KEE some_file
``````
chmod 700 some_file
```
but  its goes back to root with everyone can read and write, delete ...etc =S I even tried moving it and setting it but when I move it back everything changes again to root with everyone as full capabilities. please help!

---

### Post by utnubuuser on 2009-05-15
don't you have to do chown -R KEE?

and you must have a fstab

try sudo locate fstab

locate fstab
 
or locate /etc/fstab

---

### Post by KEE on 2009-05-15
> **utnubuuser said:**
> don't you have to do chown -R KEE?

and you must have a fstab

try sudo locate fstab

locate fstab
 
or locate /etc/fstab
```
/etc/fstab
/usr/include/fstab.h
/usr/lib/udev/migrate-fstab-to-uuid.sh
/usr/share/doc/mount/examples/fstab
/usr/share/doc/util-linux/examples/fstab.example2
/usr/share/man/man5/fstab.5.gz
```
but i cant find /etc/fstab in the search, i even tried nautilus but got nothing =S

---

### Post by uupreti on 2009-05-15
You can also give premission by remounting it.

Try 

sudo mount -o remount,rw /dev/drive_tobe_mounted.

---

### Post by KEE on 2009-05-15
> **uupreti said:**
> You can also give premission by remounting it.

Try 

sudo mount -o remount,rw /dev/drive_tobe_mounted. whats the -o ?

---

### Post by uupreti on 2009-05-15
> **KEE said:**
> whats the -o ?


It is switch for mount command. it's **hyphen** and small **o**. you can do **man mount** to see more switch cases. **o** is one of these for option like rw,ro,remount.....

---

### Post by KEE on 2009-05-15
> **uupreti said:**
> It is switch for mount command. it's **hyphen** and small **o**. you can do **man mount** to see more switch cases. **o** is one of these for option like rw,ro,remount.....

rw is not rewrite is it?

---

### Post by KEE on 2009-05-15
hmm ok I get this  ```
root@KEE-desktop:~# sudo mount -o remount,rw /dev/driveB
mount: can't find /dev/driveB in /etc/fstab or /etc/mtab

```

---

### Post by MadMax2 on 2009-05-15
I've just developed a problem (I haven't read the whole thread yet.. in a hurry) but the message  is
[Intrepid]

Unable to mount J and K w [CD Rom]

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.

 Possible causes include: 
-the remote application did not send a reply
-the message bus security policy blocked the reply
-the reply timeout expired
- or the network connection was broken.

---

### Post by KEE on 2009-05-15
> **MadMax2 said:**
> I've just developed a problem (I haven't read the whole thread yet.. in a hurry) but the message  is
[Intrepid]

Unable to mount J and K w [CD Rom]

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.

 Possible causes include: 
-the remote application did not send a reply
-the message bus security policy blocked the reply
-the reply timeout expired
- or the network connection was broken.eh?

---

### Post by hobo14 on 2009-05-16
Can't find /etc/fstab??  "/etc/fstab" is it's full path, that's where it is... I don't know what you mean when you say you can't find it.

Remounting will work, but only temporarily.  If you want it to be the way you like every time you boot, edit /etc/fstab, like this (don't try to "find" it first, just type this in):

sudo gedit /etc/fstab

and put in the options from my first post.

---

### Post by uupreti on 2009-05-16
> **KEE said:**
> hmm ok I get this  ```
root@KEE-desktop:~# sudo mount -o remount,rw /dev/driveB
mount: can't find /dev/driveB in /etc/fstab or /etc/mtab

```


I think you are not giving drive destination correctly. What kind of drive you want to remount with writable option??

---

### Post by KEE on 2009-05-16
> **hobo14 said:**
> Do you mean you have a whole drive mounted somewhere and can't change the permissions?

Edit /etc/fstab, put "uid=1000" and "umask=022" (or "umask=000" if you really want to)  in the options for that drive.

where do I edit this line? ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=02dc8dd9-b783-451e-a2a4-b77bcd1777fb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=71a0abdc-3315-4da3-bae4-6bf72c25c2f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by hobo14 on 2009-05-17
Is this your entire /etc/fstab?

The only things there are /, swap and your cd drive, and I assume your problem is not with any of them.  But, it also sounds like the problem you are having is with a disk that is also mounted...

Which disk is it?  

Also, see this thread useful info, esp. post #6: [http://ubuntuforums.org/showthread.php?t=1160843]("http://ubuntuforums.org/showthread.php?t=1160843")

---

### Post by KEE on 2009-05-17
> **KEE said:**
> where do I edit this line? ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=02dc8dd9-b783-451e-a2a4-b77bcd1777fb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=71a0abdc-3315-4da3-bae4-6bf72c25c2f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```yeah I know it strange but its mountable =S and I can move files in and out of the drive just its stuck as root permission. its a partition of this drive =S but  its root permission and I cant change that and its stuck as everyone can create and delete files =S not good. ```
 sudo blkid

```
 ```
/dev/sda1: UUID="BE3CE2DF3CE291A7" LABEL="DriveB" TYPE="ntfs" 
/dev/sda2: LABEL="DriveB" UUID="38EB-2B45" TYPE="vfat" 

```

---

### Post by KEE on 2009-05-19
please need help =)

---

### Post by utnubuuser on 2009-05-20
This "drive", is it a USB key/flash?  USB hd? What?

---

### Post by utnubuuser on 2009-05-21
You might also want to check package "acl" in universe repo.  It's a program for setting file/directory permissions.  
I've not used it, but the description goes something like this:> Users can provide more refined control of their files and directories by using ACLs, which maintain lists of users and groups and the rights they have to access certain files and directories. ACLs allow for much more refined access to directories, instead of just the all-or-nothing approach of owners, groups, and other.  With ACLs, only specific users could be granted write access to a file, while some others could be given only read access....
acl in synaptic; In terminal, after installation:> man acl

---

