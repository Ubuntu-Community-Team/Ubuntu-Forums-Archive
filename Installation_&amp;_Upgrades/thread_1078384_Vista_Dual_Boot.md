---
title: "Vista Dual Boot"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by chevmaro on 2009-02-23
So Im a noob to Linux.  I think I have learned alot over the weekend though.  I setup Ubuntu 8.10 Desktop for the first time. My intentions were to have a media server to serve to my PS3.  I setup MediaTomb and its working great so far.  

My only problem is getting the thing to dual boot with vista.  My current configuration is 2 80GB drives in Raid0 that Vista uses.  I have ubuntu on a 250gb drive.  I have a 100mb partition for /boot, 40GB for FileSystem, 2gb for swap, and the remaining 200 or so gb is /home where I store media.  

Ubuntu does not recognize the two 80gb drives as being a raid.  It sees them as two drives.  Any time I try to write to them it corrupts my windows files and I have to format the drive.  So I dont think its possible to write my ubuntu MBR to the windows drive or is it?  

If I understand this correctly I think I need to get the Vista MBR and write it to my 250gb ubuntu drive.

Currently I can still access either OS by pressing F8 and selecting the boot device from the bios screen.  If I select my Raid it will boot into vista with no problems.  If I select the other 250gb drive it will boot into ubuntu no problem.  

Its working fine right now and if I have to live with it this way im ok with that.  But I would prefer to get a boot screen vs. using the bios.  Any suggestions please.

---

### Post by chevmaro on 2009-02-23
Forgot to mention.  I tried supergrub and it works great but, when booting from the vista drive it will only let me boot to windows.  Same with the other drive, if I boot with the ubuntu drive it will boot to linux but not windows.

---

### Post by caljohnsmith on 2009-02-23
I think it would help to first get a clearer picture of your setup, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by chevmaro on 2009-02-23
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdc1 and 
                       looks at sector 83007 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #1 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xba181b92

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   206,094,335   206,092,288   7 HPFS/NTFS
/dev/sda2         206,094,336   259,448,823    53,354,488   7 HPFS/NTFS
/dev/sda3         259,448,832   312,588,287    53,139,456   c W95 FAT32 (LBA)

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b0539

Partition  Boot         Start           End          Size  Id System



Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf3fcf3fc

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63       192,779       192,717  83 Linux
/dev/sdc2             192,780   488,392,064   488,199,285   5 Extended
/dev/sdc5             192,843    78,316,874    78,124,032  83 Linux
/dev/sdc6          78,316,938    82,220,669     3,903,732  82 Linux swap / Solaris
/dev/sdc7          82,220,733   488,392,064   406,171,332  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sdc1: UUID="e22fe888-4a49-49db-bf73-7b89269dd5f4" TYPE="ext3" 
/dev/sdc5: UUID="d4ca59b2-9733-4f39-b2f7-185258d8b9b9" TYPE="ext3" 
/dev/sdc6: UUID="a0a6bd0e-78b9-436c-80b9-0d01fb66f289" TYPE="swap" 
/dev/sdc7: UUID="061aa346-066f-43a8-bbb1-a6adebc1b68a" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdc5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc1 on /boot type ext3 (rw,relatime)
/dev/sdc7 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/preston/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=preston)


============================= sdc1/grub/menu.lst: =============================

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
# kopt=root=UUID=d4ca59b2-9733-4f39-b2f7-185258d8b9b9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e22fe888-4a49-49db-bf73-7b89269dd5f4

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		e22fe888-4a49-49db-bf73-7b89269dd5f4
kernel		/vmlinuz-2.6.27-11-generic root=UUID=d4ca59b2-9733-4f39-b2f7-185258d8b9b9 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e22fe888-4a49-49db-bf73-7b89269dd5f4
kernel		/vmlinuz-2.6.27-11-generic root=UUID=d4ca59b2-9733-4f39-b2f7-185258d8b9b9 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e22fe888-4a49-49db-bf73-7b89269dd5f4
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d4ca59b2-9733-4f39-b2f7-185258d8b9b9 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e22fe888-4a49-49db-bf73-7b89269dd5f4
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d4ca59b2-9733-4f39-b2f7-185258d8b9b9 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e22fe888-4a49-49db-bf73-7b89269dd5f4
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.27-11-generic
    .0GB: initrd.img-2.6.27-7-generic
    .0GB: vmlinuz-2.6.27-11-generic
    .0GB: vmlinuz-2.6.27-7-generic

