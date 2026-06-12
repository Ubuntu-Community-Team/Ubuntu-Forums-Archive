---
title: "newbie needs grub help"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by n00b512 on 2009-11-02
My grub install is majorly hosed.  When I try to reinstall grub sudo grub-install /dev/sda I get "cannot find a device for /boot/grub" If I mount sda7 as /boot and run the same command it appears to work however no grub.cfg file is created and when I try to run update-grub it complains about not being able to find / When I actually try to boot this thing it drops to a grub> menu and when I try to cat grub/grub.cfg it can't find the cfg My device map is hd0 /dev/sda and grub ver is 1.97beta4  Why can't I install grub properly?

---

