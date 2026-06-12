---
title: "swap crashed after resume."
date: 2011-01-08
forum: Hardware
---

### Post by kazik1616 on 2011-01-08
Hello Forum.
After installation of GRUB2 I have following issue:
When starting laptop after hibernating the system, the system does not resume but is performing normal startup. Moreover after startup, my swap partition seems to be crashed.
Symptompts:
1. free command does not show swap space
2. swapon /dev/sda7 before free command also does not show swap space. I must perform mkswap /dev/sda7 & swapon /dev/sda7. After that I am adding swap uuid to /etc/initramfs-tools/conf.d/resume file.
Moreover everything was working fine when using old GRUB.
Using default kernel with ubuntu 10.10
Any ideas?


here is output of my  filefrag -v /dev/sda7
Filesystem type is: 1021994
File size of /dev/sda7 is 0 (0 blocks, blocksize 4096)
/dev/sda7: 0 extents found

My uncommented lines from /etc/default/grub:
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=4
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

