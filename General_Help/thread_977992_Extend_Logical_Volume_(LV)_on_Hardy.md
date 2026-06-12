---
title: "Extend Logical Volume (LV) on Hardy"
date: 2008-11-10
forum: General Help
---

### Post by seattleweb on 2008-11-10
Dilemma...

I have a **remote** dedicated server with a logical volume (/dev/mapper/VolGroup00-LogVolVar), in which the **ext3** /var partition needs to be extended from 5GB to 50GB. 

I've run lvextend to give the volume 50GB, but now I need to resize the filesystem. Should I:

1) Use ext2online with the filesystem mounted?
2) Forcibly unmount /var and run ext2resize?
3) Forcibly unmount /var and run resize2fs?

```

# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup00-LogVolRoot
                       10G  2.5G  7.0G  27% /
varrun                1.9G   88K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G   60K  1.9G   1% /dev
devshm                1.9G     0  1.9G   0% /dev/shm
/dev/mapper/VolGroup00-LogVolVar
                      5.0G  1.6G  3.3G  33% /var
/dev/sda1             228M   26M  191M  13% /boot

```

```
vgdisplay 
  --- Volume group ---
  VG Name               VolGroup00
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  6
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               231.66 GB
  PE Size               4.00 MB
  Total PE              59306
  Alloc PE / Size       15360 / 60.00 GB
  Free  PE / Size       43946 / 171.66 GB
  VG UUID               gjleRh-60ZU-4BTU-V8DS-gq3V-sQ1F-7S0EZi

```

```
 pvdisplay 
  --- Physical volume ---
  PV Name               /dev/md0
  VG Name               VolGroup00
  PV Size               231.67 GB / not usable 1.38 MB
  Allocatable           yes 
  PE Size (KByte)       4096
  Total PE              59306
  Free PE               43946
  Allocated PE          15360
  PV UUID               W9odVf-JZeF-LELX-sc1K-5pE3-B9EP-ms0cl7
``` 

```

# df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/mapper/VolGroup00-LogVolRoot
              ext3    10403128   2587676   7291164  27% /
varrun       tmpfs     1920192        88   1920104   1% /var/run
varlock      tmpfs     1920192         0   1920192   0% /var/lock
udev         tmpfs     1920192        60   1920132   1% /dev
devshm       tmpfs     1920192         0   1920192   0% /dev/shm
/dev/mapper/VolGroup00-LogVolVar
              ext3     5201536   1581920   3357472  33% /var
/dev/sda1     ext3      233333     26573    194713  13% /boot


```

---

### Post by seattleweb on 2008-11-10
Also, I see another option:

4) Run resize2fs /dev/... without unmounting ..(as this doc shows [http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html) )

Any ideas?

---

### Post by seattleweb on 2008-11-11
bump

---

### Post by seattleweb on 2008-11-13
Could someone with the knowledge please confirm that it is safe to run resize2fs on a mounted filesystem?

---

