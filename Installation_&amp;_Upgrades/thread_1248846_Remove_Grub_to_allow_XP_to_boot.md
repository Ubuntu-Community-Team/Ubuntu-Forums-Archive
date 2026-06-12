---
title: "Remove Grub to allow XP to boot"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by Aled's Dad on 2009-08-24
I wonder if I can ask the advice of the Ububtu experts on this forum?
  I have never posted before, and apologise in advance for the length of this post.
   
  My son was a great devotee of this forum.  He used to enjoy reading the posts,  and used to post occasionally here under the name of “Aled y Cymro”. He learnt a lot here. He thought Ubuntu was great, and Windows was the pits.
   
  Sadly Aled died in June, having installed a second HDD on his computer to make it a dual boot, with XP on the first drive and Ubuntu on the second.
   
  Unfortunately, things are not well on the original HDD, there are frequent fatal error messages, and weird things like sound disappearing, only reappearing after rolling back sound drivers in Device manager. Other irritations are accented characters appearing even on a seemingly English (UK) keyboard. My son loaded lots of game programs, and although most are uninstalled, it’s left a lot of clutter in the registry.
   
  It really needs a repair if not a re-installation of Windows XP.
  I also want to  stop the computer from booting directly into Ubuntu.
   
  I have tried to get my head round Ubuntu, but I fear that I’m too long in the tooth to learn much about it.
   
  I gather that Grub is installed. When the machine boots, I get a menu inviting me to choose from the following options:
   
  “    Ubuntu 9.04, kernel 2.6.28-11-generic
       Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
       Ubuntu 9.04, memtest 86+
  Other operating systems:
       Microsoft Windows XP Home Edition”
   
  Now I can choose XP  at that menu if I’m quick enough, but I’d rather just get the system to revert back to how it used to be and load XP automatically.
   
  To do this, as I understand it,I need to remove Grub  as follows:
   
  1)  Change BIOS settings so that 1st Boot device is set to CD.
  2   Boot from the original XP CD, enter the recovery console (press R when it asks you whether you want to install windows etc.) When you're at the console, type:                        [FONT=Courier]fixmbr[/FONT]
  
  This hopefully should remove Grub, and allow XP to boot automatically.
   
  (I understand that several posters are divided in their opinion as to whether to use this method or to do it in DOS and  type:  [FONT=&quot]fdisk /MBR[/FONT]      at a DOS prompt.
  Someone else suggested :   [FONT=Courier]fixboot[/FONT]
  Another suggested[FONT=Courier]:[/FONT]            [FONT=&quot]fixboot c:[/FONT]          then      [FONT=&quot]fixmbr            )[/FONT]
  
  I would appreciate any help you folk can give.
  If this is successful, realistically, I’m going to have to reformat the Ubuntu drive as an NTFS.
  Then I’m going to have to reinstall XP.
  I trust then that Windows would then recognise the second drive and it would appear in Windows Explorer? It doesn’t now as it is not an NTFS drive.
   
  I’m sorry having to come into the midst of folk who are obviously keen supporters of Ubuntu, to ask their help how to remove an OS that my young son was a keen advocate of. 
   
  I just wish it didn’t have to be this way.
   
  Any help you can give an ageing Dad would be appreciated. If any of my plans above don’t make sense, please let me know. I’m not planning on doing any of this until I get all your welcome advice, and I’ve got it clear in my mind.
   
  **Aled’s Dad**
   
   
  _My system setup:_
   
  AMD Athlon 64 3200+ processor
  1.5GB (3x512) DDR RAM
  Gigabyte Geforce 6800
  Creative Labs Sound Blaster Audigy
   
  _Original HDD_  -Maxtor 6Y160MO    SATA    NTFS 152.7GB (Disc 0 in Windows Disk Management-Primary Partition) running Win XP SP2.
   
  _Second HDD_ - Seagate ST3160215 4S Barracuda 7200.10 160GB   SATA -Disc 1 in Windows Disk Management-Primary Partition (144.74GB)  and Logical Drive 4.31GB  running Linux/Ubuntu.
   
  _My current boot.ini file in Windows is :_
   
  [bootloader]
  timeout=30
  default=multi(0)disk(0)rdisk(0)Partition(1)\WINDOWS
  [operating systems]
  multi(0)disk(0)rdisk(0)Partition(1)\WINDOWS=”Microsoft Windows XP Home Edition” /noexecute=optin/fastdetect
   
  (Does anything need to be changed here or will it perhaps be fixed by fixmbr?)
   
   
  I don’t have the expertise to edit the menu.lst file in the boot folder in Ubuntu. It seems to be password protected, I don’t have permissions to change it. I’ve tried, but I can’t.
   
  That file is as follows :
   
  [FONT=Arial]# menu.lst - See: grub(8), info grub, update-grub(8)[/FONT]
  [FONT=Arial]#            grub-install(8), grub-floppy(8),[/FONT]
  [FONT=Arial]#            grub-md5-crypt, /usr/share/doc/grub[/FONT]
  [FONT=Arial]#            and /usr/share/doc/grub-doc/.[/FONT]
  
  [FONT=Arial]## default num[/FONT]
  [FONT=Arial]# Set the default entry to the entry number NUM. Numbering starts from 0, and[/FONT]
  [FONT=Arial]# the entry number 0 is the default if the command is not used.[/FONT]
  [FONT=Arial]#[/FONT]
  [FONT=Arial]# You can specify 'saved' instead of a number. In this case, the default entry[/FONT]
  [FONT=Arial]# is the entry saved with the command 'savedefault'.[/FONT]
  [FONT=Arial]# WARNING: If you are using dmraid do not use 'savedefault' or your[/FONT]
  [FONT=Arial]# array will desync and will not let you boot your system.[/FONT]
  [FONT=Arial]default                     0[/FONT]
  
  [FONT=Arial]## timeout sec[/FONT]
  [FONT=Arial]# Set a timeout, in SEC seconds, before automatically booting the default entry[/FONT]
  [FONT=Arial]# (normally the first entry defined).[/FONT]
  [FONT=Arial]timeout                     30[/FONT]
  
  [FONT=Arial]## hiddenmenu[/FONT]
  [FONT=Arial]# Hides the menu by default (press ESC to see the menu)[/FONT]
  [FONT=Arial]#hiddenmenu[/FONT]
  
  [FONT=Arial]# Pretty colours[/FONT]
  [FONT=Arial]#color cyan/blue white/blue[/FONT]
  
  [FONT=Arial]## password ['--md5'] passwd[/FONT]
  [FONT=Arial]# If used in the first section of a menu file, disable all interactive editing[/FONT]
  [FONT=Arial]# control (menu entry editor and command-line)  and entries protected by the[/FONT]
  [FONT=Arial]# command 'lock'[/FONT]
  [FONT=Arial]# e.g. password topsecret[/FONT]
  [FONT=Arial]#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/[/FONT]
  [FONT=Arial]# password topsecret[/FONT]
  
  [FONT=Arial]#[/FONT]
  [FONT=Arial]# examples[/FONT]
  [FONT=Arial]#[/FONT]
  [FONT=Arial]# title                        Windows 95/98/NT/2000[/FONT]
  [FONT=Arial]# root                       (hd0,0)[/FONT]
  [FONT=Arial]# makeactive[/FONT]
  [FONT=Arial]# chainloader          +1[/FONT]
  [FONT=Arial]#[/FONT]
  [FONT=Arial]# title                        Linux[/FONT]
  [FONT=Arial]# root                       (hd0,1)[/FONT]
  [FONT=Arial]# kernel   /vmlinuz root=/dev/hda2 ro[/FONT]
  [FONT=Arial]#[/FONT]
  
  [FONT=Arial]#[/FONT]
  [FONT=Arial]# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST[/FONT]
  
  [FONT=Arial]### BEGIN AUTOMAGIC KERNELS LIST[/FONT]
  [FONT=Arial]## lines between the AUTOMAGIC KERNELS LIST markers will be modified[/FONT]
  [FONT=Arial]## by the debian update-grub script except for the default options below[/FONT]
  
  [FONT=Arial]## DO NOT UNCOMMENT THEM, Just edit them to your needs[/FONT]
  
  [FONT=Arial]## ## Start Default Options ##[/FONT]
  [FONT=Arial]## default kernel options[/FONT]
  [FONT=Arial]## default kernel options for automagic boot options[/FONT]
  [FONT=Arial]## If you want special options for specific kernels use kopt_x_y_z[/FONT]
  [FONT=Arial]## where x.y.z is kernel version. Minor versions can be omitted.[/FONT]
  [FONT=Arial]## e.g. kopt=root=/dev/hda1 ro[/FONT]
  [FONT=Arial]##      kopt_2_6_8=root=/dev/hdc1 ro[/FONT]
  [FONT=Arial]##      kopt_2_6_8_2_686=root=/dev/hdc2 ro[/FONT]
  [FONT=Arial]# kopt=root=UUID=7c10b45d-e244-442f-aefe-993d6ff90488 ro[/FONT]
  
  [FONT=Arial]## default grub root device[/FONT]
  [FONT=Arial]## e.g. groot=(hd0,0)[/FONT]
  [FONT=Arial]# groot=(hd1,0)[/FONT]
  
  [FONT=Arial]## should update-grub create alternative automagic boot options[/FONT]
  [FONT=Arial]## e.g. alternative=true[/FONT]
  [FONT=Arial]##      alternative=false[/FONT]
  [FONT=Arial]# alternative=true[/FONT]
  
  [FONT=Arial]## should update-grub lock alternative automagic boot options[/FONT]
  [FONT=Arial]## e.g. lockalternative=true[/FONT]
  [FONT=Arial]##      lockalternative=false[/FONT]
  [FONT=Arial]# lockalternative=false[/FONT]
  
  [FONT=Arial]## additional options to use with the default boot option, but not with the[/FONT]
  [FONT=Arial]## alternatives[/FONT]
  [FONT=Arial]## e.g. defoptions=vga=791 resume=/dev/hda5[/FONT]
  [FONT=Arial]# defoptions=quiet splash[/FONT]
  
  [FONT=Arial]## should update-grub lock old automagic boot options[/FONT]
  [FONT=Arial]## e.g. lockold=false[/FONT]
  [FONT=Arial]##      lockold=true[/FONT]
  [FONT=Arial]# lockold=false[/FONT]
  
  [FONT=Arial]## Xen hypervisor options to use with the default Xen boot option[/FONT]
  [FONT=Arial]# xenhopt=[/FONT]
  
  [FONT=Arial]## Xen Linux kernel options to use with the default Xen boot option[/FONT]
  [FONT=Arial]# xenkopt=console=tty0[/FONT]
  
  [FONT=Arial]## altoption boot targets option[/FONT]
  [FONT=Arial]## multiple altoptions lines are allowed[/FONT]
  [FONT=Arial]## e.g. altoptions=(extra menu suffix) extra boot options[/FONT]
  [FONT=Arial]##      altoptions=(recovery) single[/FONT]
  [FONT=Arial]# altoptions=(recovery mode) single[/FONT]
  
  [FONT=Arial]## controls how many kernels should be put into the menu.lst[/FONT]
  [FONT=Arial]## only counts the first occurence of a kernel, not the[/FONT]
  [FONT=Arial]## alternative kernel options[/FONT]
  [FONT=Arial]## e.g. howmany=all[/FONT]
  [FONT=Arial]##      howmany=7[/FONT]
  [FONT=Arial]# howmany=all[/FONT]
  
  [FONT=Arial]## specify if running in Xen domU or have grub detect automatically[/FONT]
  [FONT=Arial]## update-grub will ignore non-xen kernels when running in domU and vice versa[/FONT]
  [FONT=Arial]## e.g. indomU=detect[/FONT]
  [FONT=Arial]##      indomU=true[/FONT]
  [FONT=Arial]##      indomU=false[/FONT]
  [FONT=Arial]# indomU=detect[/FONT]
  
  [FONT=Arial]## should update-grub create memtest86 boot option[/FONT]
  [FONT=Arial]## e.g. memtest86=true[/FONT]
  [FONT=Arial]##      memtest86=false[/FONT]
  [FONT=Arial]# memtest86=true[/FONT]
  
  [FONT=Arial]## should update-grub adjust the value of the default booted system[/FONT]
  [FONT=Arial]## can be true or false[/FONT]
  [FONT=Arial]# updatedefaultentry=false[/FONT]
  
  [FONT=Arial]## should update-grub add savedefault to the default options[/FONT]
  [FONT=Arial]## can be true or false[/FONT]
  [FONT=Arial]# savedefault=false[/FONT]
  
  [FONT=Arial]## ## End Default Options ##[/FONT]
  
  [FONT=Arial]title                           Ubuntu 9.04, kernel 2.6.28-11-generic[/FONT]
  [FONT=Arial]root                          (hd1,0)[/FONT]
  [FONT=Arial]kernel                      /boot/vmlinuz-2.6.28-11-generic root=UUID=7c10b45d-e244-442f-aefe-993d6ff90488 ro quiet splash [/FONT]
  [FONT=Arial]initrd                        /boot/initrd.img-2.6.28-11-generic[/FONT]
  [FONT=Arial]quiet[/FONT]
  
  [FONT=Arial]title                           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)[/FONT]
  [FONT=Arial]root                          (hd1,0)[/FONT]
  [FONT=Arial]kernel                      /boot/vmlinuz-2.6.28-11-generic root=UUID=7c10b45d-e244-442f-aefe-993d6ff90488 ro  single[/FONT]
  [FONT=Arial]initrd                        /boot/initrd.img-2.6.28-11-generic[/FONT]
  
  [FONT=Arial]title                           Ubuntu 9.04, memtest86+[/FONT]
  [FONT=Arial]root                          (hd1,0)[/FONT]
  [FONT=Arial]kernel                      /boot/memtest86+.bin[/FONT]
  [FONT=Arial]quiet[/FONT]
  
  [FONT=Arial]### END DEBIAN AUTOMAGIC KERNELS LIST[/FONT]
  
  [FONT=Arial]# This is a divider, added to separate the menu items below from the Debian[/FONT]
  [FONT=Arial]# ones.[/FONT]
  [FONT=Arial]title                           Other operating systems:[/FONT]
  [FONT=Arial]root[/FONT]
  
  
  [FONT=Arial]# This entry automatically added by the Debian installer for a non-linux OS[/FONT]
  [FONT=Arial]# on /dev/sda1[/FONT]
  [FONT=Arial]title                           Microsoft Windows XP Home Edition[/FONT]
  [FONT=Arial]root                          (hd0,0)[/FONT]
  [FONT=Arial]savedefault[/FONT]
  [FONT=Arial]makeactive[/FONT]
  [FONT=Arial]chainloader             +1[/FONT]
   
   
  
  
  
   
   
  I

---

### Post by VMC on 2009-08-24
If you have the original XP you can boot to the recovery mode and then type fixmbr

Here's a [LINK]("http://www.blogmanno.com/?q=node/9") for further help.

---

I'm very sad about your loss. So soon after his passing to have to deal with such stuff. I hope you find comfort with your loved ones. Vern

---

### Post by ronparent on 2009-08-24
A reinstall of windows xp would take care of everything. 

It is probably advisable because over time windows becomes so loaded with so much detrious that it becomes unrelyable. I've done this recently with older windows xp installs that were showing signs of arterialscerosis if not outright senility. Althoug it entails reinstalling all programs as well as windows service pack, the net results have effectively cleared useless junk out of the attic. Althoug it sounds drastic I would reccommend it.

---

