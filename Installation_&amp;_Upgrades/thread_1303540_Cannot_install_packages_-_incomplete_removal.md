---
title: "Cannot install packages - incomplete removal"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by bwinfrey on 2009-10-28
[http://ubuntuforums.org/showthread.php?t=1297628](http://ubuntuforums.org/showthread.php?t=1297628)

Unfortunately I removed the restricted modules packages prior to the reply in thread above.  So, here's the problem....

ath5k works horribly ...
```
--- router ping statistics ---
57 packets transmitted, 18 received, 68% packet loss, time 56143ms
rtt min/avg/max/mdev = 2.379/22.819/127.619/32.336 ms

```
The same H/W and OS running in VMWare/Windows (virtual machine boots linux on dual boot wubi install)
```
--- router ping statistics ---
78 packets transmitted, 78 received, 0% packet loss, time 77160ms
rtt min/avg/max/mdev = 1.659/8.606/58.200/11.369 ms

```
attempted to re-install linux-restricted-modules-2.6.28-16-generic.  I did not notice any errors, but I could not boot to 2.6.28-16-generic.

Next I attempted to remove linux-restricted-modules-2.6.28-16-generic, but errors were encountered.  I then tried to re-install linux-image-2.6.28-16-generic and the following is the output - which is the same error as the previous attempt to remove restricted...
```
sudo dpkg --force-all -r linux-image-2.6.28-16-generic linux-restricted-modules-2.6.28-16-generic 
(Reading database ... 275230 files and directories currently installed.)
Removing linux-image-2.6.28-16-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/last-good-boot
dpkg: error processing linux-image-2.6.28-16-generic (--remove):
 cannot remove `/boot/vmcoreinfo-2.6.28-16-generic': Input/output error
Removing linux-restricted-modules-2.6.28-16-generic ...
rmdir: failed to remove `/lib/modules/2.6.28-16-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.28-16-generic': Input/output error
update-initramfs: Generating /boot/initrd.img-2.6.28-16-generic
mv: cannot move `/boot/initrd.img-2.6.28-16-generic.new' to `/boot/initrd.img-2.6.28-16-generic': No such file or directory
dpkg: error processing linux-restricted-modules-2.6.28-16-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.28-16-generic
 linux-restricted-modules-2.6.28-16-generic
```

Can anyone help me restore.  I am currently booting to the previous kernel.  I would like to restore back to a working 2.6.28-16 Mad-WiFi set up.

Thanks...

---

### Post by bwinfrey on 2009-10-31
I booted to the recovery option and ran these menu items to correct the problem.

FSCK
DPKG - Failed due to ath5k status, so I blacklisted ath5k and retried.  It did not try to connect. It removed the broken packages.  It suggested GRUB. 
GRUB

Now I am able to install.

---

