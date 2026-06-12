---
title: "After upgrading"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by raunhar on 2009-04-13
I had installed 8.10 and later clicked on upgrade option.
Now in GRUB I am getting two more options , the latest two being of Kernel with new version and new version kernel with safe mode. The old kernel version boot option still exists.
How can  remove it and will it be safe to remove it.

---

### Post by Cybie257 on 2009-04-13
> **raunhar said:**
> I had installed 8.10 and later clicked on upgrade option.
Now in GRUB I am getting two more options , the latest two being of Kernel with new version and new version kernel with safe mode. The old kernel version boot option still exists.
How can  remove it and will it be safe to remove it.

sudo gedit /boot/grub/menu.lst

Don't delete the information, but comment them out with the "#" sign. Best to double them up "##" (see example). that way you can always re-enable it if needed. 

Also, it's always a good idea to leave one old kernel available in case something goes wrong and can't boot up. You can always try to boot into and older kernal to fix any problems. Has saved me a few times. 

EXAMPLE: (BEFORE)

```
## ## End Default Options ##

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		473ff6b6-c1c6-4b64-8a5b-32ce03bef89e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=473ff6b6-c1c6-4b64-8a5b-32ce03bef89e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		473ff6b6-c1c6-4b64-8a5b-32ce03bef89e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=473ff6b6-c1c6-4b64-8a5b-32ce03bef89e ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-8-generic
uuid		473ff6b6-c1c6-4b64-8a5b-32ce03bef89e
kernel		/boot/vmlinuz-2.6.28-8-generic root=UUID=473ff6b6-c1c6-4b64-8a5b-32ce03bef89e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-8-generic
quiet

```

AFTER:

```
## ## End Default Options ##

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		473ff6b6-c1c6-4b64-8a5b-32ce03bef89e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=473ff6b6-c1c6-4b64-8a5b-32ce03bef89e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

##title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
##uuid		473ff6b6-c1c6-4b64-8a5b-32ce03bef89e
##kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=473ff6b6-c1c6-4b64-8a5b-32ce03bef89e ro  single
##initrd		/boot/initrd.img-2.6.28-11-generic

##title		Ubuntu jaunty (development branch), kernel 2.6.28-8-generic
##uuid		473ff6b6-c1c6-4b64-8a5b-32ce03bef89e
##kernel		/boot/vmlinuz-2.6.28-8-generic root=UUID=473ff6b6-c1c6-4b64-8a5b-32ce03bef89e ro quiet splash 
##initrd		/boot/initrd.img-2.6.28-8-generic
##quiet

```


-Cybie

PS> These are snippets and not the whole menu.lst file.

---

