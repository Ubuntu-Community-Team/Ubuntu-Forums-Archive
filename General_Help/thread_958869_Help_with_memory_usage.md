---
title: "Help with memory usage"
date: 2008-10-25
forum: General Help
---

### Post by djsroknrol on 2008-10-25
I've been battling this problem since I did a fresh install of Hardy on my daughters Intel P4 2.8MHz w/512RAM.

Hardy is on a 25G partition (17% used) with a 900MB swap. thing is, if I do a free -m check, I get this:

```
             total       used       free     shared    buffers     cached
Mem:           486        476         10          0          1        108
-/+ buffers/cache:        366        120
Swap:            0          0          0

```

Top doesn't show the swap either. Is there a way to get Hardy to see the swap manually? It won't even install a VM in VMware server for her school work and it's very frustrating to both of us.

Thanks for reading and hopefully someone can point me in the right direction.

---

### Post by kerry_s on 2008-10-25
looks like your swap is not active, can you post your /etc/fstab file

for now:

sudo swapon -a

---

### Post by ciscosurfer on 2008-10-25
djsroknrol, [this thread]("http://ubuntuforums.org/showthread.php?t=889917") might prove useful :-)

---

### Post by djsroknrol on 2008-10-26
Thanks guys...I must have been tired or something :)

Running through this:

```
sudo fdisk -l
cat /etc/fstab
sudo blkid
free -m
```

I got it going...I appreciate the post ciscosurfer. Now to see if I can fix VMware server for her....

EDIT: The swap problem was the problem with VMware Server for her as well

---

### Post by ciscosurfer on 2008-10-26
Glad we could help.  Please mark this thread as [SOLVED] if indeed it is now solved.  Thanks :-)

---

