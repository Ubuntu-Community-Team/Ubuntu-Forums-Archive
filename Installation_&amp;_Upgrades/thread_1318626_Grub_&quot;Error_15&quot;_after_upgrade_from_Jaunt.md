---
title: "Grub &quot;Error 15&quot; after upgrade from Jaunty to Karmic"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by cknight on 2009-11-07
Just upgraded my system last night from Jaunty to Karmic (via upgrade, not a clean install).  I now can't boot from any kernels getting an "Error 15" from grub.  Any ideas what is going on?  Here is some info which may help:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       996,029       995,967  83 Linux
/dev/sda2             996,030   625,137,344   624,141,315   5 Extended
/dev/sda5             996,093    34,202,384    33,206,292  83 Linux
/dev/sda6          34,202,448   617,136,974   582,934,527  83 Linux
/dev/sda7         617,137,038   625,137,344     8,000,307  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4ea93807

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   563,881,499   563,881,437   5 Extended
/dev/sdb5                 126   563,881,499   563,881,374  83 Linux
/dev/sdb2    *    563,881,500   625,137,344    61,255,845   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda5: UUID="00ab043e-08e4-49d4-8e74-a5e45c9b9fe3" TYPE="ext4" 
/dev/sda6: UUID="1b2d062a-b2c3-491e-8843-336b306866d1" TYPE="ext4" 
/dev/sda7: UUID="383352fb-84d2-4a57-be11-ab81a44fdf41" TYPE="swap" 
/dev/sdb2: UUID="71B6895C5F3CA881" LABEL="Vista Partition" TYPE="ntfs" 
/dev/sdb5: LABEL="Data" UUID="7254f67d-47f1-4b75-a8ba-f272ad7e2629" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /mnt type ext4 (rw)
/dev/sda1 on /mnt/boot type ext2 (rw)
/dev on /mnt/dev type none (rw,bind)

============================= sda1/grub/menu.lst: =============================

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
# kopt=root=UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=06c0371d-4fd7-4003-81fe-fdfa70ca495f

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		06c0371d-4fd7-4003-81fe-fdfa70ca495f
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		06c0371d-4fd7-4003-81fe-fdfa70ca495f
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		06c0371d-4fd7-4003-81fe-fdfa70ca495f
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		06c0371d-4fd7-4003-81fe-fdfa70ca495f
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		06c0371d-4fd7-4003-81fe-fdfa70ca495f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows Vista
rootnoverify 	(hd1,1)
chainloader 	+1

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.28-16-generic
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: vmlinuz-2.6.28-16-generic
    .0GB: vmlinuz-2.6.31-14-generic

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=06c0371d-4fd7-4003-81fe-fdfa70ca495f

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		06c0371d-4fd7-4003-81fe-fdfa70ca495f
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		06c0371d-4fd7-4003-81fe-fdfa70ca495f
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		06c0371d-4fd7-4003-81fe-fdfa70ca495f
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		06c0371d-4fd7-4003-81fe-fdfa70ca495f
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		06c0371d-4fd7-4003-81fe-fdfa70ca495f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows Vista
rootnoverify 	(hd1,1)
chainloader 	+1

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=06c0371d-4fd7-4003-81fe-fdfa70ca495f /boot           ext2    relatime        0       2
# /home was on /dev/sda7 during installation
UUID=1b2d062a-b2c3-491e-8843-336b306866d1 /home           ext4    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=63634451-7b03-40cc-83f7-1b55d7498641 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb5 /data ext4 defaults 0 0

=================== sda5: Location of files loaded by Grub: ===================


    .5GB: boot/grub/menu.lst
    .5GB: boot/grub/stage2
    .5GB: boot/initrd.img-2.6.28-16-generic
    .5GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.28-16-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: initrd.img
    .5GB: initrd.img.old
    .5GB: vmlinuz
    .5GB: vmlinuz.old

---

### Post by jheaton5 on 2009-11-07
After you get Error 15, can you get to the grub menu?

If you can, select e and make note of the name of the kernel.  Then select c to go to the grub console. In the console type:```
grub> kernel <kernel name>
grub> boot <kernel name>
```

The kernel should boot and you will be able to login.  After the system is completed the boot sequence, in any terminal, type ```
$ sudo update-grub
```

---

### Post by cknight on 2009-11-08
> **jheaton5 said:**
> After you get Error 15, can you get to the grub menu?

