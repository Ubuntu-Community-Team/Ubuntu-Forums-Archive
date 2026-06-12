---
title: "Remove multiple Kernel entries in GRUB?"
date: 2008-11-15
forum: General Help
---

### Post by wightghost on 2008-11-15
As the title suggests, I have several entries relating to Kernels in the GRUB menu as shown below:
> 
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=51a78f5e-42ad-44ee-9da3-583ff8ae3a11 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=51a78f5e-42ad-44ee-9da3-583ff8ae3a11 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=51a78f5e-42ad-44ee-9da3-583ff8ae3a11 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=51a78f5e-42ad-44ee-9da3-583ff8ae3a11 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=51a78f5e-42ad-44ee-9da3-583ff8ae3a11 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=51a78f5e-42ad-44ee-9da3-583ff8ae3a11 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Since my system is working fine can I delete the old Kernel entries (2.6.24-16-generic and 2.6.24-19-generic) without causing problems?

Thanks for any help.

---

### Post by pytheas22 on 2008-11-16
Yes, you can delete the lines from your grub menu without a problem (back it up first just in case...although this is a really low-risk operation).  You can also delete the extraneous kernel images (i.e. everything besides /boot/initrd.img-2.6.24-21-generic) from your /boot directory too, if you want.

FYI: Ubuntu 8.10 is supposed to delete old kernels automatically, although I haven't used it long enough to see if it actually does.

---

### Post by grj23 on 2010-02-15
> **pytheas22 said:**
> Yes, you can delete the lines from your grub menu without a problem (back it up first just in case...although this is a really low-risk operation).  You can also delete the extraneous kernel images (i.e. everything besides /boot/initrd.img-2.6.24-21-generic) from your /boot directory too, if you want.

FYI: Ubuntu 8.10 is supposed to delete old kernels automatically, although I haven't used it long enough to see if it actually does.

Where exactly is the grub menu?  Which file is it?  Thought I'd double check before I fiddled  ;)

Thanks...

---

### Post by plucky on 2010-02-15
> **grj23 said:**
> Where exactly is the grub menu?  Which file is it?  Thought I'd double check before I fiddled  ;)

Thanks...

```
/boot/grub/menu.lst
```

To remove old kernels,use **Synaptic Package Manager** and search for **linux-image** and select the older kernels for complete removal.This will remove the extra kernels from your grub menu.

It is a good idea to leave at least one older kernel just in case you break the current kernel.

Good Luck

---

### Post by scouser73 on 2010-02-15
Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by timgood on 2010-02-15
A much quicker way is to install Ubuntu Tweak from GetDeb here:

[http://www.getdeb.net/updates/Ubuntu/9.10/?q=tweak]("http://www.getdeb.net/updates/Ubuntu/9.10/?q=tweak")

which will do the whole lot for you, automatically.


Hope this helps.

---

### Post by grj23 on 2010-02-15
Thanks all!  Very helpful as always.

---

