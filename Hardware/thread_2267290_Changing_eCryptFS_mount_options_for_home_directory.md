---
title: "Changing eCryptFS mount options for home directory"
date: 2015-02-28
forum: Hardware
---

### Post by CA_Warren on 2015-02-28
(Assumed because this involves mounting/unmounting fs it might go best in hardware - if there's a better forum for it let me know.)

I'm building something that requires that the system not be mounted with the nosuid mount option. After the recent Trusty upgrade it started complaining about the nosuid option being set, so I checked fstab:

```
$ cat /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
...
UUID=<snip> /               ext4    errors=remount-ro 0       1
...
```

No problematic mount options there, so check where ~ is mounted:

```
$ df

...
/home/cdot/.Private 941493860 423797712 469847956  48% /home/cdot
...
```

Then check how that's mounted:

```
$ cat /proc/mounts

...
/home/cdot/.Private /home/cdot ecryptfs rw,nosuid,nodev,relatime,ecryptfs_fnek_sig=<snip>,ecryptfs_sig=<snip>,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs 0 0
gvfsd-fuse /run/user/1001/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1001,group_id=1001 0 0
...
```

So I think what's happening is Ubuntu is mounting my home directory in a VFS with the nosuid mount option, presumably this is default for eCryptFS.  

Can anyone tell me how to edit the eCryptFS mount options for Ubuntu? I'm sure I'm missing something, but haven't been able to find documentation on it.

---

