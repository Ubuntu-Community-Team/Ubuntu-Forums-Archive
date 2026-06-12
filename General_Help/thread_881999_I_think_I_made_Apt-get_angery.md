---
title: "I think I made Apt-get angery"
date: 2008-08-06
forum: General Help
---

### Post by huntzire on 2008-08-06
I compiled and successfully installed a custom kernel, which i later removed with dpkg.

 Anyway After a recent update, aptget gives me the following error when I tried to install anything

 ```
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
``` 

So I tried out dpkg --configure -a to correct the issue and got this.

[```
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.26-custom
Cannot find /lib/modules/2.6.26-custom
update-initramfs: failed for /boot/initrd.img-2.6.26-custom
dpkg: subprocess post-installation script returned error exit status 1

```

I think it might have to do with the package management system not being informed the kernel was removed by dpkg because I used dpkg to remove it.

If so how to I wipe this issue out or fix it atleast.

If im totally wrong then tell and hopefully you can give me a solution please ^_^

---

### Post by huntzire on 2008-08-06
Bump

^__^

---

### Post by Thiago_M on 2008-08-15
Your custom-built kernel installation seems to have left something under /var/lib/initramfs-tools. 

try the following:

```
ls /var/lib/initramfs-tools
``` 

You should have a file for each installed kernel on your system, each one named after its corresponding kernel version. If you find a file named "2.6.26-custom", try removing it (make sure you actually removed your custom-build kernel first!).

```
sudo rm /var/lib/initramfs-tools/2.6.26-custom
```

and then

```
sudo dpkg --configure -a
```

Check if this works

---

