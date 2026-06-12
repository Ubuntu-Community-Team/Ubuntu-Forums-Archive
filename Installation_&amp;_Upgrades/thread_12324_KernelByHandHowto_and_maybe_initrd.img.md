---
title: "KernelByHandHowto and maybe initrd.img"
date: 2005-01-23
forum: Installation &amp; Upgrades
---

### Post by mathiasv on 2005-01-23
Hello.

I have been installing a new kernel following [KernelByHandHowto](http://www.ubuntulinux.org/wiki/KernelByHandHowto) 
, but after restart it says "Kernel panic: VFS: Unable to mount root fs on unknown-block (0,0)". This probably happens because I am missing some drivers, as I just tried to guess which were needed.

Googling and experiments with /usr/src/linux/.config, /boot/grub/menu.lst, make bzImage and mkinitrd have not brougth me any further. I would appreciate any help to get this working "the linux way" with or without an initrd.

Thanks in advance.
Mathias.

---

### Post by black hole sun on 2005-01-23
Sounds like a grub error - I believe it's trying to mount on an invalid partition number. Can you post your grub config, and the output of 

fdisk -l # that's an L not an I, also you'll need to be root to access FDISK

Thanks

---

### Post by mathiasv on 2005-01-24
Thanks for the reply. I suppose you think of /boot/grub/menu.lst as grub's config. Appreciate if you will take a look at the following:

The last kernel "Ubuntu, kernel 2.6.8.1-3-386" shown here boots just fine.

%%% Start quote from menu.lst %%%

```
## ## End Default Options ##

title           Ubuntu, kernel  (mv)
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/hda1 ro quiet splash
savedefault
boot

title           Ubuntu, kernel  (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/hda1 ro single
savedefault
boot

title           Ubuntu, kernel 2.6.8.1-3-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title           Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.8.1-3-386
savedefault
boot
```
%%% End quote from menu.lst %%%

Here comes the fdisk, but I have only one partition.

%%% Start quote from fdisk-output %%%
```
root@haddock:/home/mathias # fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       76527    38569576+  83  Linux
/dev/hda2           76528       77520      500472    f  W95 Ext'd (LBA)
/dev/hda5           76528       77520      500440+  82  Linux swap
```
%%% End quote from fdisk-output %%%

Really hope you can see something out of this.
Mathias.

---

### Post by KLineD on 2005-01-30
I have the exact same problem, with the preconfigured kernel booting just fine but the custom one not booting with the same kernel panic error. Anyone?

---

### Post by rnimz on 2005-01-30
I experienced the same thing, last night I installed, got the system up and running on  2.6.8.1-3-386 with the same setup as listed above. I used Synaptic package manager to update the kernel to 2.6.8.1-4-386.  I can't boot 2.6.8.1-4 at all, and for some reason during that package upgrade the system removed (or moved to a place I can find it) /boot/initrd.img-2.6.8.1-3-386. So now I am unable to boot either kernel. My menu.lst file looks exactly the same as above. Any help would be appreciated... (I can get at the file system with the Live CD). 

Reid

[B] More information in this thread, still not a way to get bck initrd.img though...
[http://ubuntuforums.org/showthread.php?t=696&page=1&pp=10&highlight=initrd.img](http://ubuntuforums.org/showthread.php?t=696&page=1&pp=10&highlight=initrd.img)[/B]

---

### Post by mathiasv on 2005-02-01
Heyhey! It seems to work now!

I just read the [KernelDoesNotSupportCapabilities](http://www.ubuntulinux.org/wiki/KernelDoesNotSupportCapabilities)
which describes how to make a initrd.img manually, which in my case is done like this:

```
mkdir /lib/modules/2.6.8.1/boot/
cp -a /lib/modules/2.6.8.1/kernel/security/capability.ko /lib/modules/2.6.8.1/boot/
mkinitrd -o /boot/initrd.img-2.6.8.1 2.6.8.1

```

Then you just have to change the  /boot/grub/menu.lst to refer to the newly made initrd.img. 

Now I just have to get my touchpad and a few minor details working. It can't be more than five minutes... Haha.. 
Good luck with it.
Mathias.

---

### Post by friez on 2005-02-05
check and make sure u have the right filesystem built into the kernel and not as a modules

---

