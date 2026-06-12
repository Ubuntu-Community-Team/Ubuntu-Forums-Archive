---
title: "help with /bin/sh file"
date: 2008-08-31
forum: General Help
---

### Post by temo on 2008-08-31
I foolishly deleted my /bin/sh file. Now it won't boot. I'm running 8.04
After grub I get a message that states that rcS fails no "/bin/sh". How do I put that file back where it needs to be. I already know how dumb it was to send it to the trash as root. should I just reinstall? I hope not. I had it setup and working sweet. Any help would be great. Thanks-T

---

### Post by Bachstelze on 2008-08-31
If you only deleted /bin/sh, it will be recoverable. Boot a Live CD, run

```
sudo fdisk -l
```

and paste what you get.

---

### Post by InfinityCircuit on 2008-08-31
```
dmoerner@x40:/lib/modules/2.6.24-19-generic/misc$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2008-08-29 15:31 /bin/sh -> dash

```

/bin/sh is a symlink.  If you boot a rescue cd and mount the partition, then you should create a new symlink: ln -s /bin/dash /bin/sh.

---

