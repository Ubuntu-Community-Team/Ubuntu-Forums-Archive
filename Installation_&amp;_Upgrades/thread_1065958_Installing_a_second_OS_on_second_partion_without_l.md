---
title: "Installing a second OS on second partion without loosing original partion contents."
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by ggerules on 2009-02-10
Hi, 

I am hoping I am posting to the right forum.

I have a dell 1525 laptop that is working great with hardy installed. 

Is there a way I could resize the partition that has hardy on it to something smaller so that I could create another partion to install another OS and still have both active to boot up?

Thanks George

---

### Post by logos34 on 2009-02-10
sure, boot the live cd and use gparted

>system>admin>partition editor

(live cd because / cannot be mounted during shrink)

just make sure that when you install the new OS not to let it overwrite the ubuntu Grub bootloader if that's the one you want to continue to use.  You can add the new OS to menu.lst [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile").

---

