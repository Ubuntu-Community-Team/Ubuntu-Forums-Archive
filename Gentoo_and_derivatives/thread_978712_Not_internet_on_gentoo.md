---
title: "Not internet on gentoo"
date: 2008-11-11
forum: Gentoo and derivatives
---

### Post by Mr.Macdonald on 2008-11-11
I have successfully installed gentoo, but without internet! I am missing the device eth0. I emerged dhcp and configured /etc/conf.d/net but nothing changed.

I was told to look in "/lib/modules/*/kernel/drivers/net" but i don't have a "kernel/drivers/net" folder, although I just found that I have a "/lib/modules/*/build/drivers/net" with a bunch of stuff in it?

The only way to install anything (and get internet) is to boot the live cd and mount my whole system. Then chroot into it!

I followed the installation guide [here]("http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml") and I don't have internet

---

### Post by Ayuthia on 2008-11-12
Did you compile your own kernel?  It looks like you might not have done make modules_install to load the modules into /lib/modules.

---

### Post by regomodo on 2008-11-12
Install NetworkManager. It'll save you a few grey hairs. Also post the output of lspci and lsmod.

---

