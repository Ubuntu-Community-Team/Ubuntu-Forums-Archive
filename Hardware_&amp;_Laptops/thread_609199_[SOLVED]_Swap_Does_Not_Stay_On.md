---
title: "[SOLVED] Swap Does Not Stay On"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by rudeboyskunk on 2007-11-10
When I boot up my computer now for some reason, swap is not active!  I have to go either into GParted or commandline and do a swapon.  Any reason why this would happen, or way to fix it?

---

### Post by dwhitney67 on 2007-11-10
Is the swap mount information listed in your */etc/fstab* (file system table) file?  Normally, on startup, a system will issue a "*swapon -a*", which mounts all swap partitions specified in that file.

Here's my entry in */etc/fstab* (note, your UUID may be different):

```
UUID=52a51e04-2eb5-4ae2-b233-559b94b9a07e none swap sw 0 0
```

---

### Post by surfed on 2007-11-11
I am having the same issue, swap is defined in fstab. Not a big issue with 2G of ram i guess, do i really need swap?

---

### Post by spier on 2007-11-11
> **dwhitney67 said:**
> Is the swap mount information listed in your */etc/fstab* (file system table) file?  Normally, on startup, a system will issue a "*swapon -a*", which mounts all swap partitions specified in that file.

Here's my entry in */etc/fstab* (note, your UUID may be different):

```
UUID=52a51e04-2eb5-4ae2-b233-559b94b9a07e none swap sw 0 0
```

I resolved this same problem  by changing my /etc/fstab to point to the "hard" partition, i.e., now my fstab swap row is :
```
# /dev/hda5
# UUID=e545aa31-9b94-4c9d-af75-d7b8d8a38064 none            swap    sw              0       0
/dev/sda5       none                                    swap    sw              0       0

```

Note that, for safety, I just commented out the UUID thing.

BTW, you have to change /dev/sda5 by your swap partition. 

HTH,

---

### Post by rudeboyskunk on 2007-11-11
Cool, I'll do that.  Thanks.  I'll let you know if there's a problem.  If not, I'll mark this thread as solved.

---

