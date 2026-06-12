---
title: "Attempt to create multiboot DVD: Mostly failed"
date: 2008-08-16
forum: General Help
---

### Post by claw_atticas on 2008-08-16
I've been wanting to try out a variety of Linux OSes and user interfaces, but I didn't want to have to waste a whole bunch of CDs on all the distros I downloaded... So I decided to use ISOLinux, but couldn't find any step-by-step instructions, so I examined the code (Seemed simple enough), and decided to work at it on my own...
Current attempts at Linux OSes: Ubuntu, Kubuntu, Xubuntu, Fluxbuntu, Linux Mint, Linux Mint KDE, Linux Mint XFCE, Mandriva, Mandriva KDE, OpenSuSE, OpenSuSE KDE, Zenwalk Linux, DSL, PCLinuxOS, and Puppy Linux across 3 DVDs
Fluxbuntu, Ubuntu, Kubuntu, Xubuntu, Linux Mint, Linux Mint KDE, Fedora, 
I uncompressed all the ISO files into their own directories (puppy, mandriv, mandrivk, opensuse, opensusk, etc, etc), copied an ISOLinux directory to what would become each DVD's root, and rewrote each isolinux.cfg

DVD1
```
DEFAULT /flux/install/vmlinuz
GFXBOOT bootlogo
LABEL flux
  menu label ^Install Fluxbuntu 7.10
  kernel /flux/install/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed initrd=/install/initrd.gz quiet --
LABEL ubuntu
  menu label ^Start Ubuntu 8.04.1
  kernel /ubuntu/casper/vmlinuz
  append  file=/ubuntu/cdrom/preseed/ubuntu.seed boot=casper initrd=/ubuntu/casper/initrd.gz quiet splash --
LABEL kubuntu
  menu label ^Start Kubuntu 8.04.1 with KDE4
  kernel /kubuntu/casper/vmlinuz
  append  file=/kubuntu/cdrom/preseed/kubuntu-kde4.seed boot=casper initrd=/kubuntu/casper/initrd.gz quiet splash --
LABEL xubuntu
  menu label ^Start Xubuntu 8.04.1
  kernel /xubuntu/casper/vmlinuz
  append  file=/xubuntu/cdrom/preseed/xubuntu.seed boot=casper initrd=/xubuntu/casper/initrd.gz quiet splash --
label live
  menu label ^Start Linux Mint 5.0 Elyssa
  kernel /mint/casper/vmlinuz
  append  file=/mint/cdrom/preseed/mint.seed boot=casper initrd=/mint/casper/initrd.gz quiet splash --
LABEL mintkde
  menu label ^Start Linux Mint 4.0 KDE CE
  kernel /mintkde/casper/vmlinuz
  append  file=/mintkde/cdrom/preseed/ubuntu.seed boot=casper initrd=/mintkde/casper/initrd.gz ramdisk_size=1048576 root=/mintkde/dev/ram rw quiet splash --
LABEL mintxfce
  menu label ^Start Linux Mint 4.0 XFCE CE Beta 008
  kernel /mintxfce/casper/vmlinuz
  append  file=/mintxfce/cdrom/preseed/ubuntu.seed boot=casper initrd=/mintxfce/casper/initrd.gz quiet splash --
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
```

