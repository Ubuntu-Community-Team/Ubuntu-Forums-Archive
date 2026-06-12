---
title: "Mounting iPod that was previously mounted in VMWare"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by Strider42 on 2007-04-02
Hi,

I'm having a problem remounting my iPod in Ubuntu after it has been ejected in a VMWare XP installation.  VMWare finds the pod, but once ejected I can't seem to get it mounted again in Ubuntu without a reboot.

Is there a way to do this simply from within Gnome or a terminal window?

sudo mount /dev/sda2 /mnt/ipod fails with:

mount: you must specify the filesystem type

/etc/fstab has this entry: /dev/sda2       /mnt/ipod       vfat    rw,user,noauto          0       0

Any help gratefully appreciated.  Is there an application that let's you mount and unmount all system devices?

Thanks
Paul

---

