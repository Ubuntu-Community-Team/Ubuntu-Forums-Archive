---
title: "Multi Boot Problems"
date: 2008-11-06
forum: General Help
---

### Post by ronnielsen1 on 2008-11-06
I thought I had this grub thing figured out but I'm stuck. I'm quad booting Win Vista, XP, Mepis 8 and Ubuntu 8.10
According to gparted Mepis is at sda3 and Ubuntu is at sda5
Vista is at sdb2 and XP is at sdb5
Vista and XP work with the Vista bootloader - the linux part didn't work
Ubuntu works with grub - Mepis does not - It returns an error of 

> Read-error on swap-device (3:2:0) Kernel panic - not syncing : VFS Unable to mount root fs on unknown-block (0,0) 			 		

My boot/grub/menu.lst is as follows

> # menu.lst - See: grub([IMG]http://mepislovers.org/forums/images/smilies/cool.gif[/IMG], info grub, update-grub([IMG]http://mepislovers.org/forums/images/smilies/cool.gif[/IMG]


title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        bb187c58-bcf7-44b2-9ae2-5b2ed51e2158
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=bb187c58-bcf7-44b2-9ae2-5b2ed51e2158 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet



title        memtest86+
uuid        bb187c58-bcf7-44b2-9ae2-5b2ed51e2158
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        MEPIS at sda3, kernel 2.6.26-1-mepis-smp (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.26-1-mepis-smp root=/dev/sda3 nomce quiet splash vga=791 resume=/dev/hda2 
savedefault
boot





# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista & XP (loader)
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1 			 		

So, everything works except for Mepis

[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Mepis/sda_snapshot.png[/IMG]
[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Mepis/sdb_snapshot.png[/IMG]

---

### Post by indytim on 2008-11-06
I have no intimate knowledge of Mepis.  From what you described in your post, I'd suggest checking the fstab in Mepis.  The /swap may be incorrectly identified there.  Just a WAG :),

IndyTim

---

### Post by caljohnsmith on 2008-11-06
According to the [Mepis Wiki page]("http://www.google.com/url?sa=U&start=1&q=http://www.mepis.org/docs/en/index.php/GRUB&usg=AFQjCNE4vmnk8vkNE5HXHYaOSmQOBuHdqA"), Mepis uses Grub. If you can locate Mepis' Grub menu.lst or grub.conf file, you can simply link to it from your Ubuntu menu.lst:
```
title Mepis Grub Menu
configfile (hd0,2)/boo/grub/menu.lst
```
If Mepis won't even boot correctly from its own self-generated Grub menu.lst, then I don't think you have a problem with Grub; the problem would most likely be Mepis.

---

