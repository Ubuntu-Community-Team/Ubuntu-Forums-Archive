---
title: "I need more space"
date: 2009-11-07
forum: Hardware
---

### Post by jessica074 on 2009-11-07
I need space so I can download 9.10

i type df -h and got this:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.4G  3.3G  1.7M 100% /
varrun                247M  104K  247M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M   36K  247M   1% /dev
devshm                247M   52K  247M   1% /dev/shm
lrm                   247M  1.9M  245M   1% /lib/modules/2.6.24-24-lpia/volatile
gvfs-fuse-daemon      3.4G  3.3G  1.7M 100% /home/mom/.gvfs


the first and last ones are in 100% use.
how can i clear these? i don't want to run stuff on a separate disk, i just want to clear up this space.

---

### Post by gordintoronto on 2009-11-07
This looks like a Wubi install, Ubuntu installed within Windows.  If so, back up your data, remove Ubuntu and do the download from Windows.  Then when you install Ubuntu again, give it more space, perhaps 20 GB.

If your hard drive really is just 3.4 GB, it's not large enough.

---

