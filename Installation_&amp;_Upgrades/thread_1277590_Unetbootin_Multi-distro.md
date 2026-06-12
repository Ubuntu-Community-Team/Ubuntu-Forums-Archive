---
title: "Unetbootin Multi-distro"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by libertypilot on 2009-09-28
So I'm trying to edit my syslinux.cfg file created by unetbootin so that I can have one USB Flash drive that essentially has multiple live cds on it. So far, I have successfully gotten Xubuntu (which was originally installed by unetbootin) and Puppy Linux to work properly.

The problem I seem to run into is the kernel loads fine for each distro, but then when it begins to look for its own files it doesn't know where to find them. I've seperated them into their own folders, and anywhere that an original isolinux.cfg file pointed to the kernel at say, /vmlinuz I have replaced that with its actual location on the USB -> e.g. /puppy/vmlinuz

An example of the problem that I get when I try to boot antix:
"Can't find MEPIS filesystem, sorry."

Linux mint simply drops to a command-line shell without any error message.

I'm guessing what I really need to do is somehow make each distro think its folder is the root filesystem?
I know there's a line in some of the distros APPEND "root=....." but I'm not sure how it works and hesitant to mess with it. Plus puppy linux seems to work just fine without any sort of command.

Any ideas what I can do to fix my syslinux.cfg file?

Here's my syslinux.cfg:
```

DEFAULT     vesamenu.c32
PROMPT         0
MENU TITLE     UNetbootin
TIMEOUT     100

LABEL         unetbootindefault
MENU LABEL     Xubuntu 9.04 (Default)
KERNEL         /ubnkern
APPEND         initrd=/ubninit file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash --

LABEL         puppy
MENU LABEL     Puppy Linux
KERNEL         /puppy/vmlinuz
APPEND         initrd=/puppy/initrd.gz pmedia=cd

LABEL         dsl
MENU LABEL    Damn Small Linux
KERNEL         /dsl/boot/isolinux/linux24
APPEND         ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=/dsl/boot/isolinux/minirt24.gz nomce noapic quiet BOOT_IMAGE=knoppix

LABEL         moblin
MENU LABEL     Moblin 2.0
KERNEL         /moblin/isolinux/vmlinuz0
APPEND         initrd=/moblin/isolinux/initrd0.img root=CDLABEL=2.0-final-x86_64-200909232135 rootfstype=iso9660 ro liveimg quiet 

LABEL         linuxmint
MENU LABEL     Linux Mint 7
KERNEL         /mint/casper/vmlinuz
APPEND      file=/mint/preseed/mint.seed boot=casper initrd=/mint/casper/initrd.gz quiet splash --

LABEL        gentoo
MENU LABEL    Gentoo
KERNEL        /gentoo/isolinux/gentoo
APPEND        root=/dev/ram0 init=/linuxrc  dokeymap looptype=squashfs loop=/gentoo/image.squashfs  cdroot initrd=/gentoo/isolinux/gentoo.igz vga=791

LABEL        antix
MENU LABEL    AntiX M8.2
KERNEL        /antix/boot/vmlinuz
APPEND        initrd=/antix/boot/initrd.gz
```

EDIT: It would seem that the problem is since these files were pulled directly from the iso, they are looking for a CD to boot from. For example, Gentoo gives me the following:

```
>>Looking for the cdrom
>>Attempting to mount media:- /dev/sda1
!! Media not found
>> No bootable medium found. Waiting for new devices
>> Looking for the cdrom
>> Attempting to mount media:- /dev/sda1
!! Media not found
!! Could not find CD to boot, something else needed!
>> Determining root device...
!! Could not find the root block device in .
```

---

### Post by giuseppe105 on 2010-01-31
Its a shame this was posted in September of 09 and no one said anything about this.

@libertypilot if you are still working on this problem I am also trying to figure out why it cant find the file system.

Did you solve the problem?

---

### Post by elatre on 2010-03-06
I solved this for SystemRescueCD with the parameter "subdir". My menu.lst file (I use grub) contains the following:

```
title SystemRescueCd 32bit
root	(hd0,0)
kernel	/sysrcd/rescuecd subdir=sysrcd setkmap=de
initrd	/sysrcd/initram.igz
```
I learned this hier: [http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk](http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk)

---

