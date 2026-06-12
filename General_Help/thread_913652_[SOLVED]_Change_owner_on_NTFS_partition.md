---
title: "[SOLVED] Change owner on NTFS partition"
date: 2008-09-08
forum: General Help
---

### Post by gdboytyler on 2008-09-08
I want to change the owner on my NTFS partition.  It's a shared PC and I don't want anyone else using the PC to access the folder on the Windows partition.

Here's the line from the FSTAB file.

"# /dev/sdb1  LABEL="200GB_DATA" TYPE="ntfs" 
UUID=849C00739C006252 /media/200GB_DATA ntfs relatime        0       2"

I tried changing it to:
"# /dev/sdb1  LABEL="200GB_DATA" TYPE="ntfs" 
UUID=849C00739C006252 /media/200GB_DATA ntfs [COLOR="Red"]user=gdboytyler[/COLOR] relatime        0       2"

But when I run "sudo mount -a", I get an error that the line is bad.  What am I doing wrong?

Thanks

---

### Post by ryanhaigh on 2008-09-08
I can't be sure that this will work because I cannot test it at the moment but you could try unmounting the disk, changing the permissions on the mountpoint and then remounting.

```

sudo umount /media/200GB_DATA
sudo chown gdboytyleer:gdboytyleer /media/200GB_DATA 
chmod a-rwx /media/200GB_DATA
chmod u+rwx /media/200GB_DATA
sudo mount -a

```

---

### Post by deanjm1963 on 2008-09-08
I'm pretty sure you can't change permissions on NTFS partitions as NTFS doesn't support permissions like linux file systems do ...

Don't quote me on it!

---

### Post by prshah on 2008-09-08
> **gdboytyler said:**
> 
"# /dev/sdb1  LABEL="200GB_DATA" TYPE="ntfs" 
UUID=849C00739C006252 /media/200GB_DATA ntfs [COLOR="Red"]user=gdboytyler[/COLOR] relatime        0       2"


The list of options is comma separated; change it to 
```

# /dev/sdb1  LABEL="200GB_DATA" TYPE="ntfs" 
UUID=849C00739C006252 /media/200GB_DATA ntfs [COLOR="Red"]user=gdboytyler,relatime[/COLOR]        0       2

```

---

### Post by gdboytyler on 2008-09-08
> **prshah said:**
> The list of options is comma separated; change it to 
```

# /dev/sdb1  LABEL="200GB_DATA" TYPE="ntfs" 
UUID=849C00739C006252 /media/200GB_DATA ntfs [COLOR="Red"]user=gdboytyler,relatime[/COLOR]        0       2

```

That code got rid of the error message I was getting, but the owner didn't change.

This code got the owner changed (I needed a reboot, not just umount/mount to get the changes recogized):
```
# /dev/sdb1  LABEL="200GB_DATA" TYPE="ntfs" 
UUID=849C00739C006252 /media/200GB_DATA ntfs [COLOR="Red"]defaults,umask=007,uid=1000,gid=1000[/COLOR],relatime        0       2
```

It didn't work exactly as I thought it would.  It locked out all other users from the partition, but I couldn't selectively let other users to access certain folders, like in an EXT3 partition.  But good enough.

See this thread for details:

[http://ubuntuforums.org/showthread.php?t=899264&highlight=change+permission+ntfs]("http://ubuntuforums.org/showthread.php?t=899264&highlight=change+permission+ntfs")

---

