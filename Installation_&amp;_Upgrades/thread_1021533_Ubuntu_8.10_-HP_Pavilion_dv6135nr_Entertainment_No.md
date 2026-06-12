---
title: "Ubuntu 8.10 -HP Pavilion dv6135nr Entertainment Notebook PC"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by p4cldba on 2008-12-25
Hi,

I have this laptop . windows XP was installed previously . it crashed so I am trying to recover my data and install Ubuntu . With Ubuntu Live CD I  am able to see the hard disk but I am not able to mount the hard disk . it is failing .  so what are my options. 

Any help is appreciated.

thanks
Pk

---

### Post by eaidoido on 2008-12-25
i've seen a similar issue happen when trying to boot drives from within the live environment. however, it suggested using 'mount' with a few other flags set. did you not get any such message?

---

### Post by albinootje on 2008-12-25
> **p4cldba said:**
> Hi,

I have this laptop . windows XP was installed previously . it crashed so I am trying to recover my data and install Ubuntu . With Ubuntu Live CD I  am able to see the hard disk but I am not able to mount the hard disk . it is failing .  so what are my options. 

Can you post the error message(s) if there were any ?
And post the output of the following in a terminal:
```

sudo fdisk -l
sudo apt-get install ntfsprogs ntfs-config
sudo ntfs-config

```

---

### Post by p4cldba on 2008-12-26
Thanks Guys.

I was able to do finally with the below syntax

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

---

