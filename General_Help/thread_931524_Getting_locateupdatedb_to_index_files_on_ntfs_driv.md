---
title: "Getting locate/updatedb to index files on ntfs drives"
date: 2008-09-27
forum: General Help
---

### Post by Naugas on 2008-09-27
Hi!

When trying to get updatedb to index my Windows disks, I found the how-to at [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=697468](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=697468) .

But the convenient solution #2 doesn't work for me. The symlinks seems to be ignored, just as for the guy that wanted some help in the last post in the above thread.

My updatedb.conf:
```
PRUNE_BIND_MOUNTS="yes"
PRUNEPATHS="/tmp /var/spool /media"
PRUNEFS="NFS nfs nfs4 afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf rpc_pipefs"
```

---

### Post by quibbler on 2008-09-27
> **Naugas said:**
> Hi!

When trying to get updatedb to index my Windows disks, I found the how-to at [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=697468](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=697468) .

But the convenient solution #2 doesn't work for me. The symlinks seems to be ignored, just as for the guy that wanted some help in the last post in the above thread.

My updatedb.conf:
```
PRUNE_BIND_MOUNTS="yes"
PRUNEPATHS="/tmp /var/spool /media"
PRUNEFS="NFS nfs nfs4 afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf rpc_pipefs"
```
Have you add your windows folders to the index preferences?

Go to System-Preferences-Indexing Preferences
click on files check index my home directory and add
to the additional paths to watch by adding the window directories
you wish to index.

Regards quibbler

---

### Post by Naugas on 2008-09-27
Hmm, isn't that tracker an alltogether different thing than the locate database? I looked at it at it wasn't enabled at all. I guess it's a good application, but I would really have the standard locate work first before I try it.

Everything is working fine with the native filesystem, but updatedb isn't scanning through the symlinks for the mounted ntfs partitions.

Maybe it's got something to do with prune_bind_mounts or it's connected with the prunefs? I could start deleting these settings one instance at a time and see what happens, but I would rather see a working configuration...!

---

### Post by dez93_2000 on 2013-04-05
probably too late now & will never get seen but:
any idea if this is possible in xubuntu? i've looked in settings and can't find any reference to indexing preferences...
Will otherwise have a go with the updatedb.conf edits but this kinda thing always worries me!
[edit: turns out my updatedb.conf already has all those variables activated as it is!]
[edit2: mine was a recent install & it looks like my drives aren't automounting. I suspect that fixing that will mean the ntfs drives get scanned by default next time hence all may be well]

---

### Post by oldos2er on 2013-04-05
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

