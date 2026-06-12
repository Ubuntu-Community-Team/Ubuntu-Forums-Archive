---
title: "problem with new kernel"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by adramalech on 2009-10-08
okay so i was just compiling a new custom kernel and it got to making .deb files correctly i go to install...it then goes to configuring the new menu.lst and then i say use the package maintainers one...and not mine....it then threw some weird error....towards the end....i  had a custom 2.6.31.1 not install correctly so i have tried totally removing it from my system this is after i installed a custom 2.6.31.2 and got the error on menu.lst

and now  when ever i install/remove/purge anything this is what happenes and it gives me a nice error.....

```

Setting up linux-image-2.6.31.2-amd (2.6.31.2-amd-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.31.2-amd
) points to /boot/initrd.img-2.6.31.2-amd
 (/boot/initrd.img-2.6.31.2-amd) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.31.2-amd.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.31.2-amd
) points to /boot/vmlinuz-2.6.31.2-amd
 (/boot/vmlinuz-2.6.31.2-amd) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.31.2-amd.postinst line 588.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31.2-amd
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31.2-amd.postinst line 1186.
dpkg: error processing linux-image-2.6.31.2-amd (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.31.1-mk
 linux-image-2.6.31.2-amd
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

i am wondering after i removed all the 2.6.31.1 out of /boot and out of /usr/src why it still is using that kernel version....

---

### Post by KyleRaynor on 2009-10-15
I'm sorry no one has answered before this. I'm just now seeing it.
Do you still have a copy of your 'original' menu.lst?(from before you started compiling the custom kernel)
If so could you post both it AND your new menu.lst?

---

