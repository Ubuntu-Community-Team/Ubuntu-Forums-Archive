---
title: "Dual Core Grub won't boot..."
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2009-10-16
I've got two hard disks on my computer.

However, I installed Windows XP (NTFS) on the first hard disk, say, sda;
and installed Ubuntu 9.04 (EXT3) on the second hard disk, say, sdb.
Therefore, my grub is probably also on the very first several sectors on the second hard disk.

Now, symptoms:

1) I can see my ext3 file system from WindowsXP
2) I can boot my Ubuntu 9.04 with a boot CD
you may pick up: 
installation->boot from existing system-> etc...

namely, let the CD boot first for you to start something like Lino or Grub.

3) I can't start grub. Without the CD, whenever rebooting, it will be automatically booted into WindowsXP.


df info:
```
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            111441192  10206532  95573760  10% /
tmpfs                   517088         0    517088   0% /lib/init/rw
varrun                  517088       112    516976   1% /var/run
varlock                 517088         0    517088   0% /var/lock
udev                    517088       136    516952   1% /dev
tmpfs                   517088       264    516824   1% /dev/shm
/dev/hdc                 41030     41030         0 100% /media/CDROM

```


/etc/fstab info:
```
$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c58f5d31-a733-4228-aa8b-313c4f5a492a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=b0ef92da-737f-4790-9fe7-82af0f77b281 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```


/boot/grub/menu.lst info
```
$ cat menu.lst         
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),       
#            grub-md5-crypt, /usr/share/doc/grub    
#            and /usr/share/doc/grub-doc/.          

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.              
#                                                                            
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.                          
# WARNING: If you are using dmraid do not use 'savedefault' or your           
# array will desync and will not let you boot your system.                    
default         0                                                             

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).                                          
timeout         10                                                             

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu                                            

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the  
# command 'lock'                                                              
# e.g. password topsecret                                                     
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/                        
# password topsecret                                                          

#
# examples
#         
# title         Windows 95/98/NT/2000
# root          (hd0,0)              
# makeactive                         
# chainloader   +1                   
#                                    
# title         Linux                
# root          (hd0,1)              
# kernel        /vmlinuz root=/dev/hda2 ro
#                                         

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=c58f5d31-a733-4228-aa8b-313c4f5a492a ro          

## default grub root device
## e.g. groot=(hd0,0)      
# groot=c58f5d31-a733-4228-aa8b-313c4f5a492a

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

title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            c58f5d31-a733-4228-aa8b-313c4f5a492a 
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=c58f5d31-a733-4228-aa8b-313c4f5a492a ro quiet splash                                                                                                
initrd          /boot/initrd.img-2.6.28-15-generic                                                     
quiet                                                                                                  

title           Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid            c58f5d31-a733-4228-aa8b-313c4f5a492a                 
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=c58f5d31-a733-4228-aa8b-313c4f5a492a ro  single                                                                                                     
initrd          /boot/initrd.img-2.6.28-15-generic                                                     

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            c58f5d31-a733-4228-aa8b-313c4f5a492a 
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=c58f5d31-a733-4228-aa8b-313c4f5a492a ro quiet splash                                                                                                
initrd          /boot/initrd.img-2.6.28-11-generic                                                     
quiet                                                                                                  

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            c58f5d31-a733-4228-aa8b-313c4f5a492a                 
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=c58f5d31-a733-4228-aa8b-313c4f5a492a ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            c58f5d31-a733-4228-aa8b-313c4f5a492a
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

$

```



Please can anybody help?? 
Thanks in advance.

Cheers
JIA

---

### Post by prshah on 2009-10-16
> **jiapei100 said:**
> 
However, I installed Windows XP (NTFS) on the first hard disk, say, sda;
and installed Ubuntu 9.04 (EXT3) on the second hard disk, say, sdb.
Therefore, my grub is probably also on the very first several sectors on the second hard disk.

What you need to do is install GRUB to the FIRST hard disk, or setup the BIOS to boot off the 2nd Hard disk.

You can install grub to your first hard disk WITHOUT affecting Windows. Post back if you want more details on this.

Or you can set your BIOS to boot the 2nd hard disk rather than the first; the exact options vary from BIOS to BIOS.

---

