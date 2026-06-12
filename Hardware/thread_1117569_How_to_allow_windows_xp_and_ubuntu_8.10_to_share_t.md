---
title: "How to allow windows xp and ubuntu 8.10 to share the same file"
date: 2009-04-06
forum: Hardware
---

### Post by ubantuwannabe on 2009-04-06
Hi,

the some of the disadvantage of having dual boot system is that 

1 u can only switch one os at a time.
2 files that is stored on windows xp have to be duplicated over to linux partition when required and vice versa

from [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

the third last partitioning scheme.

which is as follow 

windows partition (ntfs), ubuntu home/ - shared data (ext3), ubuntu/(ext3) , swap

resolves the issues of duplication but not the issue of switching operating system.

so having a virtual server running the guest systems windows xp

resolve the issue of switching operating system but not duplication.

Is there any solution to the above?

I'm now currently running ubuntu 8.10 a single boot system and have already set up a vmware 2.0 running windows xp.

I type the following in the terminal windows when I run the guest os on vmware server2.0,

df -h
it did not show me anyfile running any windows partition, i.e. ntfs

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             285G   11G  261G   4% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  160K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  256K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile

that is to said it is impossible to avoid duplication of files between the two os since it cannot even find one ntfs partition.

when I google around run windows i managed to find

[http://yousefourabi.com/blog/virtualization/vmware-running-native-xp-on-sata-disk](http://yousefourabi.com/blog/virtualization/vmware-running-native-xp-on-sata-disk)

step 4

"Get the files from the floopy image onto Windows, copy them onto a CD, or over a network share. I’ll leave this up to you."

it implies that i still need a windows partition first.

so wonder if the above urls, i.e. [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) and [http://yousefourabi.com/blog/virtualization/vmware-running-native-xp-on-sata-disk](http://yousefourabi.com/blog/virtualization/vmware-running-native-xp-on-sata-disk)

actually resolve my issues.

thanks!

---

### Post by Sam Lars on 2009-04-07
You will not see any VM disks through df.  They are files that the VMs see as disks.
What virtualization software are you using?  Some software lets you share a folder to the VM, so it sees it as a network share, or as a mounted drive.

---

### Post by gtr32 on 2009-04-07
> **ubantuwannabe said:**
> 
windows partition (ntfs), ubuntu home/ - shared data (ext3), ubuntu/(ext3) , swap

Windows and Linux can both read and write to NTFS so format your shared data drive as NTFS.

---

### Post by rgl2020 on 2009-04-07
If you want to keep the dual boot system, then just change the shared data partition to ntfs.  Both windows and ubuntu will be able to read/write to it.  If you already ditched the windows partition and set up a VM, then you can share the folder/drive to VM.  Search on how to share folders with your specific VM version.  There's plenty of threads in here.

---

