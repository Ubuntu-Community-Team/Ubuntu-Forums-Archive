---
title: "Moving my ubuntu install"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by gw099 on 2009-08-13
So I've been using Ubuntu 9.04 on my external hard drive for the past couple of months or so and I absolutely love it. Now I've decided that I want to have ubuntu on my internal hard drive (160GB laptop) so I can dual boot with windows and run ubuntu without having to have my external drive with me all the time. I've done some internet searches on how to move an OS install but I havent been able to find a clear tutorial. Basically I want to move my partition without loosing my settings and data, is this possible?

Thnaks

---

### Post by ronparent on 2009-08-13
It sounds like you have a normal ubuntu install on your external drive. Find or make an unformated or ext2 formatted space on the internal drive (big enough to copy your entire ubuntu partitions to). Then, working from the live cd, bring up gparted and copy your install from the internal partition and paste that partition to the internal drive. You can do the same for swap (this method retains the uuid's). 

You didn't say whether the grub mbr was installed on the internal or external drive. If already on the internal drive you are done. With current grub implementation the ubuntu partitions are located by uuid so they will be located automatically as copied on the new drives. If on the external drive just run the grub setup routine to install it to the internal drive. Just remember, that both sets of ubuntu partitions now have the same uuid's. Therfore you should leave the external drive unplugged when booting to ubuntu. Otherwise, although it will still boot, it may be confusing trying to find which partition booted - and where your new data is saved to. If you have windows in menu.lst, you will have to edit it to find it if you have to setup grub on the internal drive.

---