DVD2
```
DEFAULT fedora
GFXBOOT bootlogo
LABEL fedora
  menu label Start Fedora 9 GNOME
  kernel /fedora/isolinux/vmlinuz0
  append initrd=/fedora/isolinux/initrd0.img root=CDLABEL=Fedora-9-Live-i686 rootfstype=iso9660 ro quiet liveimg rhgb 
LABEL fedorak
  menu label Start Fedora 9 KDE
  kernel /fedorak/isolinux/vmlinuz0
  append initrd=/fedorak/isolinux/initrd0.img root=CDLABEL=Fedora-9-Live-KDE-i686 rootfstype=iso9660 ro quiet liveimg rhgb 
LABEL mandriv
  menu label Start Mandriva Linux One 2008 Spring
  kernel /mandriv/boot/vmlinuz
  append initrd=/mandriv/boot/cdrom/initrd.gz splash=silent vga=788 
LABEL mandrivk
  menu label Start Mandriva Linux One 2008 Spring KDE
  kernel /mandrivk/boot/vmlinuz
  append initrd=/mandrivk/boot/cdrom/initrd.gz splash=silent vga=788 
LABEL opensuse
  menu label Start OpenSuSE 11
  kernel /opensuse/boot/i386/loader/linux
  append initrd=/opensuse/boot/i386/loader/initrd ramdisk_size=512000 ramdisk_blocksize=4096 splash=silent showopts
LABEL opensusk
  menu label Start OpenSuSE 11 with KDE4
  kernel /opensuse/boot/i386/loader/linux
  append initrd=/opensuse/boot/i386/loader/initrd ramdisk_size=512000 ramdisk_blocksize=4096 splash=silent showopts
LABEL zenwalk
  menu label Start Zenwalk Linux
  KERNEL /zenwalk/boot/vesamenu.c32
  APPEND /zenwalk/boot/isolinux/menu_en.cfg
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
```

DVD3
```
DEFAULT dsl
GFXBOOT bootlogo
LABEL dsl
  menu label Start DSL v4.2.5
  kernel /dsl/boot/isolinux/linux24
  append ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=/dsl/boot/isolinux/minirt24.gz nomce noapic quiet BOOT_IMAGE=/dsl/knoppix/knoppix 
LABEL fedorak
  menu label Start Fedora 9 KDE
  kernel /fedorak/isolinux/vmlinuz0
  append initrd=/fedorak/isolinux/initrd0.img root=CDLABEL=Fedora-9-Live-KDE-i686 rootfstype=iso9660 ro quiet liveimg rhgb 
LABEL mintxfce
  menu label ^Start Linux Mint 4.0 XFCE CE Beta 008
  kernel /mintxfce/casper/vmlinuz
  append  file=/mintxfce/cdrom/preseed/ubuntu.seed boot=casper initrd=/mintxfce/casper/initrd.gz quiet splash --
LABEL pclinux
  menu label Start PCLinuxOS 2007
  kernel /pclinux/isolinux/vmlinuz
  append livecd=/pclinux/livecd initrd=/pclinux/isolinux/initrd.gz root=/dev/rd/3 acpi=on vga=788 keyb=us splash=silent fstab=rw,noauto
LABEL puppy
  menu label Start Puppy Linux v4.00 Dingo
  kernel /puppy/vmlinuz
  append initrd=/puppy/initrd.gz pmedia=cd
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
```

The only one that worked was Puppy Linux, most likely because it basically had no directories, just every file in the root directory.
Ubuntu and it's variants (Including the Linux Mints) didn't show an error, just kicked me to the BusyBox Built-in Shell (Under the 'directory' "initramfs")
Fedora and its KDE said "Cannot find root file system!"
DSL said "Can't find KNOPPIX filesystem"
PCLinuxOS said "Unable to mount the livecd"
Mandriva and its KDE couldn't mount its directories (With messages like "error mounting /live/proc", "error mounting /live/sys/)
OpenSuSE and its KDE said "Couldn't find CD image configuation file"
Zenwalk said from GRUB "Could not find kernel image: /install/initrd.gz"
And Fluxbuntu said from GRUB "Could not find ramdisk image: /install/initrd.gz"

My main question: Is it possible to create a multiboot DVD for all of these distros? Or maybe if I could put the .iso files onto the DVD and have isolinux read from those?

---

### Post by claw_atticas on 2008-08-16
Sorry for that little random list of OSes before talking about uncompressing everything (The single line "Fluxbuntu, Ubuntu, Kubuntu, Xubuntu, Linux Mint, Linux Mint KDE, Fedora, "), I was using the message to check over the OSes I had on the DVDs, forgot to erase)

---

