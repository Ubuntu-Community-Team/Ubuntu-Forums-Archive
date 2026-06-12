---
title: "Not enough space error? Please help!"
date: 2009-08-05
forum: Hardware
---

### Post by frozendepths on 2009-08-05
When trying to download something, I receive this error message:

There is not enough room on the disk to save _____________.

Remove unnecessary files from the disk and try again, or try saving in a different location.

I just dual-booted with Ubuntu and Windows Vista.  Could you please help as soon as possible?

Thanks! :)

---

### Post by frozendepths on 2009-08-05
Could someone please reply?  :(

---

### Post by mikewhatever on 2009-08-06
Can you open Applications-->Accessories-->Terminal and post the output of the following command to verify the partitions' sizes:
df -h

---

### Post by frozendepths on 2009-08-09
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  160K  1.5G   1% /dev
tmpfs                 1.5G  228K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M  544K  480K  54% /tmp

Thanks!

---

### Post by snowpine on 2009-08-09
Well, you installed Ubuntu on a 2.3gb partition... 8gb is the recommended minimum... so your partition is full.

You'll have to boot from a Live CD and use the Gparted disk partitioner to make some more space.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by drs305 on 2009-08-09
Frozendepths, 

First, welcome to Ubuntu and the Ubuntu forums. Unfortunately, you have experienced the dreaded 2.3GB Ubuntu install!

You will either have to reinstall Ubuntu or resize your Windows partition (or another) to increase the size of the Ubuntu partition. 

This has been happening frequently lately due to some confusion in the Step 4 Partitioning section of the Ubuntu install.

I've written two guides to help, the first to reinstall without repeating what you did the first time, and the second how to resize your existing install if you prefer to do that (which may take just as long).

[URL="http://ubuntuforums.org/showthread.php?p=7658271#post7658271"] HOWTO: 2.5 GB System Partition - What Went Wrong?
[/URL]

[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

