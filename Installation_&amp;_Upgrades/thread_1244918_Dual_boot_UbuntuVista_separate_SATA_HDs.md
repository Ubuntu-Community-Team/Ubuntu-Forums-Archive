---
title: "Dual boot Ubuntu/Vista separate SATA HDs"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by jandara on 2009-08-20
[SIZE=2]Hi everyone...[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Using this forum is going to be my last resource as I have been trying for a while to get a solution to “my problem”  [/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Here there is situation:[/SIZE]
 [SIZE=2]
[/SIZE] 
[LIST]
[*][SIZE=2]I have a desktop (Dell) with Windows Vista installed (HD, SATA, 250 GB).[/SIZE]
[*][SIZE=2]I bought another HD     (SATA, 500 GB) as I want to start using Ubuntu.[/SIZE]
[*][SIZE=2]As I did not want to     put in risk my windows Vista installation, I removed the HD with     Vista, installed the new HD and started the installation of Ubuntu     9.04.[/SIZE]
[*][SIZE=2]After the     installation, Ubuntu works perfect. If I want my windows vista, the     only thing i need to do is disconnect the HD with Ubuntu and connect     the HD with Vista (actually, I do not disconnect the HDs, I only     move the cable from SATA0 to SATA1 and vice versa)[/SIZE]
[*][SIZE=2]After previous step,     both OS work fine. However, I would like to put the cover of my     computer and start using GRUB[/SIZE]
[*][SIZE=2]I went through this     [document]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs")     (among others) and did not work for me. Any clue?[/SIZE]
[*][SIZE=2]I have attached the     output for the files/commands I believe you might need.[/SIZE]
[*][SIZE=2]Thanks in advance to     anyone/everyone[/SIZE]
[/LIST]
                                 

 

 [FONT=Courier 10 Pitch][SIZE=2]**sudo fdisk -l **[/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]Disk /dev/sda: 500.1 GB, 500107862016 bytes [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]255 heads, 63 sectors/track, 60801 cylinders [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]Units = cylinders of 16065 * 512 = 8225280 bytes [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]Disk identifier: 0xe84bb3e4 [/SIZE][/FONT]
 
    [FONT=Courier 10 Pitch][SIZE=2]Device Boot      Start         End      Blocks   Id  System [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]/dev/sda1   *           1       25497   204800000   83  Linux [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]/dev/sda2           25497       59538   273436672    7  HPFS/NTFS [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]/dev/sda3           59539       60801    10145047+   5  Extended [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]/dev/sda5           59539       60801    10145016   82  Linux swap / Solaris [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]Disk /dev/sdb: 250.0 GB, 250000000000 bytes [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]255 heads, 63 sectors/track, 30394 cylinders [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]Units = cylinders of 16065 * 512 = 8225280 bytes [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]Disk identifier: 0xd8000000 [/SIZE][/FONT]
 
    [FONT=Courier 10 Pitch][SIZE=2]Device Boot      Start         End      Blocks   Id  System [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]/dev/sdb1               1           5       40131   de  Dell Utility [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]/dev/sdb2               6        1311    10485760    7  HPFS/NTFS [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]/dev/sdb3   *        1311       30394   233612288    7  HPFS/NTFS [/SIZE][/FONT]
  

 

 [SIZE=2]**[FONT=Courier New]menu.lst[/FONT]**[/SIZE]
 [FONT=Courier 10 Pitch][SIZE=2]# menu.lst - See: grub(8), info grub, update-grub(8) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]#            grub-install(8), grub-floppy(8), [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]#            grub-md5-crypt, /usr/share/doc/grub [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]#            and /usr/share/doc/grub-doc/. [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## default num [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# Set the default entry to the entry number NUM. Numbering starts from 0, and [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# the entry number 0 is the default if the command is not used. [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# You can specify 'saved' instead of a number. In this case, the default entry [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# is the entry saved with the command 'savedefault'. [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# WARNING: If you are using dmraid do not use 'savedefault' or your [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# array will desync and will not let you boot your system. [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]default        0 [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## timeout sec [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# Set a timeout, in SEC seconds, before automatically booting the default entry [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# (normally the first entry defined). [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]timeout        3 [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## hiddenmenu [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# Hides the menu by default (press ESC to see the menu) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]hiddenmenu [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]# Pretty colours [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]#color cyan/blue white/blue [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## password ['--md5'] passwd [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# If used in the first section of a menu file, disable all interactive editing [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# control (menu entry editor and command-line)  and entries protected by the [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# command 'lock' [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# e.g. password topsecret [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# password topsecret [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]# [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# examples [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# title        Windows 95/98/NT/2000 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# root        (hd0,0) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# makeactive [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# chainloader    +1 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# title        Linux [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# root        (hd0,1) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# kernel    /vmlinuz root=/dev/hda2 ro [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]# [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]### BEGIN AUTOMAGIC KERNELS LIST [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## lines between the AUTOMAGIC KERNELS LIST markers will be modified [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## by the debian update-grub script except for the default options below [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## DO NOT UNCOMMENT THEM, Just edit them to your needs [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## ## Start Default Options ## [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## default kernel options [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## default kernel options for automagic boot options [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## If you want special options for specific kernels use kopt_x_y_z [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## where x.y.z is kernel version. Minor versions can be omitted. [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## e.g. kopt=root=/dev/hda1 ro [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]##      kopt_2_6_8=root=/dev/hdc1 ro [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]##      kopt_2_6_8_2_686=root=/dev/hdc2 ro [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# kopt=root=UUID=74d112be-c3ed-4e32-91d8-7d0aba2fe8d8 ro [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## default grub root device [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## e.g. groot=(hd0,0) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# groot=74d112be-c3ed-4e32-91d8-7d0aba2fe8d8 [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## should update-grub create alternative automagic boot options [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## e.g. alternative=true [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]##      alternative=false [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# alternative=true [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## should update-grub lock alternative automagic boot options [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## e.g. lockalternative=true [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]##      lockalternative=false [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# lockalternative=false [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## additional options to use with the default boot option, but not with the [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## alternatives [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## e.g. defoptions=vga=791 resume=/dev/hda5 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# defoptions=quiet splash [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## should update-grub lock old automagic boot options [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## e.g. lockold=false [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]##      lockold=true [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# lockold=false [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## Xen hypervisor options to use with the default Xen boot option [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# xenhopt= [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## Xen Linux kernel options to use with the default Xen boot option [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# xenkopt=console=tty0 [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## altoption boot targets option [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## multiple altoptions lines are allowed [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## e.g. altoptions=(extra menu suffix) extra boot options [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]##      altoptions=(recovery) single [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# altoptions=(recovery mode) single [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## controls how many kernels should be put into the menu.lst [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## only counts the first occurence of a kernel, not the [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## alternative kernel options [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## e.g. howmany=all [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]##      howmany=7 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# howmany=all [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## specify if running in Xen domU or have grub detect automatically [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## update-grub will ignore non-xen kernels when running in domU and vice versa [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## e.g. indomU=detect [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]##      indomU=true [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]##      indomU=false [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# indomU=detect [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## should update-grub create memtest86 boot option [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## e.g. memtest86=true [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]##      memtest86=false [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# memtest86=true [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## should update-grub adjust the value of the default booted system [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## can be true or false [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# updatedefaultentry=false [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## should update-grub add savedefault to the default options [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]## can be true or false [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]# savedefault=false [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]## ## End Default Options ## [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-15-generic [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]uuid        74d112be-c3ed-4e32-91d8-7d0aba2fe8d8 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=74d112be-c3ed-4e32-91d8-7d0aba2fe8d8 ro quiet splash  [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]initrd        /boot/initrd.img-2.6.28-15-generic [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]quiet [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]uuid        74d112be-c3ed-4e32-91d8-7d0aba2fe8d8 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=74d112be-c3ed-4e32-91d8-7d0aba2fe8d8 ro  single [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]initrd        /boot/initrd.img-2.6.28-15-generic [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-11-generic [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]uuid        74d112be-c3ed-4e32-91d8-7d0aba2fe8d8 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=74d112be-c3ed-4e32-91d8-7d0aba2fe8d8 ro quiet splash  [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]initrd        /boot/initrd.img-2.6.28-11-generic [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]quiet [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]uuid        74d112be-c3ed-4e32-91d8-7d0aba2fe8d8 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=74d112be-c3ed-4e32-91d8-7d0aba2fe8d8 ro  single [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]initrd        /boot/initrd.img-2.6.28-11-generic [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]title        Ubuntu 9.04, memtest86+ [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]uuid        74d112be-c3ed-4e32-91d8-7d0aba2fe8d8 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]kernel        /boot/memtest86+.bin [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]quiet [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]title Windows Vista 1,2 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]root (hd1,2) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]savedefault [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]makeactive [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]chainloader +1 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]map (hd0) (hd1) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]map (hd1) (hd0) [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]title Windows Vista 1,1 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]root (hd1,1) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]savedefault [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]makeactive [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]chainloader +1 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]map (hd0) (hd1) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]map (hd1) (hd0) [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]title Windows Vista 1,0 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]root (hd1,0) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]savedefault [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]makeactive [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]chainloader +1 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]map (hd0) (hd1) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]map (hd1) (hd0) [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=2]### END DEBIAN AUTOMAGIC KERNELS LIST[/SIZE][/FONT]
  

 

 [FONT=Courier New][SIZE=2]
[/SIZE][/FONT] 
 **[FONT=Courier New][SIZE=2]cat /boot/grub/device.map [/SIZE][/FONT]**
 [FONT=Courier New][SIZE=2](hd0)    /dev/sda [/SIZE][/FONT]
 [FONT=Courier New][SIZE=2](hd1)    /dev/sdb [/SIZE][/FONT]
  

 

[FONT=Courier New][SIZE=2]
[/SIZE][/FONT] 
[FONT=Courier New][SIZE=2]**cat /proc/partitions **[/SIZE]
major minor  #blocks  name

   8        0  488386584 sda
   8        1  204800000 sda1
   8        2  273436672 sda2
   8        3          1 sda3
   8        5   10145016 sda5
   8       16  244140625 sdb
   8       17      40131 sdb1
   8       18   10485760 sdb2
   8       19  233612288 sdb3[/FONT]





[FONT=Courier New][SIZE=2]
[/SIZE][/FONT]

---

### Post by joshedmonds on 2009-08-20
I've spent about 30 minutes looking at this, and while I don't claim to know the exact issue, I have some suggestions.

Bear in mind that you don't have to fully boot the computer to play with your menu.lst entries, just boot to the grub menu and make changes (F6? then e to edit) then boot, if they work write them down, if they don't just reset and try again. Much quicker than editing menu.lst every time.

The 'Windows Vista 1,2' entry in your menu.lst looks correct based on your fdisk and the Grub mapping.

The [Grub manual]("http://www.gnu.org/software/grub/manual/grub.html#Chain_002dloading") suggests these options:
[LIST]
[*]Change 'root' to 'rootnoverify'
[*]Add 'boot' on the line after 'chainloader +1'[/LIST]

Based on some other reading, I'd also suggest the following:
[LIST]
[*]Remove the map entries. Vista may boot without the map entries, as it surveys the drives independently.
[*]Swap the map entries, i.e. map hd1->0 then hd0->1. If you're going to follow a tutorial, may as well do it consistently :) . Although again, this shouldn't make a difference.[/LIST]

You also haven't specified how the boot is failing. Is it a grub error code, Vista bootloader error, blank screen?

Hopefully some other advice will be forthcoming, but it is intriguing...

---

### Post by SoftwareExplorer on 2009-08-20
Does your grub menu come up with the options you put in when you boot with the ubuntu drive first?

I would think if so that the windows vista 1,1 or 1,2 would start windows.

---

### Post by SoftwareExplorer on 2009-08-20
By the way, Jandara, welcome to ubuntu forums.

---

### Post by presence1960 on 2009-08-20
Boot your Machine and go into BIOS and in hard disk boot order set your 500 GB (sda) as first to boot. This should bring up GRUB assuming you installed GRUB to MBR of sda when you installed Ubuntu. if not it is an easy fix. So do this and see if GRUB comes up. If it does boot into Ubuntu.

Once in Ubuntu open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` 
scroll down to the bottom and edit your windows entry to this:

```
 title        Windows Vista
 root         (hd1,1)
 map          (hd0) (hd1)
 map          (hd1) (hd0)
 chainloader  +1 

 title        Dell Utility
 root         (hd1,0) 
 map          (hd0) (hd1)
 map          (hd1) (hd0)
 chainloader  +1

if windows is on sdb3 your vista root line should be root (hd1,2) instead of  root (hd1,1)
```

If I assume right your dell utility partition is a recovery partition. In any case I would make a backup of that partition for safe keeping. If dell gives you the ability to burn a set of bootable DVD(s) to recover Vista I would do that also. This way you have 2 ways to recover your factory image if the need arises.

FYI: you didn't need to keep plugging & unplugging the disks. You could have went in BIOS and set the disk you wanted to boot from as first in the hard disk boot order. whichever bootloader is on MBR of the disk that boots first is what will take over. if it is your Windows disk windows bootloader will take over, if it is your Ubuntu disk GRUB will take over.

P.S. put the Ubuntu disk into the first SATA slot.

---

### Post by presence1960 on 2009-08-20
you are in all probability going to need the map lines because windows is dependent on it being on a primary partition of the first disk that boots. The map lines "trick" windows into believing it is on the first disk that boots. In your setup you want to use GRUB and that is on sda which boots first. windows is on sdb, so You most likely need those map lines.

---

### Post by jandara on 2009-08-20
[FONT=Arial]Thanks everyone for your replies and the time you spent reading my comments.[/FONT]
  [FONT=Arial] [/FONT]
  [FONT=Arial]**Joshedmonds**: yes, I forgot to put the error I am getting. When I boot my computer, I got the GRUB menu with my options. It does not matter if I select Windows Vista 1,2 or 1,1 or 1,0… I always get the same error: [COLOR=Red]**Error 21**[/COLOR]. I will try your suggestion tonight and let you know what happens.[/FONT]
  [FONT=Arial] [/FONT]
  [FONT=Arial]**SoftwareExplorer **: Yes, I can see the menu with all my options, but any of my option to boot Windows Vista (1,1 or 1,2) have worked.[/FONT]
  [FONT=Arial] [/FONT]
  [FONT=Arial]**presence1960 **: computer is already configured to boot my 500GB HD (sda), this HD is connected to the 1st sata slot (SATA0). Actually,  I can see the Menu with all options. I will try with your suggestions for the menu.lst, but I am not seeing differences except for the savedefault and makeactive commands that you have removed.[/FONT]
  [FONT=Arial] [/FONT]
  [FONT=Arial]Any additional suggestion, please let me know.[/FONT]

---

### Post by presence1960 on 2009-08-20
> **jandara said:**
> 
  [FONT=Arial]**presence1960 **: computer is already configured to boot my 500GB HD (sda), this HD is connected to the 1st sata slot (SATA0). Actually,  I can see the Menu with all options. I will try with your suggestions for the menu.lst, but I am not seeing differences except for the savedefault and makeactive commands that you have removed.[/FONT]
  [FONT=Arial] [/FONT]
  [FONT=Arial]Any additional suggestion, please let me know.[/FONT]

actually there is a difference, you have the map lines after the chainloader +1 entry, they should precede the chainloader +1 entry. You can also try rootnoverify instead of root for the second line if root does not work.

---

### Post by Bartender on 2009-08-20
This being a fairly new Dell, the BIOS surely has a boot option as you start up.  
With just about any new PC, there's a key you tap as the PC is starting.  BIOS will pause and give you a screen which asks, "Which device do you want me to boot from?"

Not in those exact words of course :)

The point being, the simplest thing for you to do at this point might be to fix the Vista MBR (directions for this are all over the web), then UNPLUG the Vista HDD and either reinstall Ubuntu to the second HDD or use one of many instructions to have Ubuntu fix GRUB.

What you end up with is 
1) Vista, untouched, on the first drive
2) Ubuntu on the second drive WITH GRUB INSTALLED TO THAT DRIVE instead of part of GRUB on the Vista MBR.

Then you hook both drives up to the motherboard and use the boot option key (I don't know what it is on your Dell but it shouldn't be hard to figure out) to choose whether you want to start Vista or Ubuntu.

---

### Post by presence1960 on 2009-08-20
> **Bartender said:**
> 

What you end up with is 
1) Vista, untouched, on the first drive
2) Ubuntu on the second drive WITH GRUB INSTALLED TO THAT DRIVE instead of part of GRUB on the Vista MBR.

Then you hook both drives up to the motherboard and use the boot option key (I don't know what it is on your Dell but it shouldn't be hard to figure out) to choose whether you want to start Vista or Ubuntu.

He already has this except in reverse order- Ubuntu with GRUB on MBR is on first disk & Windows with it's bootloader on MBR is on second disk. he gets GRUB on booting, but we are working to get Vista entries in menu.lst to work. When he boots from the second drive windows loads- but he stated he wants to use GRUB.

---

### Post by jandara on 2009-08-21
Ok guys
 

 My BAD... I thought something like this would happen.
 

 I double checked the connection of my devices (HDs and DVD) and the physical connection I had was:
 

 SATA0: 500GB HD (Ubuntu)
 SATA1: DVD
 SATA2: 250GB HD (Vista)
 ](*,)


 So, with my configuration when I selected Vista,  GRUB was trying to boot from the DVD drive (obviously that is why it was not working).
 

 After changing the DVD to SATA2 and 250GB to SATA1 everything started working perfect.
:)
 

 Now, in my defense, why when I did [FONT=Courier New]fdisk -l[/FONT] I got that the 250GB was on HD1?
:-k



 Anyway, I am so happy with this that I will not dig in that question.
 

 I am so sorry about my mistake and the time you spent reading my post. Thanks very much for your help.. now, I will try to get all applications/drivers to work...

---

### Post by presence1960 on 2009-08-21
No biggie, glad you got it working. Enjoy Ubuntu. The great thing about linux is you can break stuff and fix it, but when you fix it you not only learn the fix, but why it broke and why the fix works.

---

### Post by joshedmonds on 2009-08-23
An excellent solution. I told you the question was intriguing...

---

