---
title: "Disk space has mysteriously filled up? AaH!"
date: 2010-12-19
forum: Hardware
---

### Post by OxentroT on 2010-12-19
Hello all @ Ubntuforums long time no talk!

I'm using Lenovo TP SL-510 with internal HDD(142GB)capacity with Ubuntu10.04. This problem occured sometime after an installation of Virtualbox following an installation of a WinXP virtual machine within vBox. I was soon being continually notified of only 3.3GB remaining.. I was wondering what may have caused this and if there is an existing simple solution?

Here is a dskinfo print
```

bn0@n0v0n:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            148284504 137166584   3585448  98% /
none                    958504       296    958208   1% /dev
none                    962724       104    962620   1% /dev/shm
none                    962724        92    962632   1% /var/run
none                    962724         0    962724   0% /var/lock
none                    962724         0    962724   0% /lib/init/rw
none                 148284504 137166584   3585448  98% /var/lib/ureadahead/debugfs
bn0@n0v0n:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  131G  3.5G  98% /
none                  937M  296K  936M   1% /dev
none                  941M  104K  941M   1% /dev/shm
none                  941M   92K  941M   1% /var/run
none                  941M     0  941M   0% /var/lock
none                  941M     0  941M   0% /lib/init/rw
none                  142G  131G  3.5G  98% /var/lib/ureadahead/debugfs
bn0@n0v0n:~$

```

[-o< Thank You!

---

### Post by lavinog on 2010-12-19
The Disk Usage Analyzer is handy for finding what is eating your space.

you can also use **du** in the command line to identify large folders.
```

du -hs ~/*

```

find is also good for finding large files
```

find ~/ -size +500M

```

Some common diskspace issues are ~/.thumbnails /var/log
```

du -hs ~/.thumbnails /var/log

```

you can also use bleachbit to free up space from various caches and removing unused language packs.

---

### Post by OxentroT on 2010-12-20
> lavinog 	
Re: Disk space has mysteriously filled up? AaH!
The Disk Usage Analyzer is handy for finding what is eating your space.


Thankyou very much lavindog! I find these commands very useful and I have added them to my reference file of useful commands.

I also found that I have somehow inadvertently created Three different .VDI files as I was drinking when I tried to create my VM. LOL!

Happy Holidays! and I hope that this posting later helps someone with a similar issue.

:guitar:

---

