---
title: "U3 Drive"
date: 2009-03-22
forum: Hardware
---

### Post by jazott3 on 2009-03-22
Hi,
I'm running Ubuntu 8.10 on a Dell Inspiron 6000 (although that doesn't matter here.) I use a U3 "Smart Drive" every so often and I am trying to figure out how to mount it with ubuntu. I have successfully been able to do
```


sudo mkdir /media/U3
sudo mount /dev/cdrom1 /media/U3


```

That mounts the U3 partition on the drive and executing ls gives:

```
joe@joe-laptop:/media/u3$ ls
autorun.inf  LaunchPad.zip  LaunchU3.exe
joe@joe-laptop:/media/u3$ 

```

How do I mount the data partition? Miscellaneous facts include it is a SanDisk Cruzer Micro 16GB... U3 Password is enabled, I thought that might spell disaster. LaunchU3 Doesnt open in wine, because it seems wine is incompatible with my hardware.

Thanks,
joe

---

### Post by Vignesh S on 2009-06-19
Try upgrading to Ubuntu 9.04. I have a U3 drive myself and both the U3 and the data partitions show up without any problems. But unfortunately, U3 doesn't seem to work under Ubuntu, even under Wine. So that might be the problem there.

---

