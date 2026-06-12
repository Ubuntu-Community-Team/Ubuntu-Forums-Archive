---
title: "mount at boot drive attached to asus wireless router"
date: 2016-03-04
forum: Hardware
---

### Post by goodstuff9 on 2016-03-04
I recently installed Ubuntu 15.10.  

Previously, I had Ubuntu 15.04.  In 15.04, I had this entry in my fstab file to mount an external hard drive that is attached to my wireless router:  

//rt-ac87r-8b48/My_Book /media/rt-ac87r-8b48 cifs user,guest,uid=1000,gid=users,iocharset=utf8,sec=ntlm,file_mode=0777,dir_mode=0777,_netdev,noperm 0 0

In 15.04, this worked great - at boot, the drive mounted.  

In 15.10, with the exact same fstab file, I get no error messages, but this drive does NOT mount at boot.  I have to manually mount it (which works fine).  

I'm at a loss as to what to look at next to figure out why this will not work.  I have the cifs tools installed in 15.10 (as they were in 15.04).

---

