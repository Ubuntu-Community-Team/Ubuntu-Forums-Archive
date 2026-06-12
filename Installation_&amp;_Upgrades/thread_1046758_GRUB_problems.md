---
title: "GRUB problems"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by Cyber Akuma on 2009-01-21
I multi-boot my system, the latest OS I installed was OpenSUSE, mainly because every distro picket I tried recommended either that or Ubuntu, and I wanted to try both.

However, despite OpenSUSE's installer finding my grub config files on the Ubuntu partition and me telling it not to mess with it..... it went ahead and installed it's own version of GRUB anyway... with Ubuntu and Windows options that do not work.... (which worked perfectly with the version of Grub that Ubuntu configured)

The graphical one is nice.... but im sure if I cared I could install a graphical version of GRUB on my own.

Now.... I already know how to reinstall GRUB for Ubuntu as i've done it before several times when another os messes up or writes it's own bootloader.... but I don't know how to add an option to make it successfully boot OpenSUSE if I pick it.

I tried to open the menu.lst file in the OpenSUSE partition to see what the GRUB commands were, but it refused to allow me to open it even with root permissions.

And this brings me to another problem..... if there any way to make this file auto-update if openSUSE updates something that mandates a change in GRUB? (Like how Ubuntu updates it when it updates the kernel)

.... and is there any way to even make Ubuntu auto-update it when the kernel is updated? Since I had to manually edit it to add some of my other OSes as well as layout the menu the way I prefer Ubuntu can no longer auto-update it's own menu.lst file for GRUB, its annoying to manually update it every time the kernel is changed.

---

### Post by Kaneda187 on 2009-01-21
I also have a problem with grub sounds rather similar I installed fedora to try it out and it got rid of my option to boot ubuntu, i can still get into the ubuntu partition so i was thinking if i find the grub config file tthen i could bring it over to fedoras grub config and some how make them all get along....ya think this is possible?

---

