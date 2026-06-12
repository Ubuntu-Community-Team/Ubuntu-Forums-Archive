---
title: "sharing an hd with windows"
date: 2013-09-05
forum: Hardware
---

### Post by manni2 on 2013-09-05
Hi

I'm sure there's lots of answers out there for this, but I'm stumped on searches.

My setup is: Windows8/Ubuntu installed on a (small) SSD. Since the SSD is small, I put most of my data files on a big disk, mounted as follows:

@:/data/unix/$ cat /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0
UUID=402A4D112A4D04FE    /data    ntfs-3g    defaults,windows_names,local=en_GB.UTF-8    0    0

I put all of my unix-related stuff in /data/unix. However no matter what I do I can't seem to change ownership of files in this folder from root. This plays havoc with some of the apps I'm running:

@:/data/unix$ ls -la
total 12
drwxrwxrwx 1 root root  352 Sep  5 19:08 .
drwxrwxrwx 1 root root 4096 Sep  5 19:14 ..
drwxrwxrwx 1 root root 4096 Aug 17 18:34 installations



@mp1:/data/unix$ sudo chown manni installations
@mp1:/data/unix$ ls -la
total 12
drwxrwxrwx 1 root root  352 Sep  5 19:08 .
drwxrwxrwx 1 root root 4096 Sep  5 19:14 ..
drwxrwxrwx 1 root root 4096 Aug 17 18:34 installations


Arrrg. Any help much appreciated.

Thanks in advance.

---

### Post by TheFu on 2013-09-05
Use the CIFS driver, not the older ntfs-3g stuff.
**man mount.cifs** for more information.

---

### Post by oldfred on 2013-09-05
NTFS does not support ownership nor permissions. If you have applications that need that then you may need a data partition that is Linux formatted.

Is this a wubi install?

I thought CIFS was for network mounting not local?

---

### Post by TheFu on 2013-09-05
> **oldfred said:**
> I thought CIFS was for network mounting not local?

**[COLOR="#FF0000"]You are completely correct!  My mistake.[/COLOR]** I tested it here.
I used a ```
sudo mount -t ntfs /dev/sdi4 /mnt/4
``` to get it mounted after the **-t cifs** failed.

The /etc/mtab ended up with this inside: 
```
/dev/sdi4 /mnt/4 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
```
and this
```
/sbin/mount.ntfs /dev/sdi4 /mnt/4 -o rw
``` is in the process table.

It is the ntfs-3g driver being used.

---

