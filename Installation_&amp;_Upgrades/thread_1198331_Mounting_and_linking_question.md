---
title: "Mounting and linking question"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by sionseth on 2009-06-27
Hi

I like to mount a partition automaticly when Ubuntu starts.
And if possible have a map/directory in my home dir that's linked to it.
how can i make this possible?

Thanks,
SionSeth

---

### Post by swisstone198 on 2009-06-27
you can mount the partition by editing /etc/fstab and adding a line similar to

/dev/sda2      /home/(yourname)/mountpoint          ext3 defaults     0       0

if partition is ntfs add line

/dev/sda2      /home/(yourname)/mountpoint          ntfs-3g defaults     0       0

---

### Post by sisco311 on 2009-06-27
> **sionseth said:**
> Hi

I like to mount a partition automaticly when Ubuntu starts.

[thread=872197]GUI Fstab Editing with PySDM[/thread]

> **sionseth said:**
> And if possible have a map/directory in my home dir that's linked to it.
how can i make this possible?


[list=i]
[*]you can mount the partition directly in your home directory;


[*]you can mount it in /media or /mnt and create symlink to it:
```
ln -s -T /media/**mount-point** /home/**username/name**
```


[*]you can mount it in /media or /mnt and *bind* it:

create a directory in your home dir:
```
mkdir /home/**username/name**
```

and append the /etc/fstab file with something like:
```
/media/**mount-point**    /home/**username/name**    auto     bind
```    

in order to edit the file type:
```
gksu gedit /etc/fstab
```in a terminl.
[/list]

---

### Post by sionseth on 2009-06-27
Thanks sisco311,

It worked,

I used your bind method! :D

Thanks.

---

