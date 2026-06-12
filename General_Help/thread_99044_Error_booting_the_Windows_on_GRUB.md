---
title: "Error booting the Windows on GRUB"
date: 2005-12-04
forum: General Help
---

### Post by filipenetto on 2005-12-04
Hi guys, how you doing ?

I'm a new user of Linux and Ubuntu, and I'm Brazilian, so, sorry about my bad english ... :???: 

Well, I just want to know how I make to GRUB boot correctly the Windows. The situation is that:

I have installed the Ubuntu on a hard disk and, after, I put other disk with Windows XP. So, this is not listed on GRUB. Seaching on the forum, I found the instructions to add the Windows to GRUB, and my 'menu.lst' file stay that:

[I][COLOR="DimGray"]title      Ubuntu, kernel 2.6.12-10-386
root      (hd0,0)
kernel      /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd      /boot/initrd.img-2.6.12-10-386
savedefault
boot

title      Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root      (hd0,0)
kernel      /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd      /boot/initrd.img-2.6.12-10-386
boot

title      Ubuntu, kernel 2.6.12-9-386
root      (hd0,0)
kernel      /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd      /boot/initrd.img-2.6.12-9-386
savedefault
boot

title      Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root      (hd0,0)
kernel      /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd      /boot/initrd.img-2.6.12-9-386
boot

title      Ubuntu, memtest86+
root      (hd0,0)
kernel      /boot/memtest86+.bin 
boot

title      Windows XP Professional
root      (hd1,0)
savedefault
makeactive
chainloader   +1[/COLOR][/I]

But, in this way, is not working. When I try to boot the Windows, it show this error message:

[I][COLOR="DimGray"]Boting Windows XP Professional
root      (hd1,0)
      Filesystem type unknown
      Partition type 0x7
makeactive
chainloader   +1[/COLOR][/I]

Somebody know what is happening ? 

Obs: I have an HD on the primary master with the Ubuntu, and the Windows is on the first partition on a HD in primary slave.

I hope somebody can help me ... Thanks !!!

---

### Post by amohanty on 2005-12-04
```
title Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1

```

Unfortunately windows does not like being on the second drive or partition. I wil fail to boot.
You can use the map directive to fix this like so:

```

title Windows XP Professional
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

```

This makes Windows believe its booting off the first partition of the primary HDD.

HTH
AM

---

### Post by SilentCacophony on 2005-12-04
The map commands should be used any time Windows is on a non-first drive or partition.

If you still have trouble after changing it as outlined above, it may also be helpful to try changing the **root** command to **rootnoverify**, although I'm not sure that it would apply to your case. I seem to remember having to use it once for a similar error, though.

---

### Post by filipenetto on 2005-12-07
Beautiful !!!!

This make works. Thank you very much ..... :p

---

