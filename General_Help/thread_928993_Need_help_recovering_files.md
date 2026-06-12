---
title: "Need help recovering files"
date: 2008-09-24
forum: General Help
---

### Post by sublifer on 2008-09-24
A bit of an odd case... I had a macbook hdd crash on me but I have a recent backup.  I am running Ubuntu 8.04 on this desktop and am still quite the noob with Linux.  I need to get the files from my backup (on an external hdd) to my Ubunutu desktop so I can try to recover the email.  The problem is that when I try to get the files is says permission is denied. I've done some research and it looks like I need to modify the ownership and/or permissions but so far it hasn't worked.

I can navigate to the containing directory in the terminal 

 ls -l Mail
ls: cannot open directory Mail: Permission denied

but it will let me do it in sudo and it shows user and group to be 99

sudo ls -l Mail
total 1816
-rw-r--r-- 1 99 99   12477 2008-08-29 14:45 DefaultCounts
-rw-r--r-- 1 99 99 1453056 2008-08-29 14:09 Envelope Index
-rw-r--r-- 1 99 99  306232 2008-08-28 11:09 LSMMap2
drwx------ 1 99 99      11 2008-08-29 14:45 Mailboxes
-rw-r--r-- 1 99 99    5732 2008-08-22 13:18 MessageRules.plist
-rw-r--r-- 1 99 99    5732 2008-08-13 10:05 MessageRules.plist.backup
-rw-r--r-- 1 99 99   37239 2008-08-29 14:45 OpenedAttachments.plist
drwx------ 1 99 99       8 2008-08-29 14:45 [email]POP-jknutson@pmg.md@mail.pmg.md[/email]
drwx------ 1 99 99       5 2007-10-01 10:55 Signatures
-rw-r--r-- 1 99 99    9458 2008-08-29 14:45 SmartMailboxes.plist
-rw-r--r-- 1 99 99    9458 2008-08-29 10:39 SmartMailboxes.plist.backup

chown works similarly, it denies permission unless I run it as sudo but the real kicker is that after I run it in sudo and check it it hasn't changed anything. Still has user and group as 99 and won't let me cd into it.

sudo ls -l .
drwx------ 1 99 99  14 2008-08-29 14:45 Mail

from there I try   sudo chmod 644 Mail

but checking sudo ls -l .
drwx------ 1 99 99  14 2008-08-29 14:45 Mail

It hasn't changed anything!  Please help me, what am I doing wrong?

---

### Post by sublifer on 2008-09-24
Been fiddling with groups to try a work around... I can't name a group 99 because it has to start with a letter, I've made a group called 'test' and assigned it group id 99 and made myself a member but the group doesn't even show up in the list of groups after its made and I still can't access the files.

---

### Post by sublifer on 2008-09-24
I might have found a way to get it to work...  The group 99 thing didn't work but creating a user and assigning it to ID 99 might be the trick.  It didn't create the user in the list but it did make a home folder for the user.  I logged out of the main account and logged into the new user I created.  Checking group numbers it assigned the new user group as 1003 BUT I was able to open the Mail folder.  I am in the process of copying the files onto the desktop (because the new user has no admin priviledges) so hopefully I can get retrieve the files from the other user account.  I think part of the chown/chmod issue was that the external drive has a different format type that is read-only (not really sure how to check that) hopefully won't have issues with that now that it is on the desktop hdd.

---

### Post by spibou on 2008-09-24
If the external drive is read only how did you manage to make tha back-up in the first place? Could you do **cat /etc/mtab** and post the output? We also need to know the name of the external drive. Also can you read the files from the external drive using cat?

---

### Post by sublifer on 2008-09-25
jknutson@TestPC:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/jknutson/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jknutson 0 0
/dev/sdb1 /media/Mac hfsplus rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdb2 /media/PC vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

The external drive has two partitions, PC and Mac

 cat Mail
cat: Mail: Permission denied

It seems I've made it through... Once I copied it to the new user I created with UID 99 I was able to log in to my admin account and change ownership and permissions.  I can open the old emails with a text editor, now I just have to see if I can import them into evolution.

In the future would I be able to change that external hdd so I can have admin authority over it?  At least being able to copy the files onto my pc would be nice.

Thanks!

---

### Post by Sef on 2008-09-25
When I had a similar problem, I used [Knoppix]("http://knoppix.com") and was able to change the permissions are right clicking if I remember correctly the affected icon.

---

### Post by spibou on 2008-09-25
Based on the content of /etc/mtab what I was suspecting is not the case so I can only take a guess: the Mac filesystem was journaled which Linux can only handle in read only mode. Have a look [here](http://ubuntuforums.org/archive/index.php/t-392287.html~).

---

