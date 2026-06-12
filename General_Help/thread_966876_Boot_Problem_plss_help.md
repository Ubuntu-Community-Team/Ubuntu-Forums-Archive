---
title: "Boot Problem plss help"
date: 2008-11-01
forum: General Help
---

### Post by kaushikashwin on 2008-11-01
i installed ubuntu 8.10 in E:(10GB partition) from vista 32bit x86
everythin went fine.installed
during boot, the ubuntu screen even appears but after that i get this msg

current working directory (ie,the relative path) is ubuntu/disks
     [linux-bzImage,setup 0x3000 , size =0x220cb0]
     [linux-initrd @ 0x7e5a1000 , 0xB0dac8 bytes]
loading please wait
gave up waiting for root device.   commom problem:
   -boot args(cat  /proc/cmdline)
       -check rootdelay=(did system wait long enough?)
       -check root=(did system wait long for right device?)
   -missing modules (cat /proc/modules ; IS /dev)
ALERT! /dev/disk/by-UUID/9E08EBBF08EB9495  does not exist.dropping to shell!


Busybox v1.10.2 (ubuntu 1:1.10.2-(ubuntu6)built-in shell(ash)
enter help for a list of built in commands

(initrafns) [35.656279]ata1.00:revalidation failed (errno=-19)



i donno wat this s n i m new to linux.plss help me solve this pblm n plss do a detail explanation coz i donno abt those commands.thnk u ppl in advance.

---

### Post by stinedvd on 2008-11-19
I have the same issue and have just installed 8.10 Server on a Dell 1650.  If I type exit at the (initramfs) prompt it boots normally, but I'm not sure why the boot sequence is getting stuck here.  

kaushikashwin, 
  Are you still getting this error?  Did you find a way to fix this?

---

### Post by caljohnsmith on 2008-11-19
Try adding "rootdelay=130" to your Ubuntu kernel line in your Grub's menu.lst:

[http://ubuntuforums.org/showthread.php?p=6211817](http://ubuntuforums.org/showthread.php?p=6211817)

Let me know if that makes any difference.

---

### Post by stinedvd on 2008-11-19
Thanks.  I found (Bug 290153) and added rootdelay=90 and all is good.  I should have searched more before posting.

---

