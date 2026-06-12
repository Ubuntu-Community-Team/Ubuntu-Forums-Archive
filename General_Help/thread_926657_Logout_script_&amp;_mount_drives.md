---
title: "Logout script &amp; mount drives"
date: 2008-09-22
forum: General Help
---

### Post by Sanix on 2008-09-22
Hi,

I wanted to mount my windows partitions automatically using the fstab file. But all tutorials say, I should use ntfs-config for NTFS partitions in order to have write support. Does this mean, it's impossible to have write support, if I want to specify my NTFS partitions in the fstab file?
Ubuntu automatically mounts these drives, but they are not visible on desktop and are linked to /media/xxx instead of /mnt/. 

Also, when I create links, I have to open the partition first in order to be able to open my link.


Another question is:
Is it possible to use a kind of a logout script? For example my own sh script to create a backup?

---

### Post by vanadium on 2008-09-22
```
But all tutorials say, I should use ntfs-config for NTFS partitions in order to have write support.
```
They are all wrong.

Since a few versions, read/write support is enabled in Ubuntu by default. Formerly, you had to install the (then experimental) ntfs-3g.

It suffices to specify "ntfs-3g" rather than "ntfs" in /etc/fstab to enable the use of the read/write driver.

---

### Post by Sanix on 2008-09-22
Thanks for your help, it works well now. The next question is, how can I tell Ubuntu not to mount on his own? Now I have the Ubuntu mount in /media/ and my mount in /mnt/.

---

### Post by vanadium on 2008-09-22
I do not understand this question. You can specify "noauto" to just announce, not mount the drive. You can specify "user" such that an ordinary user will be able to mount the drive. By providing the mount point, you determine yourself where the drive is going to be mounted. "man mount" provides info on all possible mount options.

---

### Post by Sanix on 2008-09-23
Ubuntu 8.04 mounts automatically my Windows partitions. I just does it and this is not visible in the fstab file. So my question is, where I can configure that.

---

### Post by vanadium on 2008-09-24
I don't have a windows partition myself, but my understanding is that now, an ntfs partition is mounted "on demand", i.e. when you browse to it with nautilus (or perhaps a file open dialog). Probably such a partition will initially not be available from the command line, until the moment that it has been mounted. I do not know where and how automatically mounted devices are configured. You can still opt to mount these volumes in the traditional way, i.e. through /etc/fstab, though.

---

