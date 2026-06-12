---
title: "Vista MBR, BSD's fault, Grub"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by samfuqua on 2009-05-26
Okay, so it's actually my fault for not reading all the way through the docs first.

Anyways, I had an install of 9.04 that was an upgrade from 8.10 dual-booted with Vista without any trouble.  I decided to give FreeBSD a try and so I ghosted my 9.04 partition and deleted it, made a new partition, and put FreeBSD on it.  I installed the BSD bootloader and MBR, which messed up my Vista partition.  It's still there, it's just not booting.  I deleted FreeBSD and re-ghosted my 9.04 partition onto it.  Then I popped in a liveCD, chrooted my 9.04 install and put grub back.  Now, as I expected, I have grub and can't boot my Windows partition.  I have ms-sys installed, but I'm not sure what to do with it because I've read that it reams grub.  So do I restore my Vista MBR and then reinstall GRUB?  Can someone help?  
I'm a pretty experienced user, I just don't want to mess up my Vista partition.

---

### Post by Mark Phelps on 2009-05-27
The simplest and easiest way to restore the Vista MBR is to boot from a Vista DVD and run Startup Repair.

If you don't have such a DVD, you can use torrent to download an image from the NeoSoft forums.

I've read that the SuperGrubDisk can rewrite an MS Windows MBR but I've not actually tried it.  You could download that, burn it, and give it a try.

---

### Post by coffeecat on 2009-05-27
> **samfuqua said:**
> Then I popped in a liveCD, chrooted my 9.04 install and put grub back.  Now, as I expected, I have grub and can't boot my Windows partition.

Some questions:

Exactly how did you 'put grub back' with a chroot? Normally after you've restored a Linux image back to a partition and you need to restore grub to the mbr, all you have to do is invoke grub from a live CD terminal - you don't actually need to chroot.

When you say you have grub and can't boot Windows, do you mean...

... there's no Windows entry on the grub menu? Or...

... there is a Windows choice but when you select it, Windows fails to boot up?

And, can you boot up into your 9.04 installation OK?

Perhaps you'd better post the contents of your /boot/grub/menu.lst (use the live CD to access it if you can't boot into Ubuntu), and the output of:

```
sudo fdsik -l
```

---

### Post by samfuqua on 2009-05-27
Forget what I said about chrooting.  I have since restored grub using a livecd.  What I mean by "Windows won't boot" is that there's an entry, but selecting instantly reboots my computer, bringing up the grub menu again.

Here's the fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1433    11510541    7  HPFS/NTFS
/dev/sda2   *        1434       12991    92838452    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           12992       19457    51938145    5  Extended
/dev/sda5           12992       13112      971901   82  Linux swap / Solaris
/dev/sda6           18087       19457    11012526   83  Linux
/dev/sda7           13113       18086    39953623+  83  Linux

Partition table entries are not in disk order


Here's the menu.lst:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=92c5b7f7-e4e9-42d8-a060-4abd3f3f117a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=92c5b7f7-e4e9-42d8-a060-4abd3f3f117a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		92c5b7f7-e4e9-42d8-a060-4abd3f3f117a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=92c5b7f7-e4e9-42d8-a060-4abd3f3f117a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		92c5b7f7-e4e9-42d8-a060-4abd3f3f117a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=92c5b7f7-e4e9-42d8-a060-4abd3f3f117a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		92c5b7f7-e4e9-42d8-a060-4abd3f3f117a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=92c5b7f7-e4e9-42d8-a060-4abd3f3f117a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		92c5b7f7-e4e9-42d8-a060-4abd3f3f117a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=92c5b7f7-e4e9-42d8-a060-4abd3f3f117a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		92c5b7f7-e4e9-42d8-a060-4abd3f3f117a
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
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by samfuqua on 2009-05-27
Oh, and where it says that the partitions are out of order, that's because the order is sda5,sda7,sda6.  I moved my sda6 to the end of the disk before I created sda7.

---

### Post by coffeecat on 2009-05-29
These are the interesting bits:

> **samfuqua said:**
> Here's the fdisk -l:

<snip>

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1433    11510541    7  HPFS/NTFS
/dev/sda2   *        1434       12991    92838452    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

and

> **samfuqua said:**
> Here's the menu.lst:

<snip>

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
chainloader    +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1

There are two Vista/NTFS partitions. I guess sda1/(hd0,0) is a manufacturer's restore partition and sda2(hd0,1) is the Vista C:\ partition. Just so that we're clear, when you say that selecting the Windows entry causes the computer to reboot immediately, which entry are you referring to, the first or second? If I'm right about sda1 being a restore partition, then if everything were working properly selecting the first should boot you into the restore utility and the second should boot you into Vista.

Anyway, there are two things that may or may not be relevant.

Partition 2 doesn't end on a cylinder boundary. Vista is much more fussy about its C: partition than ever XP was. If it was booting OK before with the partition not on a cylinder boundary then this is a red-herring. But if this is new change then this might be relevant.

The second thing is that partition 2 has the boot flag (as you'd expect) and entry 2 in menu.lst has the makeactive command (which sets the boot flag). But the entry for partition 1 doesn't have the makeactive command so, depending on how the manufacturer set the restore partition up, you may or may not be able to boot into it. But that's for the restore partition so, if you're trying to boot from the second entry, this isn't relevant. But if you're selecting the first entry then *maybe* the lack of both a boot flag and a makeactive command is leading to the instant reboot. Maybe - I'm theorising; I wouldn't know without experimenting.

The only other thing I can suggest is that, if you've got access to a "proper" Vista install DVD, you could try booting into it, select the repair utility and try to repair the Vista C: partition. If you haven't, you may or may not be lucky with the restore partition (if you can actually boot into it). Some (most?) manufacturer's restore partitions only let you restore a factory setup image, so you lose all your updates, settings and applications. But the restore partition on my Sony Vaio has some repair utilities. You might be lucky.

---

