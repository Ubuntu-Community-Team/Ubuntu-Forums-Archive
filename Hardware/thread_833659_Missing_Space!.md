---
title: "Missing Space?!"
date: 2008-06-18
forum: Hardware
---

### Post by cyrus6789 on 2008-06-18
Hey guys, I just installed Ubuntu 8.04 and it works great. My concern, is that I have 2 harddrives one of which is no worry but the other is. My secondary HD, which is SATA, has a capacity of 1 TB and yet in Gparted it says it only has 950 GB which i know could be common as some of the harddrive has to have certain data on it to keep it in check, the real problem is when I format it, and mount it in ubuntu it only shows as having 870GB, so my question is where are the 80GB going and can i get them back?

     Thanks in advance

---

### Post by SkonesMickLoud on 2008-06-18
What's the output of:

```

df -h

```

---

### Post by Dynamo_Joe on 2008-06-19
Two issues: 

1. Hard drive manufacturers express capacity in decimal whereas the OS uses binary hence 1GB does not equal 1.024GB. 

2. Disk space is normaly reserved on a Linux/Unix system so that Root/Sys Admin can clear up the mess left behind by users. 

On a data storage drive, you can remove the reserve storage space by running the following command: 
```
 sudo tune2fs -m 1 /dev/hdd1

```

replace "/dev/hdd1" with your drive identifier. 

The above commands reduces the reservse disk space from 5% (default) to 1%. 

Running the above command shouldn't affect the data (as stated in the "Wiki"). [HTML]https://help.ubuntu.com/community/InstallingANewHardDrive[/HTML]

---

