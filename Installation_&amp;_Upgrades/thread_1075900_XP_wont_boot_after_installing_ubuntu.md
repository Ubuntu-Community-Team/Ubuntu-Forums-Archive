---
title: "XP wont boot after installing ubuntu"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by Penguinw on 2009-02-20
I just installed ubuntu on my new box and i cant boot xp, all what happens when i select windows xp in grub is it comes up saying "Starting up..." then has a flashing cursor underneath it. I don't think my hdd access light is flashing. My menu.lst entry is:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd0,0)
savedefault
chainloader	+1

Any help would be much appreciated, thanks.

---

### Post by dakiro on 2009-02-20
add this, should help

title XP
fallback 1
find --set-root /ntldr
chainloader /ntldr
savedefault --wait=2

---

### Post by caljohnsmith on 2009-02-20
It sounds to me like your Windows boot sector might need to be fixed, so in order to get a better idea if that is the case, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by Penguinw on 2009-02-20
ok, heres the text from the RESULTS.txt

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb401021f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   850,946,984   850,946,922   7 HPFS/NTFS
/dev/sda2         850,946,985   976,768,064   125,821,080  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5E38BC4738BC1FC7" LABEL="Sid" TYPE="ntfs" 
/dev/sda2: UUID="8f1962c2-d28b-4338-859a-556487a89e74" TYPE="ext2" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext2 (rw,relatime,errors=remount-ro)
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
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/philip/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=philip)
/dev/scd0 on /media/SXPPSP2 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================

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
timeout		10

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
# kopt=root=UUID=8f1962c2-d28b-4338-859a-556487a89e74 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8f1962c2-d28b-4338-859a-556487a89e74

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
uuid		8f1962c2-d28b-4338-859a-556487a89e74
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8f1962c2-d28b-4338-859a-556487a89e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8f1962c2-d28b-4338-859a-556487a89e74
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8f1962c2-d28b-4338-859a-556487a89e74 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8f1962c2-d28b-4338-859a-556487a89e74
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8f1962c2-d28b-4338-859a-556487a89e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8f1962c2-d28b-4338-859a-556487a89e74
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8f1962c2-d28b-4338-859a-556487a89e74 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8f1962c2-d28b-4338-859a-556487a89e74
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd0,0)
savedefault
chainloader	+1

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8f1962c2-d28b-4338-859a-556487a89e74 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=5E38BC4738BC1FC7 /windows        ntfs    defaults,umask=007,gid=46 0       1
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 448.7GB: boot/grub/menu.lst
 448.7GB: boot/grub/stage2
 448.8GB: boot/initrd.img-2.6.27-11-generic
 448.7GB: boot/initrd.img-2.6.27-7-generic
 448.7GB: boot/vmlinuz-2.6.27-11-generic
 448.7GB: boot/vmlinuz-2.6.27-7-generic
 448.8GB: initrd.img
 448.7GB: initrd.img.old
 448.7GB: vmlinuz
 448.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by caljohnsmith on 2009-02-20
According to the script results, there doesn't seem to be anything wrong with how Grub is configured to boot Windows, so I would recommend using "testdisk" to see if your Windows boot sector needs fixing; to use testdisk, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sda1 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Or if testdisk says the boot sectors are identical and doesn't give you an option to "Rebuild BS", let me know, and we can work from there.

---

### Post by Penguinw on 2009-02-21
ok, just done the testdisk, and it worked fine. It booted up correctly. Thank you very much :)

---

### Post by caljohnsmith on 2009-02-21
You're welcome, glad that testdisk fixed your XP install. Cheers and enjoy your dual-boot setup. :)

---

### Post by bbob on 2009-02-21
I have the same issue as Penguinw.  I have a single 40 GB drive with XP Pro on the first partition (10 Gb), and Freedos on the second (4 Gb).  These were working fine in a dual-boot config using the boot manager that comes with Freedos, until I installed Ubuntu on the remaining free space on the drive.

Grub gives me menu choices for all 3 OSes, and Ubuntu and Freedos boot fine.  But when booting XP, I get the Windows splash screen followed by a blue screen that flashes on so quickly that I can't read the text on it.  Then the computer restarts.

Testdisk says "Sectors are identical."

Here is the content of the RESULTS.TXT file generated by boot_info_script26.sh:



