---
title: "Errors when updating through Update Manager"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by jono30 on 2008-12-04
For the last month or so, whenever I use update manager, I always get the following window at the end of the update process:
```

An error occured
The following details are provided:

E: linux-image-2.6.24-21-generic: subprocess post-installation script returned error exit status 2
E: linux-image-2.6.24-22-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-ubuntu-modules-2.6.24-22-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-22-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

```I'm not familiar with Ubuntu's Terminal commands, so if anyone can take me through the precise steps to fix this, I would be very grateful. Thanks.

---

### Post by ibutho on 2008-12-04
Do you get any errors when you run "sudo apt-get update" and "sudo apt-get upgrade" in a terminal? If so, can you post the error messages.

---

### Post by jono30 on 2008-12-04
"sudo apt-get update" produces no errors.

"sudo apt-get upgrade" gives the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

---

### Post by ibutho on 2008-12-04
Try the command below
```
sudo rm /var/cache/apt/archives/lock
```
After that run the commands I showed you above and see if they work.

---

### Post by jono30 on 2008-12-05
"sudo rm /var/cache/apt/archives/lock" produced the error:
```
rm: cannot remove `/var/cache/apt/archives/lock': No such file or directory
```I then ran the previous commands, and "sudo apt-get upgrade" gave the same errors as before.  I also had a crash report notification, in relation to one of the linux-image-generic packages.

I then ran "sudo rm /var/cache/apt/archives/lock" again, and it simply gave me another command prompt, so I assume the command worked ok this time. So I ran  "sudo apt-get upgrade" again, which produced this response:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.24-21-generic (2.6.24-21.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-21-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.24-22-generic (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-22-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-22-generic (--configure):
 subprocess post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by jono30 on 2008-12-08
***bump***

Thanks in advance.

---

### Post by jenkinbr on 2008-12-08
Could you post the output of ```
fdisk -l
```

---

### Post by jono30 on 2008-12-08
I can't get fdisk to work, but just noticed in another thread that people used "df -h", so I tried that and it said one of the filesystems (/dev/sda1/) which is mounted at /boot is at 100%. When I did a directory listing for /boot, it gave this:

```
abi-2.6.24-16-generic          initrd.img-2.6.24-18-generic.bak
abi-2.6.24-17-generic          initrd.img-2.6.24-19-generic
abi-2.6.24-18-generic          initrd.img-2.6.24-19-generic.bak
abi-2.6.24-19-generic          initrd.img-2.6.24-21-generic
abi-2.6.24-21-generic          lost+found
abi-2.6.24-22-generic          memtest86+.bin
config-2.6.24-16-generic      System.map-2.6.24-16-generic
config-2.6.24-17-generic      System.map-2.6.24-17-generic
config-2.6.24-18-generic      System.map-2.6.24-18-generic
config-2.6.24-19-generic      System.map-2.6.24-19-generic
config-2.6.24-21-generic      System.map-2.6.24-21-generic
config-2.6.24-22-generic      System.map-2.6.24-22-generic
grub                  vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-17-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-18-generic
initrd.img-2.6.24-17-generic      vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-17-generic.bak  vmlinuz-2.6.24-21-generic
initrd.img-2.6.24-18-generic      vmlinuz-2.6.24-22-generic
```I decided to delete most of the above files (the earlier versions). This reduced the usage down to 61% and fixed some of th earlier errors. I'm going to reboot and see if that fixes the remaining problems.

---

### Post by jenkinbr on 2008-12-08
That's what I would have recommended

Be sure to run update-grub to update your bootloader menu so it isn't filled up with bogus entries. Note that you need to be root to run update-grub, so add sudo to the beginning.

---

