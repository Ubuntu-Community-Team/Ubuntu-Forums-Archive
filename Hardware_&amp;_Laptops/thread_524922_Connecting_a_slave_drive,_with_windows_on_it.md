---
title: "Connecting a slave drive, with windows on it"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by dk2852 on 2007-08-13
Hello all. 
I am pretty new to Ubuntu, in fact I don't really know much about it at all. I just installed it a few months ago on my desktop. However, I am very proficient with windows and computers in general.
Anyways, I have a laptop hard drive which has windows XP pro on it. I need to move some data from that hard drive to my Ubuntu hard drive. I have hooked up the XP hard drive to the optical drive port, because it wasn't working through the slave drive port. The computer recognizes the drive because it was in the BIOS, but I can't find it in Ubuntu, I looked in the Computer folder, and it wasn't there.
All I need to do is transfer the data onto the Ubuntu drive. Any help is appreciated, just please give it to me in the simplest possible way. Like tell me what to click and where it will be.

---

### Post by siralphred on 2007-08-13
try installing ntfs-3g [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)  look under the Easy method... or u can look in /media/   directory in ubuntu to see if u can find it...hope this helps

---

### Post by dk2852 on 2007-08-13
I installed NTS config, and I looked in the media folder, but I still cannot find it. I discovered that it is in the device manager. But there is no way to get into the files.

---

### Post by siralphred on 2007-08-13
maybe someone else can help u, u need to mount it ntfs3g before u can access it, assuming u did that, if they not huge files u can transfer with a flashdrive or dvdrw

---

### Post by shad0w_walker on 2007-08-13
Did you run ntfs-config? It gives you a nice gui tool to select where you want to mount the drive.

Hit alt-F2 and run the command 

```
gksu ntfs-config
```

Will prompt you for your password then open up a simple dialog showing all the detected NTFS drives. Good luck.

---

