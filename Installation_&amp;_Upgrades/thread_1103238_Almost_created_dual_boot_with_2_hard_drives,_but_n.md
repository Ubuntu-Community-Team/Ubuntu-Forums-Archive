---
title: "Almost created dual boot with 2 hard drives, but no LILO!"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by stir-crazy on 2009-03-22
So help me out here, at this point, how do I fix this.

I have a primary 20GiB HDD with WinXP on this machine, it does have a 90 MB partition of free space.

I installed UE 8.04 on a 40GiB slave drive, and all seems right.  Except I don't have a LILO selection at startup, and I'm stuck with Windows for the time being.

Any ideas on what I can do to fix this?  TIA!

---

### Post by upchucky on 2009-03-22
since you indicate a separate physical drive for each os, you will need to use the bios to be able to boot to different drives. if this is what you wanted then disconnect the windows drive, put in the ubuntu live cd and have it repair the MBR of the Ubuntu drive. reconnect the windows drive and enable the bios booting. now each os will boot depending on which one you select each time you start the machine.

it may very well be that ubuntu is already bootable by selecting it in the bios at startup, try it first.

if this is not the boot scenario that you intended then you need to use the live cd to install grub on the ubuntu drive and add the windows info to /boot/grub.menu.lst so it can boot either os.


below is my menu.lst it is a sample, and the drive geometry will be different from yours so you can not use it, however it serves as a reference of what to expect.



title		Ubuntu 8.04, kernel 2.6.24-16-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-386
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd		/boot/initrd.img-2.6.24-16-386


title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by stir-crazy on 2009-03-22
So, from the sounds of things, I'd have to either use BIOS to select which OS I'm going to run each time (sounds like a pain, and I'm not altogether sure it would work with this IDE setup), OR, swap out which drive is Master and Slave, adding Windows to the GRUB menu of the Ubuntu drive.  The latter sounds doable, but darn...I am so sick of cracking that case open on this machine!  Will give that a try later on tonight.

---

### Post by meierfra. on 2009-03-22
> So, from the sounds of things, I'd have to either use BIOS to select which OS I'm going to run each time (sounds like a pain, and I'm not altogether sure it would work with this IDE setup)


No. You only have the change the boot order in the bios once. Hopefully  this will give you the Grub menu and you should be able to boot into Ubuntu and XP from the Grub menu.

Even if this does not work out this easily, you should be able to reconfigure grub so that you can boot into both OS's from the Grub menu without having to physically swap the two hard drives.

---

### Post by stir-crazy on 2009-03-22
Not so sure I'd be able to do this without cracking the case and swapping the drives.  Been having troubles with this machine the past few weeks, and just got the jumpers on these drives cooperating...will play with BIOS and see if it simply lets me boot first from the Slave, but I'm not too hopefull.

---

### Post by meierfra. on 2009-03-22
> Not so sure I'd be able to do this without cracking the case and swapping the drives. Been having troubles with this machine the past few weeks, and just got the jumpers on these drives cooperating...will play with BIOS and see if it simply lets me boot first from the Slave, but I'm not too hopefull.

If you can't change the boot orders in  the bios, boot from the Ubuntu LiveCD, open a terminal "Applications->Accessories->Termimal" and post the output of

```
sudo fdisk -lu
```

Then I can give you instructions how to install grub to the MBR of your boot drive. (I'm pretty sure that this can be resolved without having to swap drives)

---

