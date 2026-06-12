---
title: "Ubuntu as secondary distro - need to update grub"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by pete-the-meat on 2009-01-10
Hi :)

I have just installed Ubuntu as my secondary distro alongside ArchLinux as the first and want to add it now to my existing menu.lst (included below). Arch is installed on /dev/sdb3 and the /boot partition where grub is installed is /dev/sdb1 - Ubuntu currently resides on /dev/sdb5. How would I go about adding Ubuntu to this list?

Thanks in advance :)

```

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/hda        (hd0)
#  /dev/hdb2       (hd1,1)
#  /dev/hda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/df006190-526e-44e8-a902-4eabed8a535c ro
initrd /kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/df006190-526e-44e8-a902-4eabed8a535c ro
initrd /kernel26-fallback.img

```

---

### Post by mikewhatever on 2009-01-10
Here are the entries from my menu.lst for regular and recovery mode.
> title           Ubuntu 8.10, kernel 2.6.27-9-generic
uuid            35641887-5022-
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=35641887- ro quiet splash
initrd          /boot/initrd.img-2.6.27-9-generic
quiet


title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		3564188
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=35 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic


You can find out the correct UUID for /dev/sdb5 with the help of <sudo vol_id -u /dev/sdb5>, and the relevant info about the kernel version by looking into /boot on the Ubuntu root partition.

---

### Post by lha on 2009-01-10
Use the configfile command; something like

```
title        Ubuntu
configfile   (hd1,4)/boot/grub/menu.lst
```

---

### Post by caljohnsmith on 2009-01-10
I would try what lha suggested with a small change:
```
title        Ubuntu Grub Menu
configfile   (hd0,4)/boot/grub/menu.lst
```
You mentioned that Ubuntu is on the same drive as Arch, and since Arch is on (hd0), Ubuntu would be too. How about giving it a shot and let us know how it goes.

---

### Post by pete-the-meat on 2009-01-10
Here is my updated menu.lst:

```

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/hda        (hd0)
#  /dev/hdb2       (hd1,1)
#  /dev/hda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/df006190-526e-44e8-a902-4eabed8a535c ro
initrd /kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/df006190-526e-44e8-a902-4eabed8a535c ro
initrd /kernel26-fallback.img

# (2) Ubuntu 8.10
title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid 6100d203-a7a6-4f8e-adbe-41c0052ae076
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=6100d203-a7a6-4f8e-adbe-41c0052ae076 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

# (3) Ubuntu 8.10 Recovery)
title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid 6100d203-a7a6-4f8e-adbe-41c0052ae076
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=6100d203-a7a6-4f8e-adbe-41c0052ae076 ro single
initrd /boot/initrd.img-2.6.27-7-generic 

```

I took the route that mikewhatever suggested, except since I can't boot into Ubuntu yet I took the UUID from GParted under Arch. I am certain that it is correct and that the kernel file names are also correct. However whenever I select them in the grub menu it just tells me file not found :(

---

### Post by pete-the-meat on 2009-01-10
Got it working! :D

The updated menu.lst is below - thanks for all your help! :)

```

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/hda        (hd0)
#  /dev/hdb2       (hd1,1)
#  /dev/hda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/df006190-526e-44e8-a902-4eabed8a535c ro
initrd /kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/df006190-526e-44e8-a902-4eabed8a535c ro
initrd /kernel26-fallback.img

#(2) Ubuntu 8.10
title	Ubuntu 8.10
root	(hd,0,4)
kernel	/boot/vmlinuz-2.6.27-7-generic root=UUID=6100d203-a7a6-4f8e-adbe-41c0052ae076 ro quiet splash
initrd	/boot/initrd.img-2.6.27-7-generic

#(3) Ubuntu 8.10 (recovery mode)
title	Ubuntu 8.10 (recovery mode)
root	(hd,0,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=/6100d203-a7a6-4f8e-adbe-41c0052ae076 ro single
initrd	/boot/initrd.img-2.6.27-7-generic

```

---

### Post by Herman on 2009-01-10
You can use what mikewhatever suggested, but I suggest a few small changes:
```
#(2) Ubuntu 8.10
title    Ubuntu 8.10
root    (hd0,4)
kernel    [COLOR=Red]**/boot**[/COLOR]/vmlinuz[COLOR=Red]**-2.6.27-7-generic**[/COLOR] root=UUID=6100d203-a7a6-4f8e-adbe-41c0052ae076 ro quiet splash
initrd    [COLOR=Red]**/boot**[/COLOR]/initrd.img[COLOR=Red]**-2.6.27-7-generic**[/COLOR]

#(3) Ubuntu 8.10 (recovery mode)
title    Ubuntu 8.10 (recovery mode)
root    (hd0,4)
kernel [COLOR=Red]**/boot**[/COLOR]/vmlinuz[COLOR=Red]**-2.6.27-7-generic**[/COLOR] root=UUID=/6100d203-a7a6-4f8e-adbe-41c0052ae076 ro single
initrd    [COLOR=Red]**/boot**[/COLOR]/initrd.img[COLOR=Red]**-2.6.27-7-generic**[/COLOR]
```I would suggest deleting all references to a specific kernel and initrd.img and booting by the symlinks (shortcuts) to whatever the current kernel and initrd happens to be at any time. That way you won't need to go and update your menu.lst manually every time there's a kernel update. ```
#(2) Ubuntu 8.10
title    Ubuntu 8.10
root    (hd0,4)
kernel    /vmlinuz root=UUID=6100d203-a7a6-4f8e-adbe-41c0052ae076 ro quiet splash
initrd    /initrd.img

#(3) Ubuntu 8.10 (recovery mode)
title    Ubuntu 8.10 (recovery mode)
root    (hd0,4)
kernel /vmlinuz root=UUID=/6100d203-a7a6-4f8e-adbe-41c0052ae076 ro single
initrd    /initrd.img
``` Regards, Herman :)

---

### Post by pete-the-meat on 2009-01-10
Cheers Herman - worked like a charm!

How do I mark this as solved?

---

### Post by bendib on 2009-01-10
here is what you do.

title		Ubuntu linux
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
I would check /boot of that partition and make sure the names of  the kernel and initrd are correct.

Cheers!

---

### Post by Herman on 2009-01-10
> here is what you do.

title		Ubuntu linux
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
I would check /boot of that partition and make sure the names of  the kernel and initrd are correct.

Cheers! :) You want to would boot Ubuntu directly by it's specific kernel and initrd.img when you're booting from Ubuntu's own internal menu.lst file, because Ubuntu is programmed to run the update-grub script, which automatically updates the menu.lst  at every kernel update.

If you're booting Ubuntu from some other operating system, or from GRUB in a Dedicated GRUB Partition, it's best to use a configfile boot, like lha and caljohnsmith suggested, or install Ubuntu's boot loader to the boot sector of a partition and chainload it, or boot by the symlinks so that you will be booting Ubuntu by it's most up to date kernel.
That aviods the need to manually edit menu.lst files every time there are kernel updates, and if you're booting many Linux systems, that can get to be a laborious task.
It's important to be booting the most up to date kernels, because those may contian security updates as well as enhancements which might make your hardware work better, and allow more advanced programs to work properly too.
You would only want to remain with an out of date kernel if a newer one didn't work properly in your hardware for some reason, (that's rare, but it can happen). :)

---

