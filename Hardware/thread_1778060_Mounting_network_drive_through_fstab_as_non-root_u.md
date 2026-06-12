---
title: "Mounting network drive through fstab as non-root user"
date: 2011-06-08
forum: Hardware
---

### Post by JOZeldenrust on 2011-06-08
Hey everyone,

I'm trying to set up a network disk, and I've run into a bit of a puzzle. I can mount the disk through fstab, but it becomes property of root, so I have no writing access to it from my normal users account.

This it the line in fstab that mounts the network disk:

//192.168.1.102/openshare/ /media/openshare cifs 0 0

What should it be to have it mount the disk as property of another user?

Thanks for your help guys!

---

### Post by Morbius1 on 2011-06-08
Mounting the remote share in fstab almost looks like an NTFS mount of a local partition:

Take possessions of the mounted share:
>  //192.168.1.102/openshare/ /media/openshare cifs [COLOR=Blue]uid=1000[/COLOR] 0 0uid=1000 should be you. To make sure run the following command:
```
id
```

---

### Post by JOZeldenrust on 2011-06-08
> **Morbius1 said:**
> Mounting the remote share in fstab almost looks like an NTFS mount of a local partition:

Take possessions of the mounted share:
uid=1000 should be you. To make sure run the following command:
```
id
```

That did the trick. Thanks!

---

