---
title: "Unable to upgrade to 8.04.2"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by Jvaldezjr on 2009-03-09
When I try to update Hardy to 8.04.2 I get the follwoing errors with Apt:

```
Unpacking replacement linux-image-2.6.24-23-generic ...                                                                          
dpkg-deb: subprocess paste killed by signal (Broken pipe)                                                                        
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb (--unpack):                   
 short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.24-23-generic/kernel/drivers/isdn/sc/sc.ko')              
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=2b649ae9-b45a-43b1-b5a8-983e71bbec53'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace wine-dev 1.1.15~winehq0~ubuntu~8.04-0ubuntu2 (using .../wine-dev_1.1.16~winehq0~ubuntu~8.04-0ubuntu1_i386.deb) ...
Unpacking replacement wine-dev ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb
```

Anyone know how to correct this?

---

### Post by albandy on 2009-03-09
try this:
sudo dpkg -i /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb

and then put the result

---

### Post by Jvaldezjr on 2009-03-09
```
Preparing to replace linux-image-2.6.24-23-generic 2.6.24-23.46 (using .../linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-23-generic ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.24-23-generic/kernel/drivers/isdn/sc/sc.ko')
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=2b649ae9-b45a-43b1-b5a8-983e71bbec53'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb
```

Here it is.

---

### Post by Jvaldezjr on 2009-03-10
I found that when I tried to update wine, one of the packages were broken, so I fixed that problem, and all the 51 packages with the 8.04.2 update installed, except for the newer kernel.  I don't know why I'm still getting these errors, but I sitll have a usable system, and I'll probably reinstall Kubuntu when Jaunty comes out, so I'm going to ignore it for now.

---

