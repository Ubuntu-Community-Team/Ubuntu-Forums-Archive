---
title: "Help with grub looping when selecting Vista"
date: 2008-08-25
forum: General Help
---

### Post by mdupontm on 2008-08-25
Hey there everyone, I recently installed a new theme which require me to make a few mods (one of which was switching to grub gfx) Anyways, everything was working great until I had to restart into Vista (I'm dual booting). The problem happens here; when I choose vista in Grub, it just loops back into Grub. All the other drives seem to work fine; I can boot into ubuntu fine, same with my recovery partition. Please help me out! Thanks

shuttehface@buzzKillington:~$ sudo fdisk -l
[sudo] password for shuttehface: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e045244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11587    93072546    7  HPFS/NTFS
/dev/sda2           11588       13505    15406335   83  Linux
/dev/sda4           13506       14593     8739360    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d25cce5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

---

### Post by spiderbatdad on 2008-08-25
you might include /boot/grub/menu.lst with your post, so we can verify it maps to (hd1,2)

---

### Post by mdupontm on 2008-08-25
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

gfxmenu (hd0,0)/boot/grub/message.aqua

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=077131c4-8627-4a47-89f9-fef132f76186 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=077131c4-8627-4a47-89f9-fef132f76186 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista/Longhorn (loader)
root		(hd0,3)
savedefault
makeactive
chainloader	+1

---

### Post by spiderbatdad on 2008-08-25
so this doesn't correspond to what you have in fstab. Though it looks like the mbr is on the first disk, which is good. In fstab sda would correspond to (hd0) and sdb (hd1). I think what you need is to map the drive...I can look around some, or maybe someone will chime in. I no expert at it, and have never had the need, so I don't have it right off, but it looks something like:
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by mdupontm on 2008-08-25
alright well if you guys can walk me through step by step as to what commands I should be entering. Thanks

---

### Post by spiderbatdad on 2008-08-25
have you installed startup manger from synaptic package manager? It might be the easiest fix. It's a gui utility for working with grub. I think it installs to the System>>Administration menu.

---

### Post by mdupontm on 2008-08-25
hi, I looked at startup manager but it doesnt seem to have anything that would change what is happening.

---

### Post by caljohnsmith on 2008-08-25
Are you able to boot OK into Ubuntu? Because if you can, then using (hd0,0) or (hd0,3) would be correct for your Vista, depending on which of those partitions is really your Vista. So which partition is your Vista OS? I would assume the first one (hd0,0), since it has the boot flag set.

I think I know what happened to you: at some point, maybe when your originally installed Ubuntu, or when you went to fix Grub, you accidentally installed Grub to the boot sector of your Vista partition. You would have done that by doing:
```
grub> setup (hd0,0)
```
When you really meant to install Grub to the MBR:
```
grub> setup (hd0)
```

If that is the problem, you can use a [Vista Recovery CD]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") and just run the following command from the command line:
```
bootrec /fixboot
```

---

### Post by mdupontm on 2008-08-25
yea the vista partition is (hd0,0). What about if I dont have the Vista Recovery CD ????

---

### Post by caljohnsmith on 2008-08-25
> **mdupontm said:**
> yea the vista partition is (hd0,0). What about if I dont have the Vista Recovery CD ????
If you click the "Vista Recovery CD" in my previous post, you will see it is a link to where you can download that CD. :)

---

