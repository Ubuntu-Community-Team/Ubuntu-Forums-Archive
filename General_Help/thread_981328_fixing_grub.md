---
title: "fixing grub"
date: 2008-11-13
forum: General Help
---

### Post by jimi_hendrix on 2008-11-13
so i installe arch(on a diff partition)...which reinstalled grub...now what o i put in my /boot/grub/menu.lst to boot to ubuntu? its on my sda6 partition

---

### Post by plucky on 2008-11-13
I suggest you use [config_file_boot](http://users.bigpond.net.au/hermanzone/p15.htm#Second_method_configfile_boot) so that you will always boot the latest kernel when Ubuntu kernel is updated.


Just add the line ```
title  Ubuntu 8.04
configfile (hd0,5)/boot/grub/menu.lst
``` to your menu.lst and select it when the grub menu comes up.


Good Luck

---