If you can, select e and make note of the name of the kernel.  Then select c to go to the grub console. In the console type:```
grub> kernel <kernel name>
grub> boot <kernel name>
```

The kernel should boot and you will be able to login.  After the system is completed the boot sequence, in any terminal, type ```
$ sudo update-grub
```

thanks for your response, but unfortunately, it didn't work.  At the grub terminal I typed:
```
grub> kernel /boot/vmlinuz-2.6.31-14-generic

```
but I still get "file not found".  Yet, here's the output of by /boot directory:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount -t ext2 /dev/sda1 /mnt/boot
ubuntu@ubuntu:~$ cd /mnt
ubuntu@ubuntu:/mnt$ cd boot
ubuntu@ubuntu:/mnt/boot$ ls -l
total 28070
-rw-r--r-- 1 root root 1474560 2009-06-27 12:07 1737_A06.img
-rw-r--r-- 1 root root  528310 2009-10-20 21:56 abi-2.6.28-16-generic
-rw-r--r-- 1 root root  629174 2009-10-16 18:03 abi-2.6.31-14-generic
-rw-r--r-- 1 root root   96866 2009-10-20 21:56 config-2.6.28-16-generic
-rw-r--r-- 1 root root  111371 2009-10-16 18:03 config-2.6.31-14-generic
drwxr-xr-x 2 root root    1024 2009-11-07 07:55 grub
-rw-r--r-- 1 root root 7208464 2009-11-07 07:55 initrd.img-2.6.28-16-generic
-rw-r--r-- 1 root root 7898342 2009-11-07 07:50 initrd.img-2.6.31-14-generic
drwxr-xr-x 2 root root   12288 2009-05-30 23:07 lost+found
-rw-r--r-- 1 root root   20068 2009-06-27 12:06 memdisk
-rw-r--r-- 1 root root  128796 2009-10-23 16:11 memtest86+.bin
-rw-r--r-- 1 root root 1450875 2009-10-20 21:56 System.map-2.6.28-16-generic
-rw-r--r-- 1 root root 1664737 2009-10-16 18:03 System.map-2.6.31-14-generic
-rw-r--r-- 1 root root    1074 2009-10-20 21:58 vmcoreinfo-2.6.28-16-generic
-rw-r--r-- 1 root root    1196 2009-10-16 18:06 vmcoreinfo-2.6.31-14-generic
-rw-r--r-- 1 root root 3491696 2009-10-20 21:56 vmlinuz-2.6.28-16-generic
-rw-r--r-- 1 root root 3890400 2009-10-16 18:03 vmlinuz-2.6.31-14-generic

```

Any other ideas?  Presumably my boot partition is correctly mounting, otherwise I wouldn't be seeing the grub menu, so I'm very perplexed it can't find the file.  Did the installation of the new kernel during the upgrade itself go awry?  Would installing grub2 start from scratch (rather than building off of the old grub entries), as I'd like to do this anyway?

---

### Post by jheaton5 on 2009-11-08
Try:```
grub> kernel vmlinuz-2.6.31-14-generic
grub> boot grub> kernel vmlinuz-2.6.31-14-generic
```

---

### Post by cknight on 2009-11-08
> **jheaton5 said:**
> Try:```
grub> kernel vmlinuz-2.6.31-14-generic
grub> boot grub> kernel vmlinuz-2.6.31-14-generic
```

Man I love this community.  Thanks for this, it did the trick (slightly modified to "grub> kernel /vmlinux...").  I've since edited my menu.lst (in /boot/grub) to remove offending references to /boot and it now finds the kernel image appropriately.  Now off to post my next Karmic katosprophe.  Definitely not feeling the karma on this upgrade...

---

### Post by dcanti on 2009-11-11
Hello guys, 

 i'm new here in ubuntu foruns, and i have this error 15 with grub. Using the solution:

go to menu, edit one line and press c to enter in command line
type:
grub>kernel /boot/vmlinuz-2.6.31-14-generic
grub>boot grub kernel /boot/vmlinuz-2.6.31-14-generic

and the system load, but when i type in the terminal 
sudo update-grub

The ubuntu says:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Soo i think thats fine, rigth? 

no, when i reboot the grub fails again and only load the system when i edit the grub, like in the beginning. Anyone know how to fix it?

---

### Post by dcanti on 2009-11-11
answring my own question and give the solution to the problem to anyone:

just in kernel line in menu.lst change the UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX to root=/dev/"the partition that is the / of your system" in my case is a sda1

---

