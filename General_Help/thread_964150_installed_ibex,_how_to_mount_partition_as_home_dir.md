---
title: "installed ibex, how to mount partition as home dir?"
date: 2008-10-30
forum: General Help
---

### Post by Crypty on 2008-10-30
I have my laptop set up like this

15gb WINxp ntfs
10gb Ubuntu OS ext3
73gb Ubuntu Home ext3
2gb swap

So last time I upgraded ubuntu I just installed the new OS to that 10gb partition my settings and home docs were all there and everything was great. 
This time I installed ibex and then my home partition was not mounted automatically. I can mount it and my files are all there but its still not mounted as home. What do I have to do to fix this?

Any help is appreciated. Thanks.

---

### Post by nitrousoxide82 on 2008-10-30
Supposing your partition layout is like this
```

/dev/sda
    /dev/sda1 ntfs (Windows XP)
    /dev/sda2 ext3 (Ubuntu OS)
    /dev/sda3 ext3 (Ubuntu home)
    /dev/sda4 swap

```

you should add the corresponding line to the /etc/fstab file, by editing it as root -- of course, if it's not already there (which I assume is the case). For this example, it would look like this:
```

# Entry for /dev/sda3 mounted on /home
/dev/sda3  /home  ext3  relatime

```
Substitute /dev/sda3 with your partition device file name as appropriate. If you had to add this line (i.e. there was no line with mountpoint /home when you first opened the file), save the file and reboot. Next time you boot, the specified partition will be mounted on /home.

Hope this helps.

---

