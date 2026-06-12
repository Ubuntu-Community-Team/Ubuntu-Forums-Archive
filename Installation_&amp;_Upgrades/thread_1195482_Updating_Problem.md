---
title: "Updating Problem"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by dooob on 2009-06-23
I've just installed Ubuntu Jaunty on my laptop with 300gigs in it. When i click on update, it says i dun have enough space :confused:??

---

### Post by raymondh on 2009-06-23
> **dooob said:**
> I've just installed Ubuntu Jaunty on my laptop with 300gigs in it. When i click on update, it says i dun have enough space :confused:??

from terminal, type (and post output of)

```
df -h
```

---

### Post by dooob on 2009-06-23
```
Filesystem            Size  Used Avail Use% Mounted on 
/dev/sda6             2.3G  2.3G     0 100% / 
tmpfs                 1.8G     0  1.8G   0% 
/lib/init/rw varrun                1.8G  108K  1.8G   1% 
/var/run varlock               1.8G     0  1.8G   0% 
/var/lock udev                  1.8G  180K  1.8G   1% 
/dev tmpfs                 1.8G  460K  1.8G   1% 
/dev/shm lrm                   1.8G  2.4M  1.8G   1% 
/lib/modules/2.6.28-11-generic/volatile 
/dev/sda1             282G  2.4G  265G   1% /media/disk  
```


mmm looks like i'll have to repartition it?

---

### Post by raymondh on 2009-06-23
> **dooob said:**
> ```
Filesystem            Size  Used Avail Use% Mounted on 
/dev/sda6             2.3G  2.3G     0 100% / 
tmpfs                 1.8G     0  1.8G   0% 
/lib/init/rw varrun                1.8G  108K  1.8G   1% 
/var/run varlock               1.8G     0  1.8G   0% 
/var/lock udev                  1.8G  180K  1.8G   1% 
/dev tmpfs                 1.8G  460K  1.8G   1% 
/dev/shm lrm                   1.8G  2.4M  1.8G   1% 
/lib/modules/2.6.28-11-generic/volatile 
/dev/sda1             282G  2.4G  265G   1% /media/disk  
```


mmm looks like i'll have to repartition it?



you see it 'huh? :)  

Back up your files and have a go re-partitioning.  With so much space, I'd recommend creating a separate /home partition to keep your files and settings.  That way, any fixes and /or upgrades to root (/), you can still keep /home untouched.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Good luck and Happy Ubuntu-ing.

---

### Post by dooob on 2009-06-23
lucky for me, i just installed it. no updates no nothing. i'll just reinstall it i guess.

---

