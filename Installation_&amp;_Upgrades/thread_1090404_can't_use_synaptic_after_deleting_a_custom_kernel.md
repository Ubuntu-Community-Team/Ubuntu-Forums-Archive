---
title: "can't use synaptic after deleting a custom kernel"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by chanyunkwan on 2009-03-08
hi,

I compiled the newest kernel and deleted it, maybe not properly.
so, now I can't use the synaptic or apt-get to install anything.

[U]the system asked me to run this to fix the error.
sudo dpkg --configure -a
[/U]

```
kwan@kwan-laptop:~$ sudo dpkg --configure -a
[sudo] password for kwan: 
Setting up initramfs-tools (0.92bubuntu16) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28.7kwan
Cannot find /lib/modules/2.6.28.7kwan
update-initramfs: failed for /boot/initrd.img-2.6.28.7kwan
dpkg: subprocess post-installation script returned error exit status 1
kwan@kwan-laptop:~$ 


```

then I tried this solution I found on this forum(it doesn't work for me)
```
kwan@kwan-laptop:/etc/event.d$ sudo update-initramfs -k 2.6.28.7kwan -d
Cannot delete /boot/initrd.img-2.6.28.7kwan, doesn't exist.

```

I stuck at here. 

Hope to have your help!!

thank you so much.

Kwan

---

