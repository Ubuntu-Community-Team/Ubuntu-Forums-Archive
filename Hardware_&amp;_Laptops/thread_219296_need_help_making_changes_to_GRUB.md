---
title: "need help making changes to GRUB"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by ironfistchamp on 2006-07-19
Hey all I have a slight problem I hope you can help me with.

I dual boot Ubuntu and XP. After XP died I reinstalled. I have done this many times and have been able to reinstall GRUB using a live cd no probs. This time however XP detected an unknownOS. When I went to reinstall grub everything seemed fine until I tried to get into windows. Can someone help me fix my GRUB to get into both Lin and Win? 

Thanks

Ironfistchamp

Here is the useful bit of my menu.lst file (I think)

title		Ubuntu, kernel 2.6.15-26-686
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot

#title		Ubuntu, kernel 2.6.15-26-386
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-26-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-26-386
#boot

title		Ubuntu, kernel 2.6.15-25-686
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-686 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-686 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-686 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-25-686
boot

#title		Ubuntu, kernel 2.6.15-25-386
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-25-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-25-386
#boot

#title		Ubuntu, kernel 2.6.15-23-686
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-23-686
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-23-686
#boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

#title		Ubuntu, kernel 2.6.15-22-386
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-22-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-22-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-22-386
#boot

#title		Ubuntu, kernel 2.6.15-21-386
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-21-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-21-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-21-386
#boot

#title		Ubuntu, kernel 2.6.15-20-386
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-20-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-20-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-20-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-20-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-20-386
#boot

#title		Ubuntu, kernel 2.6.15-19-386
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-19-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-19-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-19-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-19-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-19-386
#boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I have commented out the other entries on purpose.

---

### Post by zxee on 2006-07-19
What response do you get from grub when you try to boot windows?
You could try rootnoverify in place of root for your xp grub entry and see if that boots xp.

---

