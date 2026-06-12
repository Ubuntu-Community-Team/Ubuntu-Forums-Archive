---
title: "error message while upgrading"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by akrai on 2009-01-08
hi all,
i switched to ubuntu recently and am new to it. while upgrading , I am getting a particular error message 

E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version

i dont get what is wrong.
can someone help me?

---

### Post by avtolle on 2009-01-08
Please run ```
df -h
``` from the terminal and post the results here.

---

### Post by kranny on 2009-01-08
Looks like /boot is not mounted..Check it out..

---

### Post by avtolle on 2009-01-08
> **kranny said:**
> Looks like /boot is not mounted..Check it out..

I'm thinking the /boot is full, thus my first post.

---

### Post by kranny on 2009-01-08
> **avtolle said:**
> I'm thinking the /boot is full, thus my first post.

Ya may be:???:

---

### Post by akrai on 2009-01-09
> **avtolle said:**
> Please run ```
df -h
``` from the terminal and post the results here.
```

akrai@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      1.4G  748M  589M  56% /
tmpfs                 243M     0  243M   0% /lib/init/rw
varrun                243M   88K  243M   1% /var/run
varlock               243M     0  243M   0% /var/lock
udev                  243M  2.8M  241M   2% /dev
tmpfs                 243M  104K  243M   1% /dev/shm
/dev/sda5              20G   12G  8.1G  60% /host
lrm                   243M  2.0M  241M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/loop1            3.7G  1.8G  1.8G  50% /usr
```
yeah it looks like /boot is not mounted. How do I mount it? My fstab reads the following:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/usr.disk /usr            ext3    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
~

```

---

