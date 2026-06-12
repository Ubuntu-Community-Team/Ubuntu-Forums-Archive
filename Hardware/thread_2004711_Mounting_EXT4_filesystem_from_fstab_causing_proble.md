---
title: "Mounting EXT4 filesystem from fstab causing problems with APACHE"
date: 2012-06-16
forum: Hardware
---

### Post by l0uismustdie on 2012-06-16
Hello. I am running Ubuntu 12.04 with Apache. Recently I had an NTFS external drive connected which was mounted with fstab via this setting:
```

/dev/sdc2  /media/cavalry       auto    rw,user,sync    0       0

```I have several directories on this drive that are served by my web server via directory aliases in Apache's configuration. One such directory and its permissions looks like:
```

drwxrwxrwx 1 root root 4096 May 28 22:42 econ/

```However, I have made the switch to an EXT4 filesystem and am attempting to mount with the follow line in fstab:
```

/dev/sdc2  /media/cavalry       ext4    defaults        0       0

```With the same directory having permissions:
```

drwxrwxrwx 11 josh josh 4096 May 28 22:42 econ/

```The problem here is that when the EXT4 file system is mounted I am unable to access this directory from the web (receiving a 'do not have permissions error'). I am unable to see (with the obvious difference that the NTFS directory is owned by root while the EXT4 directory is owned by josh) what could possibly be causing this issue.

If anyone can offer any assistance I would be most appreciative.

---

### Post by ahallubuntu on 2012-06-16
One difference is that Linux does not handle NTFS permissions the same way it handles NTFS permissions.  In fact, I don't think Linux respects NTFS permissions much at all.  I believe everything on an NTFS partition is readable by default in Linux.

Look at the top directories of partition and make sure permissions are set correctly there, not just of the specific files.  Each subdirectory must have permissions set correctly.   So if your files are in say /media/cavalry/www/econ make sure the top level permissions are set as well as on www and econ .  You can use chmod -R to set recursive permissions.

---

### Post by l0uismustdie on 2012-06-17
RIght, thanks for your reply. The permissions set on the EXT4 system once it is mounted are the same through the whole directory tree as what I posted last time:
```

drwxrwxrwx 11 josh josh ...

```

This is true in each directory in the tree. The only difference in the NTFS mounting is that the owner and group are mounted as root. What doesn't seem to make sense is why Apache can't serve the directories that are mounted with user 'josh' and group 'josh' when they are readable and writable by everyone.

---

### Post by l0uismustdie on 2012-06-21
just a bump.

---

### Post by SeijiSensei on 2012-06-21
Never mind.

---

### Post by gesti on 2012-06-21
So let's say your folder as follows: /media/cavalry/www/econ
1. make sure that media and cavalry are both can be read by the server I personally would put it readable to everyone:
```
# chmod o+r /media && chmod o+r /media/cavalry
```
2. For the www folder change the group to the group of the apache server (www-data)
```
# chown -R :www-data /media/cavalry/www
```
3. Then make sure that the www folder can be read by the group
```
# chmod -R g+r /media/cavalry/www
```

PS. not sure but the php files might also need to be executable, then add an "x" after the "r" in the last command.

---

### Post by l0uismustdie on 2012-06-22
Thanks for your reply but I'm not sure this is the answer. If you notice in my previous posts the directories are already readable by everyone all the way up the tree. As for changing the owner, this doesn't really seem reasonable because the permissions are already set such that any user should be able to read the directories. Also, there are no php files.

---

### Post by gesti on 2012-06-22
Sorry, missed that line from your post. :)
So the only change you made is the "conversion" from NTFS to EXT4?
Have the routes to the folders not changed, they were also /media/cavalry/... when you had NTFS?
Also you didn't upgrade apache nor played a bit with apache config?
And there are no .htaccess files on the way with rules that would prevent you from looking in to dirs?

---

### Post by l0uismustdie on 2012-06-22
Yes, I have only changed the filesystem type, no changes to the directory structure have been introduced. There have been no changed to Apache, or any config files and no there are no .htaccess files in play. Everything is managed through httpd.conf.

---

### Post by l0uismustdie on 2012-07-04
Bit of a duh moment here. It was the permissions of the mount point itself that were changing and I wasn't noticing it. Marking as solved. For anyone who catches this in the future...check the WHOLE path.

---

