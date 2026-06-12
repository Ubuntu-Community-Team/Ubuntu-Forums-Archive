---
title: "bzip2 errors"
date: 2008-11-22
forum: General Help
---

### Post by anhvu2875 on 2008-11-22
i alway get this error when i try to update my Intrepid by using Terminal :(:(

```
99% [1 Packages bzip2 18604032]                                      114kB/s 0s
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://www.oss-hcm.gov.vn intrepid/universe Packages                       
  Sub-process bzip2 returned an error code (2)
Fetched 4597kB in 40s (113kB/s)                                                
W: Failed to fetch http://www.oss-hcm.gov.vn/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
anhvu2875@ubuntu:~$ 

```

THANKS !

---

### Post by taurus on 2008-11-22
Looks like there is something wrong with that site, [http://www.oss-hcm.gov.vn](http://www.oss-hcm.gov.vn).  What if you comment it out by placing a # in front of it.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```
Do you still get an error message about bzip?

---

