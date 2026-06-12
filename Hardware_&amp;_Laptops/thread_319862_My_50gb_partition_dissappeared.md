---
title: "My 50gb partition dissappeared"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by lietkynes65 on 2006-12-16
I gave a 80gb hard drive thatwas partitioned long ago into a 30gb and 50gb sizes. Windows used to reside on the 30, but I decided to install Ubuntu over windows allowing it to format my 30gb partition. Ubuntu installed perfectly and it runs like a wonder except that my 50gb partition is gone. I checked with fdisk and downloaded QTParted but neither saw anything else in my dev/hda (there was no hda2) and my external hard drive at dev/sda. Any ideas? Is it gone?

---

### Post by taurus on 2006-12-16
What's the output of this command from a terminal then?

```
sudo fdisk -l
```

---

### Post by lietkynes65 on 2006-12-17
the output of sudo fdisk -l 


Disk /dev/hdc: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3495    28073556   83  Linux
/dev/hdc2            3496        3648     1228972+   5  Extended
/dev/hdc5            3496        3648     1228941   82  Linux swap / Solaris

---

### Post by taurus on 2006-12-17
What about

```
df -h
```

---

### Post by lietkynes65 on 2006-12-17
it looks like this, still only 30

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1              27G  2.0G   24G   8% /
varrun                252M   84K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   7% /lib/modules/2.6.17-10-generic/volatile

---

### Post by taurus on 2006-12-17
How about 

```
free
```

---

### Post by lietkynes65 on 2006-12-17
hey thanks so much for helping btw... free displays


```
           total       used       free     shared    buffers     cached
Mem:        515724     404292     111432          0      46304     157548
-/+ buffers/cache:     200440     315284
Swap:      1228932      19072    1209860

```

---

### Post by taurus on 2006-12-17
Are you sure it's a 80GB harddrive because "fdisk" only sees it as 30GB...

```
Disk /dev/hdc: 30.0 GB, 30005821440 bytes
```

Have you looked in the BIOS to see if it is 30GB or 80GB?

---

### Post by lietkynes65 on 2006-12-18
positive, i've had this laptop for 3 years and i had 40gb of music. oh well, thanks for trying

---

### Post by towsonu2003 on 2006-12-18
give this tool a try and see if it can see the 50GB partition:

[http://www.stud.uni-hannover.de/user/76201/gpart/#help](http://www.stud.uni-hannover.de/user/76201/gpart/#help)

it's in the repos: sudo apt-get install gpart - use it to check out the disk and copy-paste info that it gives. don't let it write anything to the disk...

Also, in your original post, you mention hda, but your fdisk tells us about hdc. any idea why that might be? A note- did you use a program called dd in your machine?

---