=========================== sdc5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d4ca59b2-9733-4f39-b2f7-185258d8b9b9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e22fe888-4a49-49db-bf73-7b89269dd5f4

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		e22fe888-4a49-49db-bf73-7b89269dd5f4
kernel		/vmlinuz-2.6.27-11-generic root=UUID=d4ca59b2-9733-4f39-b2f7-185258d8b9b9 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e22fe888-4a49-49db-bf73-7b89269dd5f4
kernel		/vmlinuz-2.6.27-11-generic root=UUID=d4ca59b2-9733-4f39-b2f7-185258d8b9b9 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e22fe888-4a49-49db-bf73-7b89269dd5f4
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d4ca59b2-9733-4f39-b2f7-185258d8b9b9 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e22fe888-4a49-49db-bf73-7b89269dd5f4
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d4ca59b2-9733-4f39-b2f7-185258d8b9b9 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e22fe888-4a49-49db-bf73-7b89269dd5f4
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc5
UUID=d4ca59b2-9733-4f39-b2f7-185258d8b9b9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
UUID=e22fe888-4a49-49db-bf73-7b89269dd5f4 /boot           ext3    relatime        0       2
# /dev/sdc7
UUID=061aa346-066f-43a8-bbb1-a6adebc1b68a /home           ext3    relatime        0       2
# /dev/sdc6
UUID=a0a6bd0e-78b9-436c-80b9-0d01fb66f289 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


    .1GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
    .1GB: boot/initrd.img-2.6.27-11-generic
    .1GB: boot/initrd.img-2.6.27-7-generic
    .1GB: boot/vmlinuz-2.6.27-11-generic
    .1GB: boot/vmlinuz-2.6.27-7-generic
    .1GB: initrd.img
    .1GB: initrd.img.old
    .1GB: vmlinuz
    .1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  01 00 6d 61 5c 77 63 6d  3a 2f 2f 4d 69 63 72 6f  |..ma\wcm://Micro|
00000010  73 6f 66 74 2d 57 69 6e  64 6f 77 73 2d 64 61 74  |soft-Windows-dat|
00000020  61 63 6c 65 6e 3f 76 65  72 73 69 6f 6e 3d 36 2e  |aclen?version=6.|
00000030  30 2e 36 30 30 31 2e 31  38 30 39 38 26 61 6d 70  |0.6001.18098&amp|
00000040  3b 6c 61 6e 67 75 61 67  65 3d 6e 65 75 74 72 61  |;language=neutra|
00000050  6c 26 61 6d 70 3b 70 72  6f 63 65 73 73 6f 72 41  |l&amp;processorA|
00000060  72 63 68 69 74 65 63 74  75 72 65 3d 61 6d 64 36  |rchitecture=amd6|
00000070  34 26 61 6d 70 3b 70 75  62 6c 69 63 4b 65 79 54  |4&amp;publicKeyT|
00000080  6f 6b 65 6e 3d 33 31 62  66 33 38 35 36 61 64 33  |oken=31bf3856ad3|
00000090  36 34 65 33 35 26 61 6d  70 3b 76 65 72 73 69 6f  |64e35&amp;versio|
000000a0  6e 53 63 6f 70 65 3d 6e  6f 6e 53 78 53 26 61 6d  |nScope=nonSxS&am|
000000b0  70 3b 73 63 6f 70 65 3d  61 6c 6c 55 73 65 72 73  |p;scope=allUsers|
000000c0  5c 6d 65 74 61 64 61 74  61 5c 65 6c 65 6d 65 6e  |\metadata\elemen|
000000d0  74 73 5c 48 4b 45 59 5f  4c 4f 43 41 4c 5f 4d 41  |ts\HKEY_LOCAL_MA|
000000e0  43 48 49 4e 45 5f 53 6f  66 74 77 61 72 65 5f 4d  |CHINE_Software_M|
000000f0  69 63 72 6f 73 6f 66 74  5f 57 69 6e 64 6f 77 73  |icrosoft_Windows|
00000100  5f 43 75 72 72 65 6e 74  56 65 72 73 69 6f 6e 5f  |_CurrentVersion_|
00000110  45 78 70 6c 6f 72 65 72  5f 56 6f 6c 75 6d 65 43  |Explorer_VolumeC|
00000120  61 63 68 65 73 5f 53 65  74 75 70 5f 4c 6f 67 5f  |aches_Setup_Log_|
00000130  46 69 6c 65 73 5f 44 65  73 63 72 69 70 74 69 6f  |Files_Descriptio|
00000140  6e 22 20 6e 61 6d 65 3d  22 40 78 73 64 3a 74 79  |n" name="@xsd:ty|
00000150  70 65 22 20 74 79 70 65  3d 22 30 78 31 30 30 30  |pe" type="0x1000|
00000160  30 30 30 63 22 20 65 6e  63 6f 64 69 6e 67 3d 22  |000c" encoding="|
00000170  62 61 73 65 36 34 22 20  76 61 6c 75 65 3d 22 65  |base64" value="e|
00000180  41 42 7a 41 47 51 41 4f  67 42 7a 41 48 51 41 63  |ABzAGQAOgBzAHQAc|
00000190  67 42 70 41 47 34 41 5a  77 41 41 41 41 3d 3d 22  |gBpAG4AZwAAAA=="|
000001a0  2f 3e 0a 20 20 20 20 20  20 20 20 3c 53 65 74 4b  |/>.        <SetK|
000001b0  65 79 56 61 6c 75 65 20  70 61 74 68 3d 22 5c 52  |eyValue path="\R|
000001c0  65 67 69 73 74 72 79 5c  6d 61 63 68 69 6e 65 5c  |egistry\machine\|
000001d0  53 63 68 65 6d 61 5c 77  63 6d 3a 2f 2f 4d 69 63  |Schema\wcm://Mic|
000001e0  72 6f 73 6f 66 74 2d 57  69 6e 64 6f 77 73 2d 64  |rosoft-Windows-d|
000001f0  61 74 61 63 6c 65 6e 3f  76 65 72 73 69 6f 6e 3d  |ataclen?version=|
00000200

