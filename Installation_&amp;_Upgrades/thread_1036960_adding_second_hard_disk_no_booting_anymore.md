---
title: "adding second hard disk: no booting anymore"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by Wiel on 2009-01-11
I have a fresh installed 8.10 (kubuntu, alternate CD) I started with one SATA hard disk. 
In the BIOS I disabled on-board SATA link and RAID. The system 
is up and running now. 

Now I added the second SATA drive and booted the system. GRUB started and 
I saw the kubuntu splash screen. After a couple of seconds this screen disapeared and I saw (big screen, B&W) the following
lines and I was left with the Busybox shell.

Loading please wait ....
19+0 records in
19+0 records out
kinit:name_to_dev_t(/dev/sda5)=dev(8,5)
kinit: trying to resume from /dev/sda5
kinit: no resume image, doing normal boot ....
mount: mounting /dev/disk/by-uuid/<some number> on /root failed:
invalid argument
mount: mounting /root/dev on /dev/.static/dev failed: no such file or directory
mount: mounting /sys on /root/sys/ failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem does not have /sbin/init
no init found: try passing init=bootarg
...and here starts the Busybox shell...

Is booted with the LiveCD , both hard disks connected. 
Output of sudo fdisk -l:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000425bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       35003   281161566   83  Linux
/dev/sda2           35004       36481    11872035    5  Extended
/dev/sda5           35004       36481    11872003+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ad6625d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux
Thank you very much for all tips.

---

### Post by caljohnsmith on 2009-01-11
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Kubuntu Live CD desktop (I assume that's what you are using right now?), open a Konsole and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Wiel on 2009-01-11
The following output is from the normal booted system. This means the second hard disk is disconnected from main board. Within 10 minutes I will send you the output from after booting from the LiveCD.

Many thanks in advance.


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.           

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -   
    Boot sector info:      
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes                               
Disk identifier: 0x000425bf                                          

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   562323194   281161566   83  Linux 
/dev/sda2       562323195   586067264    11872035    5  Extended
/dev/sda5       562323258   586067264    11872003+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK                                                           

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7ddcef53-dd34-4e40-96dd-33f02637d3e5" TYPE="ext3" 
/dev/sda5: UUID="64b3be99-83ce-46ec-b96a-fe6c2566360b" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)  
/proc on /proc type proc (rw,noexec,nosuid,nodev)       
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)       
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)     
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)                            
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)                    
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)  
fusectl on /sys/fs/fuse/connections type fusectl (rw)             
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)               

=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout         3                                                              

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu                                             

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
# kopt=root=UUID=7ddcef53-dd34-4e40-96dd-33f02637d3e5 ro          

## default grub root device
## e.g. groot=(hd0,0)      
# groot=7ddcef53-dd34-4e40-96dd-33f02637d3e5

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

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            7ddcef53-dd34-4e40-96dd-33f02637d3e5
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=7ddcef53-dd34-4e40-96dd-33f02637d3e5 ro quiet splash                                                   
initrd          /boot/initrd.img-2.6.27-7-generic                               

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            7ddcef53-dd34-4e40-96dd-33f02637d3e5                
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=7ddcef53-dd34-4e40-96dd-33f02637d3e5 ro  single                                                        
initrd          /boot/initrd.img-2.6.27-7-generic                               

title           Ubuntu 8.10, memtest86+
uuid            7ddcef53-dd34-4e40-96dd-33f02637d3e5
kernel          /boot/memtest86+.bin                

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#                                            
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0     
# /dev/sda1                                                           
UUID=7ddcef53-dd34-4e40-96dd-33f02637d3e5 /               ext3    relatime,errors=remount-ro 0       1                                                          
# /dev/sda5                                                                     
UUID=64b3be99-83ce-46ec-b96a-fe6c2566360b none            swap    sw              0       0                                                                     
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0     
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0     

================================== sda1/boot: ==================================

total 12980
drwxr-xr-x  3 root root    4096 2009-01-10 21:16 .
drwxr-xr-x 20 root root    4096 2009-01-10 21:05 ..
-rw-r--r--  1 root root  503560 2008-10-24 09:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 09:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-10 21:16 grub
-rw-r--r--  1 root root 8819450 2009-01-10 21:16 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 22:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 09:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 09:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 09:55 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 332
drwxr-xr-x 2 root root   4096 2009-01-10 21:16 .
drwxr-xr-x 3 root root   4096 2009-01-10 21:16 ..
-rw-r--r-- 1 root root    191 2009-01-10 21:16 default
-rw-r--r-- 1 root root   8108 2009-01-10 21:16 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-10 21:16 fat_stage1_5
-rw-r--r-- 1 root root   8712 2009-01-10 21:16 jfs_stage1_5
-rw-r--r-- 1 root root   4298 2009-01-10 21:16 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-10 21:16 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-10 21:16 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-10 21:16 stage1
-rw-r--r-- 1 root root 121460 2009-01-10 21:16 stage2
-rw-r--r-- 1 root root 121460 2009-01-10 21:16 stage2_eltorito
-rw-r--r-- 1 root root   9556 2009-01-10 21:16 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by Wiel on 2009-01-11
Now I booted with the LiveCD and ran the script sudo bash boot_info_....
(I mounted disk /dev/sda1 by hand to /home/ubuntu/data, wich is also possible with /dev/sdb1)

