---
title: "[SOLVED] I need help with these"
date: 2008-07-26
forum: General Help
---

### Post by velja27 on 2008-07-26
How to:
1.Auto mount a partition that is ext3 on system start up.
2.Have Root access to partition,all the time.So i can copy/paste/delete files without need to use "gksu nautilus" for that sorta stuff and so i can download files to it with Azureus and Firefox.
(gksu Firefox is not an option,tried that but i dont like the way it works,if u have some other workaround please post it)
Thanks in advance.:)

---

### Post by jamvegan on 2008-07-26
1) Add a line to /etc/fstab.  I'll give a sample line here, but you will need to use the correct device name and mount point.

```
/dev/sdb  /path/to/mountpoint   ext3   defaults  0   1
```

This will cause the file system to be mounted automatically at boot time.  If you want it to take effect immediately you can issue the command:

```
sudo mount -a
```

If you wish to see what other options you can give in /etc/fstab to control how the file system is mounted, see

```
man fstab
```

which will direct you to other man pages for further information, if needed.

2) You say "Have Root access", but I'm not sure exactly what you mean.  If you want your user (not root) to be the owner of the file system and have all rights to read, write and execute within it, then you should change the owner.  While the file system is mounted, issue the following command, using your username and the actual mountpoint:

```
sudo chown -R username: /path/to/mountpoint
```

(The -R changes the ownership on /path/to/mountpoint, and all files and directories beneath it.  If you only want to change the ownership of the mountpoint, and not everything contained within the mounted filesystem, omit the -R.)

If you want the file system to be owned by root, but want your user to have full access, then you need to change the permissions, and possibly the group.  Changing permissions has many security and functional implications.  If that's the route you wish to follow, please provide more information on exactly what you want:

Who should be able to access the file system, and what should they be able to do?  If you are the only user on the system, then the ownership change option is probably what you want.

Hope this helps!

---

### Post by velja27 on 2008-07-27
Thanks,i will try that out... when i wake up :D.
I hope i will make this work.
(I dont know why do i need to mount something at start up,cause i rarely
restart... who knows).

---