### Post by Kaneda187 on 2009-01-21
it aint looking good:(

---

### Post by Cyber Akuma on 2009-01-21
Well, I was able to get everything working again through Ubuntu's grub, but I would still like to know about auto-updating the config file.

---

### Post by caljohnsmith on 2009-01-21
Never mind if you have it working now.

---

### Post by SkyLeach on 2009-01-21
many of these issues and problems can be avoided by having a boot partition.  I generally keep a 100MB boot partition right after my windows partition (or at partition 1 if it is a linux-only system) formated as ext3.

I keep a gentoo livecd for x86 and amd64 both (2 keys, 1GB each) that I have modified according to my needs, but you can generally get by with any decent livecd/usb for this.  Typically when having bootloader problems I don't want to wait for a whole gui environment to load.

in the case of gentoo, I boot like so:
gentoo-nofb nox noacpi apic=off

This disables framebuffers, disables loading of the xserver, turns off power managemnt including on uniprocessor systems.  it's faster than the other options and safer since many problems are related to power management and/or unstable framebuffer code.

having reached a stable shell, I then can mount my bootloader reliably with:

mkdir /mnt/boot
mount -t ext3 /mnt/boot

I generally set up grub for any given linux distribution to boot /boot/vmlinuz root=/dev/sda3 (or /dev/sda1 or /dev/hda1, etc... depending on where your root partition is)

whenever you run make install with the kernel it creates a symlink from /boot/vmlinuz to whatever kernel you have just installed.

in the grub.conf file, I generally set up boot=0 and fallback=2 (the most recent stable build)

an example of my graphical grub configuration:
```

# http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2
# If you are not using Genkernel and you need help creating this file, you
# should consult the handbook. Alternatively, consult the grub.conf.sample that
# is included with the Grub documentation.

default 2
fallback 3
timeout 30
splashimage=(hd1,0)/boot/grub/splash.xpm.gz

title Gentoo Linux default
root (hd1,0)
kernel /boot/vmlinuz root=/dev/hdb3

title Gentoo Linux 2.6.28-gentoo
root (hd1,0)
kernel /boot/vmlinuz-2.6.28-gentoottvn-matt root=/dev/hdb3

title Gentoo Linux 2.6.27-gentoo-r7
root (hd1,0)
kernel /boot/vmlinuz-2.6.27-gentoo-r7ttvn-matt root=/dev/hdb3

title Gentoo Linux 2.6.26-gentoo-r4
root (hd1,0)
kernel /boot/vmlinuz-2.6.26-gentoo-r4ttvn-matt root=/dev/hdb3

title Gentoo Linux 2.6.25-gentoo-r9
root (hd1,0)
kernel /boot/vmlinuz-2.6.25-gentoo-r9ttvn-matt root=/dev/hdb3

title Gentoo Linux 2.6.25-gentoo-r8
root (hd1,0)
kernel /boot/vmlinuz-2.6.25-gentoo-r8ttvn-matt root=/dev/hdb3

title Gentoo Linux 2.6.25-gentoo-r7
root (hd1,0)
kernel /boot/vmlinuz-2.6.25-gentoo-r7ttvn-matt root=/dev/hdb3

title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

#initrd /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5
# vim:ft=conf:

```

on this system, /dev/sda1 is windows xp (ntfs) and /dev/sda2 is partitioned for linux (reiserfs format)

the second disk is configured with the partitions laid out as I suggested before, with a boot partition for all of the installed distros:
```

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
16 heads, 63 sectors/track, 77504 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x9a5d65a2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         195       98248+  83  Linux
/dev/hdb2             196        2180     1000440   82  Linux swap / Solaris
/dev/hdb3            2181       77504    37963296   83  Linux

```

Notice the 50M boot partition at the start of the second disk.

Anyhow, I know that this isn't standard for Ubuntu installs but I hope it sheds some light on how to intelligently install multiple distros.  In general, keep a boot partition and share it between all distros as it is very easy to maintain by hand.

---

### Post by Herman on 2009-01-22
> Well, I was able to get everything working again through Ubuntu's grub, but I would still like to know about auto-updating the config file. Ubuntu is based on Debian and like other Debian based distros, we have a special section added in the middle of our /boot/grub/menu.lst files called the 'Debian Automagic Kernels List'.

The Debian automagic kernels list is special because it remembers the GRUB settings we have in our menu.lst file and helps the update-grub script make us a new menu.lst whenever there's a kernel update. Every time a new kernels is installed during an internet update, the update-grub script is run automatically, and that adds the latest kernel to the top of our GRUB menu. We can still scroll down the list and boot an older kernel instead if there's some reason why we need to.

When we're editing our /boot/grub/menu.lst files, the beginning and end of out Debian automagic kernels lists are marked in upper case letters.
They look like: 

[### BEGIN AUTOMAGIC KERNELS LIST]("http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST")
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

and

[### END DEBIAN AUTOMAGIC KERNELS LIST]("http://users.bigpond.net.au/hermanzone/p15.htm#END_DEBIAN_AUTOMAGIC_KERNELS_LIST")
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

It's okay to edit things in between those two markers if we know what we're doing. 
We need to edit important changes in there to make various things persistent over kernel updates.
However, it is not advisable to insert entries for foreign operating systems within the Debian Automagic kernels list area. :)


I agree with SkyLeach, you may be interested in making a 'Dedicated GRUB Partition'.
[Making a Dedicated Grub Partition]("http://www.troubleshooters.com/linux/grub/grubpartition.htm") - by Steve Litt - original source

[How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").- by me, (more Ubuntu-specific).

The reason why I like to use the term 'Dedicated GRUB Partition' instead of just 'boot partition', is to make sure people know the difference between a 'Dedicated GRUB Partition' and a 'Separate /boot Partition'.

A 'Separate /boot Partition' is normally created with the installer at installation time and it's mainly for old computers whose BIOSes can't map more than say 8.45 GB of their hard drives, (around ten years old or older), so they won't get 'GRUB Error 18'. It contains the operating system's kernel, and 'fences it in' to within the first 8 1/2 GB, where the BIOS can 'see' it. The 'Separate /boot Partition' belongs to an operating system and it isn't easy to share one with another distro.

A 'Dedicated GRUB Partition' doesn't have any Linux kernel in it, (not necessarily anyway), can be located anywhere on the hard disk, and is 'operating system independant'. It contains only GRUB files (usually), and is useful for multi-booting.
It can be chmodded with relaxed file permissions to make it easier to edit the menu.lst file. 

You can use 'symlink' style boot entries, like SkyLeach is suggesting, or re-install each operating system's GRUB to it's own partition boot sector, and use chainloader commands, whichever you prefer.
You can also use configfile commands, but now there are getting to be some problems with those because of changes to some operating system's GRUB commands and also file system changes, so the other two kinds of boot entrys are now more advisable.
[Operating System entries for multibooting other Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

Regards, Herman :)

---

