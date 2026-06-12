---
title: "need to edit grub.conf"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by shahdharmit on 2009-09-16
Hello,

I am Fedora 11 user. I just installed Ubuntu 9.04 on my laptop. I didn't let Ubuntu install the boot loader. Now I need to edit grub.conf of my Fedora 11 to boot Ubuntu 9.04. What changes should I make to the grub.conf in order to boot Ubuntu?

Thanks.

---

### Post by earthpigg on 2009-09-16
can you show us your existing one, and share with us your partition scheme?

---

### Post by shahdharmit on 2009-09-16
title Fedora (2.6.30.5-43.fc11.i686.PAE)
    root (hd0,4)
    kernel /vmlinuz-2.6.30.5-43.fc11.i686.PAE ro root=/dev/mapper/vg_dharmit-lv_root rhgb quiet
    initrd /initrd-2.6.30.5-43.fc11.i686.PAE.img
title Fedora (2.6.29.6-217.2.16.fc11.i686.PAE)
    root (hd0,4)
    kernel /vmlinuz-2.6.29.6-217.2.16.fc11.i686.PAE ro root=/dev/mapper/vg_dharmit-lv_root rhgb quiet
    initrd /initrd-2.6.29.6-217.2.16.fc11.i686.PAE.img
title Fedora (2.6.29.6-217.2.8.fc11.i686.PAE)
    root (hd0,4)
    kernel /vmlinuz-2.6.29.6-217.2.8.fc11.i686.PAE ro root=/dev/mapper/vg_dharmit-lv_root rhgb quiet
    initrd /initrd-2.6.29.6-217.2.8.fc11.i686.PAE.img
title Ubuntu 9.04
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.18-128.el5 ro root=/dev/sda0 rhgb quiet
    initrd /boot/initrd-2.6.18-128.el5.img 


Ubuntu is installed on /dev/sda0

---

### Post by plucky on 2009-09-16
Try a chainloader boot,add this to the grub.conf file

```
title	Ubuntu 9.04 chainloader Boot
configfile (hd0,0)/boot/grub/menu.lst
```

This assumes Ubuntu is installed on /dev/sda1. /dev/sda0 does not exist.

and see if that works.

This will pick up the menu.lst file from your Ubuntu install and use that to boot.So as long as that is set up correctly by the install,your system should boot Ubuntu when the chainloader boot is selected.

This also has the advantage that it won't break when you have kernel upgrades on ubuntu.

Good Luck

---

### Post by shahdharmit on 2009-09-16
Thanks plucky for the suggestion but it gives the following result

> Error 1 : Filename must be either an absolute pathname or blocklist

Following is the Ubuntu part of grub.conf of my Fedora 11

> 
title    Ubuntu 9.04
    chainloader Boot
    configfile (hd0,0)/boot/grub/menu.lst


---

### Post by plucky on 2009-09-16
> title Ubuntu 9.04
chainloader Boot
configfile (hd0,0)/boot/grub/menu.lst 


This is incorrect,it should be on two lines as it should be executing the line "configfile (hd0,0)/boot/grub/menu.lst".

So the first line should be "title Ubuntu 9.04 chainloader Boot".

It is trying to execute the line "chainloader Boot" which is meaningless,that is why you are getting the error "Error 1 : Filename must be either an absolute pathname or blocklist".

See previous post


Good Luck

---

### Post by shahdharmit on 2009-09-16
Finally the issue has been solved and I posted the method I employed in the following post [http://forums.fedoraforum.org/showthread.php?t=230239](http://forums.fedoraforum.org/showthread.php?t=230239)

Thanks all for spending your precious time in solving my problem.

---

