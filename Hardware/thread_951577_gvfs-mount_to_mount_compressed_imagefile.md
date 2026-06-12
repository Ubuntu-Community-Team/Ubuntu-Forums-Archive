---
title: "gvfs-mount to mount compressed imagefile?"
date: 2008-10-18
forum: Hardware
---

### Post by cov on 2008-10-18
Hi,

I'm trying to mount an image file of a partition captured by dd thru gzip.

Someone mentioned gvfs-mount might do the trick, but I'm unable to find any documentation on how to do this.

Can someone point me in the right direction or let me have the syntax for this?

The command I used was:```
sudo gvfs-mount /mnt/recover/imagefile.gz /mnt/loop1
Error mounting location: volume doesn't implement mount
Error mounting location: volume doesn't implement mount
```

I'm told that the gvfs-mount command does not need the mount point and automatically mounts in $HOME/.gvfs/

in which case:```
sudo gvfs-mount /mnt/recover/imagefile.gz
Error mounting location: volume doesn't implement mount
```

Manky thanks,

Dave

---

