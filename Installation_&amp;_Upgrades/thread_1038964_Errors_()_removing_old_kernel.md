---
title: "Errors (?) removing old kernel"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by bixejo on 2009-01-14
Hello all,

Yesterday I removed an old kernel after installing a new one (still I have two kernels, the one I installed and the previous one, the removed one was the third).

I got the following messages that sound rather worrisome to me. The system seems to work fine, however, but I'm not sure whether this may cause some trouble in the future.

Could any of you tell me whether I should worry about this, please?

Uninstalling messages transcription follow (I tried to translate into English those messages I got in Spanish. Hope I did it correctly.):

> 
(Reading database ...  
202593 files and directories currently installed.)
Uninstalling linux-ubuntu-modules-2.6.22-14-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Uninstalling linux-restricted-modules-2.6.22-14-generic ...
Uninstalling linux-image-2.6.22-14-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Uninstalling: fglrx 8.471 (2.6.22-14-generic) (x86_64)
[B]dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

Error! Bad conf file.
Your dkms.conf is not valid.[/B]
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done
Thank you in advance,

---

### Post by Tim Sharitt on 2009-01-14
From what I can tell, the dkms.conf file that is invalid here was for the fglrx module that was removed. The only problem you may have is that the fglrx kernel module may not have been completly removed. However, this should not cause any problems in the future, aside from the small amount of space the module takes up.

---

### Post by bixejo on 2009-01-14
> **Tim Sharitt said:**
> From what I can tell, the dkms.conf file that is invalid here was for the fglrx module that was removed. The only problem you may have is that the fglrx kernel module may not have been completly removed. However, this should not cause any problems in the future, aside from the small amount of space the module takes up.
Thank you for your reply, Tim.

I indeed had the fglrx driver installed for the removed kernel, and had to reinstall it again (same driver, same version) after updating the kernel. This' something I have to do for it to work adequately after any kernel update.

Maybe this reinstallation moved the driver to the new kernel so that it disappeared from the old one, and that's why it could not be removed when uninstalling the old kernel (?).

Thank you again,

---

