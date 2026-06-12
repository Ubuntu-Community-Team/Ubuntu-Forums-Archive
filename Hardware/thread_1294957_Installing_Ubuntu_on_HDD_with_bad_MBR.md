---
title: "Installing Ubuntu on HDD with bad MBR"
date: 2009-10-18
forum: Hardware
---

### Post by VIkrant Pawar on 2009-10-18
Hi ,

I want to install Ubuntu , but most of the tools like SDisk and Partition Magic indicates that the MBR of my HDD is corrupt ..


I was using Ubuntu 8.10 but one fine day it just crashed and from next day i'm facing this issue .. The data is not IMP so i desided to format whole thing and start from scratch ... and still working on it.



Thanks.

---

### Post by viper250 on 2009-10-18
If your mbr is corrupted you can try using a rescue distro or use dban to wipe the drive 
dban will also brute force test the drive for errors 
download dban from distrowatch.com burn the iso to cd and boot it up. follow the instructions. if the drive has bad sectors you will get an error message that it finished early
with  the price of hard drives you can get a new one easy enough.
if dban gives you no error message your drive will have been wiped clean and you can reinstall with no problems:P

---

