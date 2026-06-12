---
title: "Not enough free disk space..."
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Cagurtay on 2009-07-29
Hello,
i tried to update ubuntu via manager , it updated but when i choose to install it says i dont have any space.
In installing ubuntu i set the bar that hdd space to right end , it seems it didnt worked out.
any way to fix it without reinstall?
ty


cagurtay@Cagurtay:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR=Red]/dev/sda6             2.3G  2.1G   79M  97% /[/COLOR] [COLOR=Blue]BAH![/COLOR]
tmpfs                 994M     0  994M   0% /lib/init/rw
varrun                994M  108K  994M   1% /var/run
varlock               994M     0  994M   0% /var/lock
udev                  994M  176K  994M   1% /dev
tmpfs                 994M  112K  994M   1% /dev/shm
lrm                   994M  2.7M  991M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             1.9G  1.8G  108M  95% /media/A-DATA UFD
/dev/sdc1             932G  193G  739G  21% /media/WD Elements
/dev/sda2              47G   97M   47G   1% /media/disk

---

### Post by jcbradley on 2009-07-29
Ive experience the same problem before and there's no other way but to format and re-install the program.

---

### Post by Cagurtay on 2009-07-29
bah :(
ty anyway

---

### Post by mdmarmer on 2009-07-29
Did you install from CD?

What is the result of 

fdisk -l

in terminal as root?

You should be able to do something with gparted to fix this without a reinstall.  

Even if you can't expand your space, you can usually copy your install to a partition with more space and it should work

Where is sda2 physically located with respect to sda6?

Mike

---

### Post by Cagurtay on 2009-07-29
yeah i did in cd that i download and burned.
ill post result and what do you mean physically ,
i got a harddisk seagate baracuda st820... cant remember, i make 3 partitions in it and got external hdd's .

---

### Post by drs305 on 2009-07-29
I just wrote a guide on this problem.[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

Your's is a bit different since it's not just a windows and / partition, but the principals are the same. You can't really run Ubuntu on a 2.3GB partition. Your options are to take space from antoher partition or reinstall. The guide also links to another thread that shows why the install ended up so small and how to prevent it from happening again if you choose that option.

---

