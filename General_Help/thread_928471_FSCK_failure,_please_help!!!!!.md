---
title: "FSCK failure, please help!!!!!"
date: 2008-09-24
forum: General Help
---

### Post by WDYSUN on 2008-09-24
Dear All,

yesterday I started Ubuntu and it did a hd check during booting. 

At some point it started reporting incorrect  blocks in the file system. The graphic interface does not boot anymore. I ran the live version and I could recover the log  in 

var/log/fsck/checkroot

which says 


Log of fsck -C3 -a -t ext3 /dev/sda1
Mon Sep 22 09:03:21 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1: e2fsck canceled.

/dev/sda1: ********** WARNING: Filesystem still has errors **********

fsck died with exit status 36

Mon Sep 22 09:03:24 2008


what I should do to fix the problem? I am not able to boot with the graphic server.

Please help me... I have a lot of works not backuped!

Regards
Pierre

---

### Post by pdwerryhouse on 2008-09-24
There is a good chance that you can still get at all your files, even with the system in this state. Try:

```
mount -a
```

Then try to get the network up and copy the files you want to save to a different server (or maybe burn them to a DVD with growisofs). 

Once you've done that, then try to repair the filesystem:
I suspect it has an error that can't be solved with the -a option that the init script is trying to run.

Try:
```
e2fsck -y /dev/sda1
```

This will answer 'yes' to all the questions that it asks. A warning, this could make the problem worse. But unless you know enough about ext3 filesystem internals, then you probably aren't going to be able to give a serious answer to those questions anyway.

---

### Post by WDYSUN on 2008-09-24
Hi dear

i solved with 

mount -a
fsck.ext3 -y /dev/sda1

Thanks for your insights
Pierre 



> **pdwerryhouse said:**
> There is a good chance that you can still get at all your files, even with the system in this state. Try:

```
mount -a
```

Then try to get the network up and copy the files you want to save to a different server (or maybe burn them to a DVD with growisofs). 

Once you've done that, then try to repair the filesystem:
I suspect it has an error that can't be solved with the -a option that the init script is trying to run.

Try:
```
e2fsck -y /dev/sda1
```

This will answer 'yes' to all the questions that it asks. A warning, this could make the problem worse. But unless you know enough about ext3 filesystem internals, then you probably aren't going to be able to give a serious answer to those questions anyway.

---

