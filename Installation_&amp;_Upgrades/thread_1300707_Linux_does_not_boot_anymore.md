---
title: "Linux does not boot anymore"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by ingmember on 2009-10-25
[FONT=Times New Roman][SIZE=3]Hello![/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I had this GRUB bootloader working well for each Operating System and each OS start-up fine:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Ubuntu 9.04, kernel 2.6.28-11-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ubuntu 9.04, memtest86+[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Other Windows operating systems[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-> Windows 7[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-> Windows Vista (recovery mode)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-> Windows XP[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Debian GNU/Linux, kernel 2.6.26-2-686[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)[/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3]Each Linux and Windows OSs were installed on separate partitions with Vista first, Seven 2nd, XP 3rd, Ubuntu 4th, Debian 5th.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]However I wanted Windows bootloader be in charge, installed EasyBCD, rewrote Windows MBR, installed NeoGrub for Linux, clicked to configure menu.lst of NeoGrub, pasted the details of the GRUB above (see the NeoGrub configuration below), saved, then after reboot I had new Bootloader looking like this:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Windows 7[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Windows Vista (recovery mode)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Windows XP[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]NeoGrub[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-> Ubuntu 9.04, kernel 2.6.28-11-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-> Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-> Ubuntu 9.04, memtest86+[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-> Debian GNU/Linux, kernel 2.6.26-2-686[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-> Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]However when entering the NeoGrub and choosing any Linux to boot I have the following error message on screen:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]For Ubuntu:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Booting 'Ubuntu 9.04, kernel 2.6.28-11-generic'[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=2ebe46ab-c5d8-4f15-a626-0162138d68a3 ro quiet splash[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Error 17: File not found[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Press any key to continue...[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]For Debian:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]root (hd0,7)[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Filesystem type is ext2fs, partition type 0x83[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]kernel /boot/vmlinuz-2.6.26-2-686 root=UUID=66f39d0f-25d0-4be6-898b-2801e5dc7f6d ro quiet[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Error 2: Bad file or directory type[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Press any key to continue[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]How to fix this problem so that each Linux start-up?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Please, consider I’m a total newbie for Linux and right now I’m experimenting with all these OSs and I want to have this problem fixed.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I attach below NeoGrub Configuration and original menu.lst for Ubuntu and Debian. Maybe you need these to help me?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]# NeoSmart NeoGrub Bootloader Configuration File[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# Please see the EasyBCD Documentation for information on how to create/modify entries:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# [http://neosmart.net/wiki/display/EBCD](http://neosmart.net/wiki/display/EBCD)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]title Ubuntu 9.04, kernel 2.6.28-11-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid 2ebe46ab-c5d8-4f15-a626-0162138d86a3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=2ebe46ab-c5d8-4f15-a626-0162138d86a3 ro quiet splash [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]initrd /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]quiet[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid 2ebe46ab-c5d8-4f15-a626-0162138d86a3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=2ebe46ab-c5d8-4f15-a626-0162138d86a3 ro single[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]initrd /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]title Ubuntu 9.04, memtest86+[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]uuid 2ebe46ab-c5d8-4f15-a626-0162138d86a3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel /boot/memtest86+.bin[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]quiet[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]title Debian GNU/Linux, kernel 2.6.26-2-686[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]root (hd0,7)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel /boot/vmlinuz-2.6.26-2-686 root=UUID=66f39d0f-25d0-4be6-898b-2801e5dc7f6d ro quiet[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]initrd /boot/initrd.img-2.6.26-2-686[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]title Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]root (hd0,7)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]kernel /boot/vmlinuz-2.6.26-2-686 root=UUID=66f39d0f-25d0-4be6-898b-2801e5dc7f6d ro single[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]initrd /boot/initrd.img-2.6.26-2-686[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Ubuntu menu.lst[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]# menu.lst - See: grub(8), info grub, update-grub(8)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# grub-install(8), grub-floppy(8),[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# grub-md5-crypt, /usr/share/doc/grub[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# and /usr/share/doc/grub-doc/.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## default num[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# Set the default entry to the entry number NUM. Numbering starts from 0, and[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# the entry number 0 is the default if the command is not used.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# You can specify 'saved' instead of a number. In this case, the default entry[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# is the entry saved with the command 'savedefault'.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# WARNING: If you are using dmraid do not use 'savedefault' or your[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# array will desync and will not let you boot your system.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]default 0[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## timeout sec[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# Set a timeout, in SEC seconds, before automatically booting the default entry[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# (normally the first entry defined).[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]timeout 10[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## hiddenmenu[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# Hides the menu by default (press ESC to see the menu)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#hiddenmenu[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]# Pretty colours[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#color cyan/blue white/blue[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## password ['--md5'] passwd[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# If used in the first section of a menu file, disable all interactive editing[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# control (menu entry editor and command-line) and entries protected by the[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# command 'lock'[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# e.g. password topsecret[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# password topsecret[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# examples[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# title Windows 95/98/NT/2000[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# root (hd0,0)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# makeactive[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# chainloader +1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# title Linux[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# root (hd0,1)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# kernel /vmlinuz root=/dev/hda2 ro[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]### BEGIN AUTOMAGIC KERNELS LIST[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## lines between the AUTOMAGIC KERNELS LIST markers will be modified[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## by the debian update-grub script except for the default options below[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## DO NOT UNCOMMENT THEM, Just edit them to your needs[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## ## Start Default Options ##[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## default kernel options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## default kernel options for automagic boot options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## If you want special options for specific kernels use kopt_x_y_z[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## where x.y.z is kernel version. Minor versions can be omitted.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. kopt=root=/dev/hda1 ro[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## kopt_2_6_8=root=/dev/hdc1 ro[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## kopt_2_6_8_2_686=root=/dev/hdc2 ro[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# kopt=root=UUID=2ebe46ab-c5d8-4f15-a626-0162138d86a3 ro[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## default grub root device[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. groot=(hd0,0)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# groot=2ebe46ab-c5d8-4f15-a626-0162138d86a3[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub create alternative automagic boot options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. alternative=true[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## alternative=false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# alternative=true[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub lock alternative automagic boot options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. lockalternative=true[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## lockalternative=false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# lockalternative=false[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## additional options to use with the default boot option, but not with the[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## alternatives[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. defoptions=vga=791 resume=/dev/hda5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# defoptions=quiet splash[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub lock old automagic boot options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. lockold=false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## lockold=true[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# lockold=false[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## Xen hypervisor options to use with the default Xen boot option[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# xenhopt=[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## Xen Linux kernel options to use with the default Xen boot option[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# xenkopt=console=tty0[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## altoption boot targets option[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## multiple altoptions lines are allowed[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. altoptions=(extra menu suffix) extra boot options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## altoptions=(recovery) single[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# altoptions=(recovery mode) single[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## controls how many kernels should be put into the menu.lst[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## only counts the first occurence of a kernel, not the[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## alternative kernel options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. howmany=all[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## howmany=7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# howmany=all[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## specify if running in Xen domU or have grub detect automatically[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## update-grub will ignore non-xen kernels when running in domU and vice versa[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. indomU=detect[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## indomU=true[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## indomU=false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# indomU=detect[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub create memtest86 boot option[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. memtest86=true[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## memtest86=false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# memtest86=true[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub adjust the value of the default booted system[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## can be true or false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# updatedefaultentry=false[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub add savedefault to the default options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## can be true or false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# savedefault=false[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## ## End Default Options ##[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]title Ubuntu 9.04, kernel 2.6.28-11-generic[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]uuid 2ebe46ab-c5d8-4f15-a626-0162138d86a3[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=2ebe46ab-c5d8-4f15-a626-0162138d86a3 ro quiet splash [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]initrd /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]quiet[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]uuid 2ebe46ab-c5d8-4f15-a626-0162138d86a3[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=2ebe46ab-c5d8-4f15-a626-0162138d86a3 ro single[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]initrd /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]title Ubuntu 9.04, memtest86+[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]uuid 2ebe46ab-c5d8-4f15-a626-0162138d86a3[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]kernel /boot/memtest86+.bin[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]quiet[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]### END DEBIAN AUTOMAGIC KERNELS LIST[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]# This is a divider, added to separate the menu items below from the Debian[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# ones.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]title Other operating systems:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]root[/SIZE][/FONT]
 
 
[FONT=Courier New][SIZE=2]# This entry automatically added by the Debian installer for a non-linux OS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# on /dev/sda1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]title Windows Vista (loader)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]rootnoverify (hd0,0)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]savedefault[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]makeactive[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]chainloader +1[/SIZE][/FONT]
 
 
 
[FONT=Times New Roman][SIZE=3]Debian menu.lst[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]# menu.lst - See: grub(8), info grub, update-grub(8)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# grub-install(8), grub-floppy(8),[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# grub-md5-crypt, /usr/share/doc/grub[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# and /usr/share/doc/grub-legacy-doc/.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## default num[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# Set the default entry to the entry number NUM. Numbering starts from 0, and[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# the entry number 0 is the default if the command is not used.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# You can specify 'saved' instead of a number. In this case, the default entry[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# is the entry saved with the command 'savedefault'.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# WARNING: If you are using dmraid do not change this entry to 'saved' or your[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# array will desync and will not let you boot your system.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]default 0[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## timeout sec[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# Set a timeout, in SEC seconds, before automatically booting the default entry[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# (normally the first entry defined).[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]timeout 5[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]# Pretty colours[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]color cyan/blue white/blue[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## password ['--md5'] passwd[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# If used in the first section of a menu file, disable all interactive editing[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# control (menu entry editor and command-line) and entries protected by the[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# command 'lock'[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# e.g. password topsecret[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# password topsecret[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# examples[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# title Windows 95/98/NT/2000[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# root (hd0,0)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# makeactive[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# chainloader +1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# title Linux[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# root (hd0,1)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# kernel /vmlinuz root=/dev/hda2 ro[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]### BEGIN AUTOMAGIC KERNELS LIST[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## lines between the AUTOMAGIC KERNELS LIST markers will be modified[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## by the debian update-grub script except for the default options below[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## DO NOT UNCOMMENT THEM, Just edit them to your needs[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## ## Start Default Options ##[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## default kernel options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## default kernel options for automagic boot options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## If you want special options for specific kernels use kopt_x_y_z[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## where x.y.z is kernel version. Minor versions can be omitted.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. kopt=root=/dev/hda1 ro[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## kopt_2_6_8=root=/dev/hdc1 ro[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## kopt_2_6_8_2_686=root=/dev/hdc2 ro[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# kopt=root=UUID=66f39d0f-25d0-4be6-898b-2801e5dc7f6d ro[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## default grub root device[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. groot=(hd0,0)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# groot=(hd0,7)[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub create alternative automagic boot options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. alternative=true[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## alternative=false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# alternative=true[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub lock alternative automagic boot options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. lockalternative=true[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## lockalternative=false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# lockalternative=false[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## additional options to use with the default boot option, but not with the[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## alternatives[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. defoptions=vga=791 resume=/dev/hda5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# defoptions=quiet[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub lock old automagic boot options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. lockold=false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## lockold=true[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# lockold=false[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## Xen hypervisor options to use with the default Xen boot option[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# xenhopt=[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## Xen Linux kernel options to use with the default Xen boot option[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# xenkopt=console=tty0[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## altoption boot targets option[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## multiple altoptions lines are allowed[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. altoptions=(extra menu suffix) extra boot options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## altoptions=(single-user) single[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# altoptions=(single-user mode) single[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## controls how many kernels should be put into the menu.lst[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## only counts the first occurence of a kernel, not the[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## alternative kernel options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. howmany=all[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## howmany=7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# howmany=all[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub create memtest86 boot option[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## e.g. memtest86=true[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## memtest86=false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# memtest86=true[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub adjust the value of the default booted system[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## can be true or false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# updatedefaultentry=false[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## should update-grub add savedefault to the default options[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]## can be true or false[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# savedefault=false[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]## ## End Default Options ##[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]title Debian GNU/Linux, kernel 2.6.26-2-686[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]root (hd0,7)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]kernel /boot/vmlinuz-2.6.26-2-686 root=UUID=66f39d0f-25d0-4be6-898b-2801e5dc7f6d ro quiet[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]initrd /boot/initrd.img-2.6.26-2-686[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]title Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]root (hd0,7)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]kernel /boot/vmlinuz-2.6.26-2-686 root=UUID=66f39d0f-25d0-4be6-898b-2801e5dc7f6d ro single[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]initrd /boot/initrd.img-2.6.26-2-686[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]### END DEBIAN AUTOMAGIC KERNELS LIST[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]# This is a divider, added to separate the menu items below from the Debian[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# ones.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]title Other operating systems:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]root[/SIZE][/FONT]
 
 
[FONT=Courier New][SIZE=2]# This entry automatically added by the Debian installer for a non-linux OS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# on /dev/sda1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]title Windows Vista/Longhorn (loader)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]root (hd0,0)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]savedefault[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]makeactive[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]chainloader +1[/SIZE][/FONT]
 
 
[FONT=Courier New][SIZE=2]# This entry automatically added by the Debian installer for an existing[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# linux installation on /dev/sda7.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]title Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda7)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]root (hd0,6)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=2ebe46ab-c5d8-4f15-a626-0162138d86a3 ro quiet splash [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]initrd /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]savedefault[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]boot[/SIZE][/FONT]
 
 
[FONT=Courier New][SIZE=2]# This entry automatically added by the Debian installer for an existing[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# linux installation on /dev/sda7.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda7)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]root (hd0,6)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=2ebe46ab-c5d8-4f15-a626-0162138d86a3 ro single [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]initrd /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]savedefault[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]boot[/SIZE][/FONT]
 
 
[FONT=Courier New][SIZE=2]# This entry automatically added by the Debian installer for an existing[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]# linux installation on /dev/sda7.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]title Ubuntu 9.04, memtest86+ (on /dev/sda7)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]root (hd0,6)[/SIZE][/FONT]
[SIZE=2][FONT=Courier New]kernel /boot/memtest86+.bin [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]savedefault[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]boot[/FONT][/SIZE]

---

### Post by Mark Phelps on 2009-10-25
NeoSmart Technologies, makers of EasyBCD and NeoGRUB, have excellent forums and tutorials for just such problems.  Suggest you check there to see what they have.

---

