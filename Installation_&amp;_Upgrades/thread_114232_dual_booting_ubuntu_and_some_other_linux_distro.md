---
title: "dual booting ubuntu and some other linux distro"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by oldmanstan on 2006-01-08
Ok, I bought an oldish laptop (PIII 600) and I installed ubuntu on it (then switched to xfce from gnome cuz it's a little speedier) but i'm also wanting to put a different distro on another partition (probably vector linux or something similar) just to fool around with. My problem is that every time I install a second distro either its bootloader wipes out grub (obviously since it goes on the MBR) or I can't boot into the new one cuz grub doesn't see it. I've been messing with it and changed the partitions around to have a separate boot partition. My partition setup is as follows:

/boot
/ (ubuntu root)
unallocated
swap

Anyone got any advice? Or maybe point me to a tutorial? Any help would be great!

---

### Post by Nomearod on 2006-01-08
Did you tried to install first the other distro and then Ubuntu? I tryed something like that, but I installed WinXP first, then Open Suse, and then Ubuntu, and it worked. ( But after some days I formated the HD and installed only WinXP and Ubuntu ).

---

### Post by jon_z on 2006-01-08
I tried forever to edit GRUB to load windows as well, because i installed windows on a second hard drive.. I was unsuccessful, my tip... Install everything first, then clean install Ubuntu... It works flawlessly that way.

---

### Post by Kipper on 2006-01-08
Oldman stan,

The short answer to question is yes, you can certainly have more than one flavour of Linux on a single hard dirve and boot into each using just one version of GRUB installed on the MBR of your disk. 

To do this you need to:

1. When you install additional versions of linux make sure they don't try to install their own version of GRUB to the MBR and overwirte what you already have. Either skip installing a bootloader at all, or install it to the bootsector of a/the partition the new version of Linux is going to be on. Any half-decent distro should allow you to do this.

2. Edit the GRUB's "menu.lst" file of the Ubuntu install to be able to boot the new flavour of linux you have installed.
 
The separate "/boot" partition you have created is only usuable by one distro at a time. It cannot be both used by Ubuntu and another distro at the same time. But you could use it as the place to install the bootloader of any new distro you install as I indicated in point one above.  

Step 2  is carried out post install of your new distro. What you are doing is simply adding another section to your existing GRUB set-up to allow the new distro to be booted. There are plenty of guides on-line about this.

Here's an example to give you an idea what you might end up with.

###################################################
# Grub Boot menu for system where hdd-1 is set as boot drive in BIOS - the master drive on the secondary IDE
# controller. GRUB maps hda as hd0 in this case, and SATA drive as hd1
###################################################
timeout 10
color black/cyan yellow/cyan
default 1

title ide_2.6.11-13mdk_noacpi
kernel (hd0,5)/vmlinuz-2.6.11-13mdk root=/dev/hda1 acpi=ht resume=/dev/hda5
initrd (hd0,5)/initrd-2.6.11-13mdk.img

title ide_2.6.11-13mdk_acpi
kernel (hd0,5)/vmlinuz-2.6.11-13mdk root=/dev/hda1 resume=/dev/hda5
initrd (hd0,5)/initrd-2.6.11-13mdk.img

title SATA_2.6.11-13mdk_acpi
kernel (hd1,7)/vmlinuz-2.6.11-13mdk root=/dev/sda7 resume=/dev/sda6
initrd (hd1,7)/initrd-clb13mdk.img

title ide_bkp
kernel (hd0,11)/vmlinuz-2.6.11-13mdk root=/dev/hda11 noapic nolapic acpi=ht resume=/dev/hda5
initrd (hd0,11)/initrd-2.6.11-13mdk.img

#
title Windows XP
rootnoverify (hd1,0)
hide (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

##########################################

In this case, the machine had two hard drives. PATA set as first boot drive in BIOS. GRUB sees this as hd0. And GRUB is installed on the MBR. The second drive is on a SATA controller and GRUB sees this as hd1. THe second drive has a linux system installed on it where the /boot partition happens to be on sda8, 
in GRUB's notation this ends up being (hd1,7). The "Windows" bit allows a Windows install on the SATA drive to be booted from GRUB installed on the MBR of the PATA drive.

Ok this is a bit more complex than your own case but shows what is possilbe using GRUB as a bootloader, it is very flexible.

---

### Post by lha on 2006-01-08
You can have multiple instances of grub installed. This is handy if you have one distro  you normally use but still want to have other distros to play with.

Here's an example:
Install Ubuntu to hda1, grub on mbr. hda2 will be a swap partition. After that, install your second distro to hda3. Be careful to install grub of for this second distro to the boot sector of hda3 and not to mbr. Add entry to menu.lst that chainloads the second grub. I did this a long time ago and I'm don't remember the exact lines you need in your menu.lst in Ubuntu, but I'd try following:

```
title Alternative GRUB
root (hd0,2)
makeactive
chainloader +1
```

This allows you to freely replace your second distro with another one and you don't have to alter your menu.lst in Ubuntu. Just wipe out hda3 and install a distro of your choice. Also, if you upgrade kernel of your secondary distro, it will likely update menu.lst to contain this new kernel, which becames automatically available to you. If you use only one instance of grub you'd have to manually add new kernels of your secondary distro to menu.lst in Ubunru.

---

### Post by Kipper on 2006-01-08
Lha has posted an interesting alternative. But GRUB's "makeactive" command will only work if the partition is a PRIMARY partition and not an EXTENDED partition. So you could run into a problem with it.

However you do it, you will have to edit your "menu.lst" file at least once.

While it is true that an update of the kenrel in Ubuntu, or other distro(s), will also need a change in the original Ubuntu GRUB "menu.lst" file, this is not always automatic. I have found the Kernel update scripts do not always find your bootloader so you end up making the changes manually. In anycase, it seems sensible to check your boot mechanism has the correct entries in it immediately after a kernel update to ensure the system will re-boot. While you are doing that  you can easily make any changes you need.

---

### Post by oldmanstan on 2006-01-10
excellent! thanks for all the help everyone, I am gonna try to get it working later this week, if i run into any problems i will post again, thanks!

---

