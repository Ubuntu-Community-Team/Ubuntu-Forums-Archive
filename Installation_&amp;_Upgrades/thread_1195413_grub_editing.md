---
title: "grub editing"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by ed sutcliffe on 2009-06-23
I would like to reduce the number of kernels  on my boot screen. I tried kgrub but I either am doing something wrong or it doesn't work. I'm dual booting with great success . I'm using a very low powered laptop (acer5515) . the vista worked so poorly that I researched other os's  big fan of ubuntu

---

### Post by yeats on 2009-06-23
There is a package in the repositories called startupmanager that lets you tweak GRUB in a nice interface.  Give it a shot.

---

### Post by merlinus on 2009-06-23
You can use synaptic, search for the kernels you wish to remove, and select that option.  /boot/grub/menu.lst will be automatically updated.

---

### Post by presence1960 on 2009-06-23
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

edit menu.lst by placing # on the options you want to hide as I did above on kernel 2.6.28-11.

It is still installed but won't show up on your menu. God forbid if something happens to another kernel and I cant boot I can boot the Live CD and uncomment that kernel. Since it is still installed I would be able to  boot from that kernel after uncommenting it.

---

### Post by ed sutcliffe on 2009-06-24
I was able to use the startupmaneger. Thanks for all the replies. I have been solving issues one at a time and learning along the way .You will hear from me again.

---

