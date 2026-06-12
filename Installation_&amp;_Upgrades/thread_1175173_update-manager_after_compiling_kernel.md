---
title: "update-manager after compiling kernel"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by renkinjutsu on 2009-05-31
i compiled a new kernel to use with Jaunty 9.04 using this method 
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html)

and now the update-manager keeps popping up with an error message telling me it couldn't update my kernel and points to the deb package built using the guide above... how do i keep update-manager from trying to update my kernel?

---

### Post by renkinjutsu on 2009-06-02
please? anyone?
how do i get the whole system to ignore the installed .deb of my new kernel image? .. it's really annoying, every time i install a new package, it spends 10 minutes at the end 'configuring' my kernel and it's trying to generate a new initrd and everything! .. then it ends up failing at the end with an error message.. this is really annoying.

---

### Post by renkinjutsu on 2009-06-03
Here's what happens when installing/upgrading packages

```
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up linux-image-2.6.30-rc7-compiled (2.6.30-rc7-compiled-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.30-rc7-compiled
) points to /boot/initrd.img-2.6.30-rc7-compiled
 (/boot/initrd.img-2.6.30-rc7-compiled) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30-rc7-compiled.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.30-rc7-compiled
) points to /boot/vmlinuz-2.6.30-rc7-compiled
 (/boot/vmlinuz-2.6.30-rc7-compiled) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30-rc7-compiled.postinst line 588.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-rc7-compiled
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-10-generic
Found kernel: /boot/vmlinuz-2.6.28-9-generic
Found kernel: /boot/vmlinuz-2.6.28-8-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30-rc7-compiled.postinst line 1186.
dpkg: error processing linux-image-2.6.30-rc7-compiled (--configure):
 subprocess post-installation script returned error exit status 2
Setting up foomatic-db-engine (4.0.0-0ubuntu6.1) ...
```

then after setting up all the packages it ends with: 

```
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 linux-image-2.6.30-rc7-compiled
```

the output when installing the .deb linux-image
```
sudo dpkg -i linux-image-2.6.30-rc7-compiled_2.6.30-rc7-compiled-10.00.Custom_i386.deb
(Reading database ... 222977 files and directories currently installed.)
Preparing to replace linux-image-2.6.30-rc7-compiled 2.6.30-rc7-compiled-10.00.Custom (using linux-image-2.6.30-rc7-compiled_2.6.30-rc7-compiled-10.00.Custom_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.30-rc7-compiled ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-rc7-compiled
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-10-generic
Found kernel: /boot/vmlinuz-2.6.28-9-generic
Found kernel: /boot/vmlinuz-2.6.28-8-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-2.6.30-rc7-compiled (2.6.30-rc7-compiled-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.30-rc7-compiled-10.00.Custom was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.30-rc7-compiled-10.00.Custom was configured last, according to dpkg)
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-rc7-compiled
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-10-generic
Found kernel: /boot/vmlinuz-2.6.28-9-generic
Found kernel: /boot/vmlinuz-2.6.28-8-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30-rc7-compiled.postinst line 1186.
dpkg: error processing linux-image-2.6.30-rc7-compiled (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.30-rc7-compiled

```

---

