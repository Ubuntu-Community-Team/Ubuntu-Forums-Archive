---
title: "My /boot partition is full - What can I delete?"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by botfish on 2009-05-05
During an update of my Ubuntu 8.04 system I received the following error. I think is is because my /boot partition is full. What files can I safely delete from my boot partition? (see ls of /boot below).

```

E: linux-ubuntu-modules-2.6.24-24-generic: subprocess post-installation script returned error exit status 1
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

```

```

Setting up linux-ubuntu-modules-2.6.24-24-generic (2.6.24-24.39) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-24-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd-2.6.24-24-generic
dpkg: error processing linux-ubuntu-modulea-2.6.24-24-generic (--configure):
 subprocess post-installation script returned exit status 1
...

```

df shows that my /boot partition is full

```

~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1                93307     92288         0 100% /boot

```

A listing of my /boot partition:

```

/boot$ ls -1
abi-2.6.24-19-generic
abi-2.6.24-21-generic
abi-2.6.24-22-generic
abi-2.6.24-23-generic
abi-2.6.24-24-generic
config-2.6.24-19-generic
config-2.6.24-21-generic
config-2.6.24-22-generic
config-2.6.24-23-generic
config-2.6.24-24-generic
grub
initrd.img-2.6.24-19-generic
initrd.img-2.6.24-19-generic.bak
initrd.img-2.6.24-21-generic
initrd.img-2.6.24-21-generic.bak
initrd.img-2.6.24-22-generic
initrd.img-2.6.24-22-generic.bak
initrd.img-2.6.24-23-generic
initrd.img-2.6.24-23-generic.bak
initrd.img-2.6.24-24-generic
lost+found
memtest86+.bin
System.map-2.6.24-19-generic
System.map-2.6.24-21-generic
System.map-2.6.24-22-generic
System.map-2.6.24-23-generic
System.map-2.6.24-24-generic
vmlinuz-2.6.24-19-generic
vmlinuz-2.6.24-21-generic
vmlinuz-2.6.24-22-generic
vmlinuz-2.6.24-23-generic
vmlinuz-2.6.24-24-generic

```

Thanks for any help.

---

### Post by Partyboi2 on 2009-05-05
Hi, search through synaptic for 'linux-image' and remove the ones you no longer need, I suggest keeping your current as well as another one.

---

### Post by botfish on 2009-05-05
Thanks Partyboi2

I removed the following and now have plenty of room on my /boot partition.
2.6.24-19
2.6.24-21
2.6.24-22

I do notice that the file /boot/initrd.img-2.6.24-19-generic remains. Shouldn't synaptic have deleted it? Can I delete it manually?


```

/boot$ ls -1
abi-2.6.24-23-generic
abi-2.6.24-24-generic
config-2.6.24-23-generic
config-2.6.24-24-generic
grub
initrd.img-2.6.24-19-generic
initrd.img-2.6.24-23-generic
initrd.img-2.6.24-23-generic.bak
initrd.img-2.6.24-24-generic
initrd.img-2.6.24-24-generic.bak
lost+found
memtest86+.bin
System.map-2.6.24-23-generic
System.map-2.6.24-24-generic
vmlinuz-2.6.24-23-generic
vmlinuz-2.6.24-24-generic

```

---

### Post by StuartN on 2009-05-05
Run "apt-get clean" to remove downloaded installation packages. Take a look at /var/cache/apt/archives/ to see how much space is currently being used by the installers for packages you have downloaded.

---

### Post by benoy4007 on 2009-05-05
> **Partyboi2 said:**
> Hi, search through synaptic for 'linux-image' and remove the ones you no longer need, I suggest keeping your current as well as another one.

Keep only last used , and then after new insalled will become your current.

---

