---
title: "Can't boot into live Ubuntu 8.10"
date: 2008-11-09
forum: General Help
---

### Post by thiagoaraujos on 2008-11-09
Hi folks,

I've got the following system configuration: MSI P6NGM-L motherboard, Core 2 Duo E7200, Seagate Barracuda SATA 500GB (on sata1) + WDC IDE 80GB (on ide1), LG H50N IDE CD-ROM (that should be enough for now).  I'm running Arch Linux right now on my system, but would like to give a try on a desktop distro like Ubuntu.

The problem is, I can't boot the live CD (the same happens to Mandriva, very similarly). I booted in verbose mode, disabling "silent" and "splash" options, and I've got a lot of messages like that:

[98.435349] EXT3-fs: mounted filesystem with ordered data mode
[.........] kjournald starting. Commit interval 5 seconds
..................

and over and over (with different incremental numbers), till I get into a busybox console, without no explicit errors. I type "exit" in the console, and I get something like:

cp: cannot create '/root/var/log': no such file or directory
mount: mounting /root/dev/ on /dev/.static/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
target filesystem doesn't have /sbin/init
no init found: try passing init= bootarg 

I've got an ext3 partition on SATA drive that runs Arch Linux. I think the overall problem's just strange, because live cd mode doesn't have to rely on a hard drive, or maybe it's just a hard drive or motherboard detection problem. 

I read somewhere that disabling IDEs could have some effect... I unplugged my IDE and got the same problem. So what could I do? Since I got that motherboard I had trouble booting in any Linux live CD, but I don't know wether this time it's really a motherboard problem, or a hard disk problem.

Thanks for any help

---

