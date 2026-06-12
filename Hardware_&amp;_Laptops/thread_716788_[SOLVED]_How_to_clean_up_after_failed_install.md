---
title: "[SOLVED] How to clean up after failed install"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by cmnorton on 2008-03-06
I am stuck. I was trying to apply a patch for a Thinkpad T61 sound problem. This was out on Launchpad

[https://bugs.launchpad.net/ubuntu/+bug/122560](https://bugs.launchpad.net/ubuntu/+bug/122560)

specifically in 

[https://bugs.launchpad.net/ubuntu/+bug/122560/comments/41](https://bugs.launchpad.net/ubuntu/+bug/122560/comments/41)

I applied the commands, and got a failure. The "You have updates" icon appeared on my toolbar, and, when I clicked on that, I was told to run
sudo apt get-update -f, but that fails.  How can I reset all this?

Here is the failure:

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-10-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 8405kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 96753 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-10-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-10-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-10-generic
Cannot find /lib/modules/2.6.22-10-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-10-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-10-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Edit:
------
sudo dpkg -P -a is supposed to purge /var/lib/dpkg/status, but it did not. I manually purged the file, and my system can update once again.

[https://bugs.launchpad.net/ubuntu/+bug/199202](https://bugs.launchpad.net/ubuntu/+bug/199202)

---

