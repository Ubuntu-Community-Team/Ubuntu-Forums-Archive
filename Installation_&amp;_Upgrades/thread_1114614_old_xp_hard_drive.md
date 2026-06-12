---
title: "old xp hard drive"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by quik_joe on 2009-04-02
I built my parents a new computer and installed ubuntu 8.10 on it, however my dad likes to play games and my sister likes to use windows office, and they don't know much about linux. I was just wondering if it was possible to take the old xp hard drive out of their old computer and install it in the new computer i built, and maybe do a dual boot ubuntu/xp. any information would help, as i don't know much about linux either.

---

### Post by spcwingo on 2009-04-03
You should be able to just slave the XP disk, then boot back into Ubuntu and run these commands:

```
sudo fdisk -l
```

This will tell you what to put in your GRUB menu.lst.  Edit grub with this command:

```
gksu gedit /boot/grub/menu.lst
```

scroll down until you see something that looks like this:

```
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro xforcevesa quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro xforcevesa quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

and edit so it looks something like this:

```
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro xforcevesa quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro xforcevesa quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Microsoft Windows XP
root		[COLOR="Red"](hd1,0)[/COLOR]
savedefault
makeactive
chainloader	+1
```

The part highlighted in red above shows where you put the information gathered from fdisk -l.  Just remember that grub counts 0 as the first so if your output from from fdisk -l is:

```
/dev/sdb1
```

for your XP drive then the highlighted area above will be correct.  Alternately, if the output is:

```
/dev/sdc2
```

the entry will be:

```
(hd2,1)
```

I hope this helps.

---

### Post by dandnsmith on 2009-04-03
I think something has been forgotten - in a new set of hardware the Windows configuration will be all wrong. It is possible to fix it, sometimes, but often a re-install is the only practicable way.

---

### Post by Mark Phelps on 2009-04-03
> **quik_joe said:**
> I was just wondering if it was possible to take the old xp hard drive out of their old computer and install it in the new computer i built

Possible -- yes.  Working -- probably not.  

The "old" XP installation includes the motherboard and hardware drivers associated with that machine.  Unless the new motherboard is identical, along with the hardware, it's likely that XP either won't run or it will fail in some way.

You can help prevent this to a degree by uninstalling all the hardware drivers in the old machine (including video) before moving the drive.  But then, you will have to install the motherboard and hardware drivers anew in the new machine.  So, unless you have an XP install CD for the new machine, you will have to hunt down drivers for it.

---