```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3a2d3a2c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,535,039    19,534,977  17 Hidden HPFS/NTFS
/dev/sda2          19,535,040    27,358,694     7,823,655   c W95 FAT32 (LBA)
/dev/sda3          27,358,695    78,124,094    50,765,400   5 Extended
/dev/sda5          27,358,758    75,923,189    48,564,432  83 Linux
/dev/sda6          75,923,253    78,124,094     2,200,842  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="01C96C90E486CDE0" LABEL="DRV2_VOL1" TYPE="ntfs" 
/dev/sda2: LABEL="FREEDOS" UUID="060D-11EA" TYPE="vfat" 
/dev/sda5: UUID="12b26842-0774-468a-bc75-9e273900379f" TYPE="ext3" 
/dev/sda6: UUID="86961b02-cdc3-4428-9193-571c82aa6944" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/whunter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=whunter)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


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
timeout		10

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
# kopt=root=UUID=12b26842-0774-468a-bc75-9e273900379f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=12b26842-0774-468a-bc75-9e273900379f

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
uuid		12b26842-0774-468a-bc75-9e273900379f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=12b26842-0774-468a-bc75-9e273900379f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		12b26842-0774-468a-bc75-9e273900379f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=12b26842-0774-468a-bc75-9e273900379f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		12b26842-0774-468a-bc75-9e273900379f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		FreeDOS
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=12b26842-0774-468a-bc75-9e273900379f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=86961b02-cdc3-4428-9193-571c82aa6944 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  22.4GB: boot/grub/menu.lst
  22.3GB: boot/grub/stage2
  22.4GB: boot/initrd.img-2.6.27-7-generic
  22.4GB: boot/vmlinuz-2.6.27-7-generic
  22.4GB: initrd.img
  22.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 08 20 00  |.X.FRDOS4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 c0 14 2a 01  |........?.....*.|
00000020  27 61 77 00 ca 1d 00 00  00 00 00 00 02 00 00 00  |'aw.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  ff 00 29 ea 11 0d 06 46  52 45 45 44 4f 53 20 20  |..)....FREEDOS  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 5e 5a  |@.^.s........_^Z|
000001c0  c3 4c 6f 61 64 69 6e 67  20 46 72 65 65 44 4f 53  |.Loading FreeDOS|
000001d0  20 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  | ...............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 4e 6f  |..............No|
000001f0  20 4b 45 52 4e 45 4c 20  20 53 59 53 00 00 55 aa  | KERNEL  SYS..U.|
00000200

```

---

### Post by caljohnsmith on 2009-02-22
Bbob, it looks like Grub is correctly configured to boot Windows, so I think it is safe to say you have a Windows problem and not a Grub problem at this point. One thing I notice though is that your Windows sda1 partition is "hidden", i.e. the file system ID is not NTFS, but that of a hidden partition. So I think the first thing to do would be to change it back to NTFS:
```
sudo sfdisk -c /dev/sda 1 7
```
Then try booting Windows again and see if it makes any difference. Let me know exactly what happens, and we can work from there if you want.

---

### Post by bbob on 2009-02-22
Caljohnsmith, thanks for the suggestion.  I ran the command, but attempting to boot XP produces the exact same result as before - the Windows splash screen followed by a momentary blue screen with text on it, and then the computer restarts.

I double checked just to make sure that the Windows partition is no longer hidden:

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,535,039    19,534,977   7 HPFS/NTFS


In case it helps, here is a copy of the boot.ini file:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

I'm happy to accept any assistance you are able to offer.

---

### Post by caljohnsmith on 2009-02-22
OK, how about booting your Windows Install CD, go to the "recovery console" and do:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. Then try booting Windows again and let me know if it made any difference or not.

---

### Post by bbob on 2009-03-09
Sorry for the delayed reply caljohnsmith.  I can't locate the original XP disks for that old machine.  So instead I've decided to use this challenge as my opportunity to simply switch that machine over to Ubuntu.  XP's NTFS partition is readable under Ubuntu, so all my data is available to me if I need it.  And if I really get stuck and absolutely have to boot XP I can throw the old HDD that I copied the XP partition from back in the machine.

So thanks for your help, and I'll move on to other challenges like getting my old Soundblaster 16 to work.  But that'll be a separate post...

---

