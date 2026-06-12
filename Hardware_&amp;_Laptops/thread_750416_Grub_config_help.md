---
title: "Grub config help"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by LieToPurify3 on 2008-04-09
I have ubuntu installed on one partition and on the other partition i had dsl installed but just switched to DeLi.  However, now my grub wont load.  I have 3 partitions, hda1 is now DeLi, hda2 is xubuntu, and hda5 is my swap.  i can usually just look at the menu.lst that the new OS comes with and add lines to it so that my ubuntu and deli partitions will be listed, but in DeLi linux, there is no /boot/grub directory.  It just has /boot and inside are the files: boot.0301, vmlinuz-2.4.34.4, vmlinuz-2.4.34.4-scsi, and a few others that dont look relevant.  How can I fix my grub and put DeLi into it?  I can access all partitions by booting a live cd of DSL.  I havent been able to boot from hd since my DeLi install.  I have my menu.lst from before i installed DeLi if that helps.

---

### Post by LieToPurify3 on 2008-04-09
i fixed the grub error and am able to boot into xubuntu, but trying to boot into DeLi gives me an error.  

Here's part of my menu.lst

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5709d448-34c9-4b3d-b517-2dc212b4121e ro pnpbios=off quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5709d448-34c9-4b3d-b517-2dc212b4121e ro pnpbios=off single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title DeLi Linux
kernel /boot/vmlinux-2.4.34.4 root=/dev/hda1

i'm not sure what to change with the Deli part.  that seems to be my only problem

---

### Post by dabl on 2008-04-09
Try adding the "root" and "initrd" lines to the DeLi stanza, so it looks like this:
```

title DeLi Linux
kernel /boot/vmlinu[COLOR="red"]x[/COLOR]-2.4.34.4
root (hd0,0)
initrd /boot/initrd.img-2.6.34-4-[COLOR="Red"]{whatever it is}[/COLOR]
```

Where I colored the "x" red, you need to find out whether it is really an "x" or the more common "z" and make the Grub menu entry match the actual kernel name.

You need to take a look at the initrd.img file for DeLi and get the rest of the name for it exactly as it is in its own /boot diretory.  :)

---

### Post by LieToPurify3 on 2008-04-09
i added the root line like you have it, but in the /boot directory for DeLi, there are no initrd files.  There are only: boot.0301 (which seems to have nothing in it), map, system.map, vmlinuz-2.4.34.4, and vmlinuz-24.34.4-scsi.  I see you highlighted teh X in "vmlinux", but in the folder, it's named "vmlinuz-..."

---

