---
title: "dpkg keeps being 'interrupted', and needing to replace blacklist-oss.conf"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by moorote on 2009-10-16
While trying to install Wine, I was told that I did not have the 'flex' package - which led me to a problem that's been hanging around for a while and finally got me onto these forums. (I need help!)

This error message has come up a few times when trying to install various packages/apps: 
[INDENT][FONT=Courier New]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
[/FONT][/INDENT]On doing what it says (i.e. putting the above into the Terminal), the following comes up: 
[INDENT][FONT=Courier New]Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
cpio: ./etc/modprobe.d/blacklist-oss.conf: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: subprocess post-installation script returned error exit status 1
[/FONT][/INDENT]I think I may have deleted blacklist-oss.conf in the past to fix the sound on my Medion laptop (which actually worked), but now it seems I need it again. How can I fix this, and how do I get dpkg working again?

Thanks so much in advance.

---

