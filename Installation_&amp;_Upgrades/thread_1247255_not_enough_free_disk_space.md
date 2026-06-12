---
title: "not enough free disk space??"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by ha55an on 2009-08-22
I am trying to install updates through the update manager but it says "the upgrade needs a total of 392 M on '/' please free an addition 334 M on '/'"  I have 117 GB free space drive which is showing in file browser can I somehow use the space on that for updates?

---

### Post by ibutho on 2009-08-22
Go to Applications -> Accessories -> Terminal and enter
```
df -h
```
What is the output of that command?

---

### Post by ha55an on 2009-08-22
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   49M  98% /
tmpfs                 470M     0  470M   0% /lib/init/rw
varrun                470M  108K  470M   1% /var/run
varlock               470M     0  470M   0% /var/lock
udev                  470M  148K  470M   1% /dev
tmpfs                 470M  340K  469M   1% /dev/shm
lrm                   470M  2.4M  467M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda2             110G   28G   83G  25% /media/disk
/dev/sda1             100M   25M   76M  25% /media/System Reserved


```

---

### Post by drs305 on 2009-08-22
Looks like you recently installed Ubuntu and ended up with the infamous 2.3GB system partition. I've written two guides on this situation. The first explains what went wrong and how to reinstall it.

The second is how to expand the / partition by taking space from the Windows partition, although the procedure would be the same for a non-windows primary partition as well.

[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

In your case, if it isn't a windows partition, you will need to take some space from either sda1 or sda2. Taking it from the partition adjacent to sda5 will be easier as far as partition management is concerned if you want to do it that way.

---

### Post by ha55an on 2009-08-22
thank you

---