Hope this helps.





```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000425bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   562323194   281161566   83  Linux
/dev/sda2       562323195   586067264    11872035    5  Extended
/dev/sda5       562323258   586067264    11872003+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8ad6625d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   586067264   293033601   83  Linux

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7ddcef53-dd34-4e40-96dd-33f02637d3e5" TYPE="ext3" 
/dev/sda5: UUID="64b3be99-83ce-46ec-b96a-fe6c2566360b" TYPE="swap" 
/dev/sdb1: UUID="df23a26f-6529-45c2-b922-0ae3052ea276" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /home/ubuntu/diska type ext3 (rw)

=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=7ddcef53-dd34-4e40-96dd-33f02637d3e5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7ddcef53-dd34-4e40-96dd-33f02637d3e5

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7ddcef53-dd34-4e40-96dd-33f02637d3e5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7ddcef53-dd34-4e40-96dd-33f02637d3e5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7ddcef53-dd34-4e40-96dd-33f02637d3e5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7ddcef53-dd34-4e40-96dd-33f02637d3e5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7ddcef53-dd34-4e40-96dd-33f02637d3e5
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7ddcef53-dd34-4e40-96dd-33f02637d3e5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=64b3be99-83ce-46ec-b96a-fe6c2566360b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 12980
drwxr-xr-x  3 root root    4096 2009-01-10 20:16 .
drwxr-xr-x 20 root root    4096 2009-01-10 20:05 ..
-rw-r--r--  1 root root  503560 2008-10-24 07:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 07:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-10 20:16 grub
-rw-r--r--  1 root root 8819450 2009-01-10 20:16 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 07:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 07:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 07:55 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 332
drwxr-xr-x 2 root root   4096 2009-01-10 20:16 .
drwxr-xr-x 3 root root   4096 2009-01-10 20:16 ..
-rw-r--r-- 1 root root    191 2009-01-10 20:16 default
-rw-r--r-- 1 root root   8108 2009-01-10 20:16 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-10 20:16 fat_stage1_5
-rw-r--r-- 1 root root   8712 2009-01-10 20:16 jfs_stage1_5
-rw-r--r-- 1 root root   4298 2009-01-10 20:16 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-10 20:16 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-10 20:16 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-10 20:16 stage1
-rw-r--r-- 1 root root 121460 2009-01-10 20:16 stage2
-rw-r--r-- 1 root root 121460 2009-01-10 20:16 stage2_eltorito
-rw-r--r-- 1 root root   9556 2009-01-10 20:16 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by caljohnsmith on 2009-01-11
So do you really have Kubuntu installed and not Ubuntu? :) Not that it is important, but your menu.lst and /etc/issue file both say you are using Ubuntu and not Kubuntu, so I am just curious. But besides that, from the output of that script, it looks like everything about your (K)ubuntu install is correctly configured as expected. So I can only think your booting problem would be somehow related to your BIOS settings for the HDDs. Is your (K)ubuntu drive still listed before the external drive in the BIOS boot order when the external drive is connected? Do any of your BIOS settings related to the (K)ubuntu drive change at all when you connect your external drive?

---

### Post by yue232qi121 on 2009-01-11
how much about a [nike dunk](http://www.afkicks.com) ??every one know??

---

### Post by Wiel on 2009-01-12
Thank you for your reaction. Yes I have really kubuntu installed (the k is only for the desktop, and not the kernel I think.:)

For the settings of the BIOS I will try a couple of things:
-which connector to use for the different drives (two drives, four connectors)
- and check how the settings in the BIOS change.

I will report tomorrow evening (in Germany).

---

### Post by Wiel on 2009-01-17
After all I managed to install.
I downloaded and used the CD: kubuntu-8.10-Desktop-AMD64.
The complete system is installed on disk sda. Booting was OK. I moved then the /home directory by hand to the other disk (sdb), of course after creating a filesystem.

I studied a little bit more the installation with the 8.10-alternate disk and found
in the file /var/log/installer/hardware that the mdraid was installed and configured although I said _No_ to the question: do you want to activate a RAid setup.  I think there is some problem with the alternate CDs

For me the problem is solved.

May thanks for your time and help.
Greetings
Wiel

---

### Post by caljohnsmith on 2009-01-17
Glad to hear you sorted out the problem and have Kubuntu booting OK; cheers and enjoy Kubuntu. :)

---