Unknown BootLoader  on sda2


Unknown BootLoader  on sda3

```

---

### Post by chevmaro on 2009-02-23
Thanks for your help.  I followed your instructions.  If we could touch on mounting a NTFS drive while were at it.  Or I can save for another post.

Thanks.

---

### Post by caljohnsmith on 2009-02-23
OK, booting Windows from a RAID array can unfortunately be tricky, usually the easiest thing to do is try all possible combinations of Windows entries in Grub that might work. So how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the end add:
```
title       Windows Vista #1
rootnoverify     (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista #2
rootnoverify     (hd1)
map        (hd0) (hd1)
chainloader +1

title       Windows Vista #3
rootnoverify     (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista #4
rootnoverify     (hd2)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title       Windows Vista #5
rootnoverify     (hd2)
map        (hd0) (hd2)
chainloader +1

title       Windows Vista #6
rootnoverify     (hd2)
map        (hd2) (hd0)
chainloader +1
```
Three out of those six entries will probably give you a basic error like "operating system not found" or something of that sort. How about trying them all from your Grub menu, and let me know if any of them work; if none work to boot Vista, let me know exactly what happens when you try each one from the Grub menu. We can work from there.

---

### Post by chevmaro on 2009-02-23
Will do.  Thanks for your help.

Can we break it down so I know what im looking at?

So lets take the first one:

title       Windows Vista #1 
rootnoverify     (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

Title Windows Vista #1.  Clear enough we are putting a title on the boot entry.

Rootnoverify
Map
Chainloader

What do those mean?

I think I know by now ubuntu sees the hard drives sort of like the bios does.  HD0 is first detected, HD1 is second etc??

---

### Post by chevmaro on 2009-02-24
Vista #1 worked.  Thanks so much.:guitar:

---

### Post by caljohnsmith on 2009-02-24
Glad to hear one of those Vista entries worked; cheers and enjoy your dual-boot Ubuntu/Vista setup. :)

---

### Post by chevmaro on 2009-02-24
Why do I have two kernels in my boot menu?  Can I remove one of them?  Disabling safe mode and mem test a bad idea or is that something I can use the install cd for?

---

### Post by caljohnsmith on 2009-02-24
> **chevmaro said:**
> Why do I have two kernels in my boot menu?  Can I remove one of them?  Disabling safe mode and mem test a bad idea or is that something I can use the install cd for?
Sure, you can remove the memtest entry from your menu.lst if want; I would recommend keeping at least one backup kernel in your menu.lst in addition to the one you are using in case you ever have problems booting the latest kernel after updates or something. So since you only have two kernels, I would recommend keeping both of them for now, but it's up to you.

---

### Post by drocksvold on 2009-03-08
Thanks for this, it saved me some time, not to mention hair!
:popcorn:

---

