---
title: "Sluggish SATA drive performance."
date: 2009-03-09
forum: Hardware
---

### Post by shankariyer on 2009-03-09
Hi,

My destop has a mix of IDE ( x2 ) and SATA ( x1 ) drives. Ubuntu and XP are installed in one of two IDE's and they all work fine.

However, the SATA drive while is alive, is acting weird. I can mount the drive from Ubuntu ( and is accessible from XP as well ) and can read/write them with reasonably big files ( say few gigs ).

However, when I use VMWare Workstation on Ubuntu to create a VM out on this big drive, it starts acting weird. The same VMWare with VM's out on the IDE's work just fine. I tested the same to create a VM out on the IDE and on SATA ( which never succeeded ). So I suspect the drive combined with its work with Ubuntu, than as an issue with VMWare.

Access to the drive becomes profoundly slow ( sometimes I suspect that the installation of access would just die ) and even nautilus takes so much of time to show the contents.

I just don't know what's going on. Can you advice as what I should be looking at to see if there is really an issue with this drive.

Thanks.

---

### Post by shankariyer on 2009-03-09
ntfs-3g seem to peek
> 
$ top

top - 18:27:12 up 1 day, 26 min,  2 users,  load average: 2.12, 2.28, 2.61
Tasks: 156 total,   2 running, 153 sleeping,   0 stopped,   1 zombie
Cpu(s): 50.5%us,  1.2%sy,  0.0%ni,  0.0%id, 48.1%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   4054968k total,  3776972k used,   277996k free,  1071300k buffers
Swap:   730916k total,    45908k used,   685008k free,  1615240k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                           
10797 root      20   0 17924 1604  680 R  100  0.0  33:50.85 mount.ntfs-3g              


---

