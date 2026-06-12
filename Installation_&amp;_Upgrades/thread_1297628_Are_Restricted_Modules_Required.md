---
title: "Are Restricted Modules Required?"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by bwinfrey on 2009-10-21
After an update I lost Mad-Wifi interface and it was no longer listed in jockey.  

I changed the blacklists and wifi is working with ath5k.  Can I get rid of all the restricted modules?  How can I tell if they are needed?

Thanks.

---

### Post by Mark Phelps on 2009-10-22
The only time you "need" restricted modules is when the default drivers don't provide all the functionality you need and the restricted modules do.

My guess would be that,at most, you have two restricted modules available -- one for WiFi and one for video.  Leaving them there won't hurt anything.

This is a case where "if it's not broken, don't fix it", meaning, you're better off leaving it alone.

---

### Post by bwinfrey on 2009-10-27
Unfortunately I removed the packages prior to the reply in thread above.  So, here's the problem....

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

