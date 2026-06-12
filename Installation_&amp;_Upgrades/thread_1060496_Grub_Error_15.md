---
title: "Grub Error 15"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by DMonkey08 on 2009-02-04
I've tried several times to install Ubuntu 8.10 on two different computers, but on each computer grub gives me "grub error 15" on boot (no menu or anything), and have had to re-install 8.04.  Both computers are dual-booted with XP, and when I tried to upgrade 8.04, it gave me grub error 17.

8.10 looks really slick, and I would like to install.  I'm confused as to why this problem would happen on two separate computers.  Can anyone help :confused:?

---

### Post by caljohnsmith on 2009-02-04
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by DMonkey08 on 2009-02-05
Here you go:

```
RESULTS.txt

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       191814752 sectors, but according to the info from 
                       fdisk, it has 191816037 sectors.
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /boot.ini /etc/fstab /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031e90

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   191,816,099   191,816,037   7 HPFS/NTFS
/dev/sda2         191,816,100   312,576,704   120,760,605   5 Extended
/dev/sda5         309,267,378   312,576,704     3,309,327  82 Linux swap / Solaris
/dev/sda6         191,816,226   309,267,314   117,451,089  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="28B4D529B4D4F9F0" TYPE="ntfs" 
/dev/sda5: UUID="a0a67122-ca60-42ca-89e1-cc3ad46c1c36" TYPE="swap" 
/dev/sda6: UUID="8b546fd8-856c-468b-baed-ac80dd5748df" SEC_TYPE="ext2" TYPE="ext3" 
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
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

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
# kopt=root=UUID=fa606613-fb13-4f24-8e87-e94bf7289375 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fa606613-fb13-4f24-8e87-e94bf7289375 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fa606613-fb13-4f24-8e87-e94bf7289375 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer


=============================== sda1/etc/fstab: ===============================

#mtd0                    /                       jffs2    defaults,noatime 1 1
none /ofw  promfs defaults 0 0

devpts                  /dev/pts                devpts  gid=5,mode=620    0 0
tmpfs                   /dev/shm                tmpfs   defaults,size=15% 0 0
proc                    /proc                   proc    defaults          0 0
sysfs                   /sys                    sysfs   defaults          0 0

=================== sda1: Location of files loaded by Grub: ===================


  97.6GB: boot/grub/menu.lst
  97.5GB: boot/grub/stage2
   4.6GB: boot/initrd.img-2.6.22-14-generic
   2.9GB: boot/initrd.img-2.6.22-14-generic.bak
    .7GB: boot/vmlinuz
   4.7GB: boot/vmlinuz-2.6.22-14-generic
    .7GB: boot/vmlinuz-2.6.22-20071121.7.olpc.af3dd731d18bc39
   4.6GB: initrd.img
   4.7GB: vmlinuz

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8b546fd8-856c-468b-baed-ac80dd5748df /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a0a67122-ca60-42ca-89e1-cc3ad46c1c36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 125.1GB: boot/vmlinuz-2.6.27-7-generic
 125.1GB: vmlinuz

```

---

### Post by caljohnsmith on 2009-02-05
I'm not sure exactly what you tried to do, but unfortunately you can't install Ubuntu's boot files or Grub to an NTFS partition like your Windows sda1 partition. Grub has no support for NTFS file systems. Did you set the sda1 partition with a mount point of "/boot" during the Ubuntu installation? If so, I would recommend not doing that, and instead just let the /boot directory go in your main sda6 Ubuntu install by not giving any partition a mount point of "/boot". How about trying that and let me know how it goes.

---

### Post by DMonkey08 on 2009-02-05
All I did  was specify the Ext3 partition (Ubuntu 8.04) to be formatted and used as "/".  Does 8.10 use a different filesystem?

---

### Post by caljohnsmith on 2009-02-05
8.10 still uses the same linux file systems as 8.04, like ext3 which you are trying to use. Did you by chance get your Ubuntu Live CD from a recent Linux magazine? If so, that might be the problem, because some recent Linux magazine unintentionally distributed a slightly corrupt CD copy of Ubuntu that doesn't install correctly. If that is not your case, can you run the "check CD for defects" option from the main menu when you boot the CD? Also, did you check the MD5 sum of the ISO image you burned? You might want to consider reburning a new CD and try that, and if you do I would recommend using a slow burning speed like 4X to help ensure an accurate burn.

---

### Post by michaelbgup on 2009-02-05
I have the same problem. I upgraded yesterday from 8.04 to 8.10. For some reason the grub did not update itself so I had to boot the older kernel (the menu had stayed the same.) I ran update-grub, looked at the resulting file, which looked good. Then I ran grub-install.

Now when I reboot, I see the updated menu, but each of the menu entries gives Error 15, file not found. However, if I use the liveCD to boot, and select the option boot from first HD, then I see the updated menu and I can successfully select the new kernel and it boots. !?  I have tried this sequence a few times now, and it mystifies me.  

Any ideas what to do now? thanks for any help.

I followed the instructions on this thread and ran the boot info script.

Here are the results of the boot script.
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       292968736 sectors, but according to the info from 
                       fdisk, it has 292977405 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 6.06.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 348851538.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 5.04 "Hoary Hedgehog"
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,798,319    16,798,257   c W95 FAT32 (LBA)
/dev/sda2    *     16,803,990   309,781,394   292,977,405   7 HPFS/NTFS
/dev/sda4         309,781,395   488,392,064   178,610,670   5 Extended
/dev/sda5         482,769,378   488,392,064     5,622,687  82 Linux swap / Solaris
/dev/sda6         309,781,521   329,316,434    19,534,914  83 Linux
/dev/sda7         329,316,498   348,851,474    19,534,977  83 Linux
/dev/sda8         348,851,538   358,618,994     9,767,457   c W95 FAT32 (LBA)
/dev/sda9         358,619,058   482,769,314   124,150,257  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31630066

Partition  Boot         Start           End          Size  Id System
/dev/sdb1                  63   185,550,749   185,550,687   c W95 FAT32 (LBA)
/dev/sdb2    *    308,576,520   312,576,704     4,000,185  82 Linux swap / Solaris
/dev/sdb3         185,550,750   308,576,519   123,025,770   5 Extended
/dev/sdb5         185,550,813   205,085,789    19,534,977  83 Linux
/dev/sdb6         205,085,853   224,620,829    19,534,977  83 Linux
/dev/sdb7         224,620,893   308,576,519    83,955,627  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="HP_RECOVERY" UUID="4303-5331" TYPE="vfat" 
/dev/sda2: UUID="2E709CCE709C9E61" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sda5: UUID="25896417-5b3c-4b31-82bf-91e403d03dcd" TYPE="swap" 
/dev/sda6: UUID="01547174-ea67-41ca-a4dc-1316c5bcf8bb" TYPE="reiserfs" 
/dev/sda7: UUID="e539d9e9-8f42-4997-ac99-fde9a5b72b13" TYPE="reiserfs" 
/dev/sda8: UUID="4459-61F3" TYPE="vfat" 
/dev/sda9: LABEL="/home" UUID="2a577d0b-35e5-4236-a6ea-1badc3fb24fe" TYPE="ext3" 
/dev/sdb1: LABEL="OCT2004" UUID="07E9-2B1B" TYPE="vfat" 
/dev/sdb2: UUID="536db259-018f-417a-8517-e2c6978c9c23" TYPE="swap" 
/dev/sdb5: LABEL="/" UUID="5dc801cd-db3b-4e24-9222-0a07adbdcfeb" TYPE="ext3" 
/dev/sdb6: LABEL="/mnt/part_alt" UUID="81f76baf-d06b-42a7-9fbb-5de9f2695ff0" TYPE="ext3" 
/dev/sdb7: LABEL="/home" UUID="50fadde1-18cc-49f8-9d6f-e582fcbc3e3e" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda6 on / type reiserfs (rw,notail)
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
/dev/sda9 on /home type ext3 (rw,relatime)
/dev/sdb1 on /media/hda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sdb5 on /media/hda5 type ext3 (rw,relatime)
/dev/sdb6 on /media/hda6 type ext3 (rw,relatime)
/dev/sdb7 on /media/hda7 type ext3 (rw,relatime)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7 on /media/sda7 type reiserfs (rw)
/dev/sda8 on /media/sda8 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

================================ sda2/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=01547174-ea67-41ca-a4dc-1316c5bcf8bb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

title           Ubuntu 7.10, kernel 2.6.27-11-generic
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=01547174-ea67-41ca-a4dc-1316c5bcf8bb ro quiet splash
initrd          /boot/initrd.img-2.6.27-11-generic
quiet

title           Ubuntu 7.10, kernel 2.6.27-11-generic (recovery mode)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=01547174-ea67-41ca-a4dc-1316c5bcf8bb ro single
initrd          /boot/initrd.img-2.6.27-11-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=01547174-ea67-41ca-a4dc-1316c5bcf8bb ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=01547174-ea67-41ca-a4dc-1316c5bcf8bb ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows 95/98/Me
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title           Ubuntu, kernel 2.6.10-5-386 (on /dev/hda5)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash 
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title           Ubuntu, kernel 2.6.10-5-386 (recovery mode) (on /dev/hda5)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro single 
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title           Ubuntu, kernel memtest86+ (on /dev/hda5)
root            (hd0,4)
kernel          /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title           Ubuntu, kernel 2.6.15-29-386 (on /dev/sda7)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/sda7 ro quiet splash 
initrd          /boot/initrd.img-2.6.15-29-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title           Ubuntu, kernel 2.6.15-29-386 (recovery mode) (on /dev/sda7)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/sda7 ro single 
initrd          /boot/initrd.img-2.6.15-29-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title           Ubuntu, memtest86+ (on /dev/sda7)
root            (hd1,6)
kernel          /boot/memtest86+.bin  
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=01547174-ea67-41ca-a4dc-1316c5bcf8bb /               reiserfs notail          0       1
# /dev/sda9
UUID=2a577d0b-35e5-4236-a6ea-1badc3fb24fe /home           ext3    defaults,relatime        0       2
# /dev/hda1
UUID=07E9-2B1B  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=5dc801cd-db3b-4e24-9222-0a07adbdcfeb /media/hda5     ext3    defaults,relatime        0       2
# /dev/hda6
UUID=81f76baf-d06b-42a7-9fbb-5de9f2695ff0 /media/hda6     ext3    defaults,relatime        0       2
# /dev/hda7
UUID=50fadde1-18cc-49f8-9d6f-e582fcbc3e3e /media/hda7     ext3    defaults,relatime        0       2
# /dev/sda1
UUID=4303-5331  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=2E709CCE709C9E61 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=e539d9e9-8f42-4997-ac99-fde9a5b72b13 /media/sda7     reiserfs defaults        0       2
# /dev/sda8
UUID=4459-61F3  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=536db259-018f-417a-8517-e2c6978c9c23 none            swap    sw              0       0
# /dev/sda5
UUID=25896417-5b3c-4b31-82bf-91e403d03dcd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

=================== sda6: Location of files loaded by Grub: ===================


 160.5GB: boot/grub/menu.lst
 160.5GB: boot/grub/stage2
 158.7GB: boot/initrd.img-2.6.22-14-generic
 158.8GB: boot/initrd.img-2.6.22-14-generic.bak
 159.0GB: boot/initrd.img-2.6.27-11-generic
 158.8GB: boot/vmlinuz-2.6.22-14-generic
 160.1GB: boot/vmlinuz-2.6.27-11-generic
 159.0GB: initrd.img
 160.1GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##
title           Ubuntu, kernel 2.6.22-14-generic (7.10)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda6 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot

title           Ubuntu, kernel 2.6.22-14-generic (7.10)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda6 ro single
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Ubuntu, kernel 2.6.15-29-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.15-29-386
boot

title           Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.15-29-386
boot


title           Ubuntu, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin 
boot
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu, kernel 2.6.15-26-amd64-k8 Default (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz root=/dev/sda6 ro quiet splash 
initrd          /boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu, kernel 2.6.15-26-amd64-k8 Default (recovery mode) (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz root=/dev/sda6 ro single 
initrd          /boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu, kernel 2.6.15-23-amd64-generic Previous (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz.old root=/dev/sda6 ro quiet splash 
initrd          /boot/initrd.img.old
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu, memtest86+ (on /dev/sda6)
root            (hd0,5)
kernel          /boot/memtest86+.bin  
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               reiserfs notail          0       1
/dev/sda9       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs-3g    defaults,locale=en_US.utf8  0       0
/dev/sda6       /media/sda6     reiserfs defaults        0       2
/dev/sda8       /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda7: Location of files loaded by Grub: ===================


 173.0GB: boot/grub/menu.lst
 171.0GB: boot/grub/stage2
 168.7GB: boot/initrd.img-2.6.15-26-386
 171.0GB: boot/initrd.img-2.6.15-27-386
 171.0GB: boot/initrd.img-2.6.15-28-386
 171.1GB: boot/initrd.img-2.6.15-29-386
 171.0GB: boot/vmlinuz-2.6.15-26-386
 171.0GB: boot/vmlinuz-2.6.15-27-386
 171.0GB: boot/vmlinuz-2.6.15-28-386
 171.1GB: boot/vmlinuz-2.6.15-29-386
 171.1GB: initrd.img
 171.0GB: initrd.img.old
 171.1GB: vmlinuz
 171.0GB: vmlinuz.old

=========================== sdb5/boot/grub/menu.lst: ===========================

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.10-5-386 
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+ 
root            (hd0,4)
kernel          /boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb7.
title           Ubuntu, kernel 2.6.10-5-386 (on /dev/hdb7)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hdb7 ro quiet splash 
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb7.
title           Ubuntu, kernel 2.6.10-5-386 (recovery mode) (on /dev/hdb7)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hdb7 ro single 
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb7.
title           Ubuntu, kernel memtest86+ (on /dev/hdb7)
root            (hd1,6)
kernel          /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Windows 95/98/Me
root            (hd1,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows 95/98/Me
root            (hd0,0)
savedefault
makeactive
chainloader     +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/windows    vfat    umask=0222      0       0


=================== sdb5: Location of files loaded by Grub: ===================


 101.0GB: boot/grub/menu.lst
 101.0GB: boot/grub/stage2
 101.0GB: boot/initrd.img-2.6.10-5-386
 101.1GB: boot/vmlinuz-2.6.10-5-386
 101.0GB: initrd.img
 101.1GB: vmlinuz

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb6

00000000  89 63 77 62 7d 48 49 90  b5 71 53 b7 da 6b 24 c9  |.cwb}HI..qS..k$.|
00000010  a3 0f 28 26 c3 91 65 e3  72 12 b3 f6 17 c0 86 42  |..(&..e.r......B|
00000020  dd f7 a3 54 23 e0 ba 7a  35 e9 a4 f8 46 31 68 03  |...T#..z5...F1h.|
00000030  e2 ab 9c 87 f7 43 a0 9b  6c fd 5f dc 09 f7 61 cc  |.....C..l._...a.|
00000040  3f 71 27 6f db 61 dc ff  01 77 62 d0 9a fe b2 39  |?q'o.a...wb....9|
00000050  ee 33 d3 de c2 74 ec 8c  83 96 f2 22 f7 bb af 6d  |.3...t....."...m|
00000060  f9 c5 76 1e 70 3a f2 00  95 11 74 77 bc 38 88 54  |..v.p:....tw.8.T|
00000070  d2 9a 85 71 ca 4f fb c3  85 ae a9 07 f4 cf bb 78  |...q.O.........x|
00000080  3a bc 26 2f d8 75 42 b2  e5 a6 ca b3 24 5b d3 ac  |:.&/.uB.....$[..|
00000090  e0 43 dc 06 75 96 cb bb  5c df ce 04 2e 8b 18 84  |.C..u...\.......|
000000a0  60 87 0b 0b 8b 8b 0c 6b  36 94 8f 91 2c 06 33 d5  |`......k6...,.3.|
000000b0  8e 21 24 8e 8e 84 f7 a0  50 eb 83 f7 33 65 f4 cb  |.!$.....P...3e..|
000000c0  36 e4 a4 2b 1b b9 5b b2  6c 17 b4 18 88 df 57 5d  |6..+..[.l.....W]|
000000d0  d5 56 37 22 f2 64 49 3f  3f ac a3 ec c9 ca 4f 55  |.V7".dI??.....OU|
000000e0  f1 11 37 2e 36 64 8d 7c  98 81 c5 cd 8d 60 8a 3d  |..7.6d.|.....`.=|
000000f0  9a f1 85 da 5c 30 9c 16  f1 7b fc ce 3c 43 b8 26  |....\0...{..<C.&|
00000100  41 8f 37 3a ef 75 fd bf  d8 56 da c8 b6 87 11 13  |A.7:.u...V......|
00000110  c5 ea d7 ab f5 a1 34 e2  f9 4c a7 0f 23 48 f2 83  |......4..L..#H..|
00000120  4e 05 f3 9c 59 77 9a 5f  99 23 f0 af ec 94 94 f8  |N...Yw._.#......|
00000130  2d 85 da 15 10 e8 64 ed  72 a9 af 08 f8 f1 c2 bb  |-.....d.r.......|
00000140  3c d0 f0 af 1c e9 d0 d9  2d 16 d3 0a 3d 22 43 11  |<.......-...="C.|
00000150  fc 33 30 37 f1 f6 fc c4  14 dc e7 b7 77 21 4d 40  |.307........w!M@|
00000160  01 aa 6a 8d ba 34 3f c8  be 5c d5 4c 02 55 32 79  |..j..4?..\.L.U2y|
00000170  80 dc 1e 7a 23 9e 3e de  32 be 87 bd fd 30 be d5  |...z#.>.2....0..|
00000180  91 dc b6 9c d6 aa 05 83  7e 9f 71 cd 74 99 29 04  |........~.q.t.).|
00000190  ee 90 92 d8 04 73 6d 92  cc bb 50 2b 96 d7 57 4f  |.....sm...P+..WO|
000001a0  83 72 47 95 ab f5 c5 b3  ed cd 25 dd 45 68 bf 92  |.rG.......%.Eh..|
000001b0  ba 72 6f 82 af 5f 34 c5  d6 75 bc 17 52 64 55 b0  |.ro.._4..u..RdU.|
000001c0  82 13 27 d1 e9 d9 11 01  f1 b7 69 bf a1 f9 d8 51  |..'.......i....Q|
000001d0  37 c1 80 f9 33 2d dd f9  16 c0 6a 9b 3f 2a fb 2b  |7...3-....j.?*.+|
000001e0  07 ba ce c6 78 10 b9 df  51 94 94 a6 3a 8a 1d cd  |....x...Q...:...|
000001f0  20 72 4a 46 f9 c2 f8 6d  1a 6a b7 91 7a 43 98 ac  | rJF...m.j..zC..|
00000200

Unknown BootLoader  on sdb7

00000000  ae 3c 92 c1 43 ba 05 9e  be cb f2 54 d2 bc ce ec  |.<..C......T....|
00000010  f4 48 2d a1 21 52 54 22  c4 ed 89 67 31 bb 1a 12  |.H-.!RT"...g1...|
00000020  56 28 ed a9 9e 73 89 a0  3b 28 30 a6 25 7f c0 7b  |V(...s..;(0.%..{|
00000030  d8 89 2f 75 4e ae ba 19  bd a6 25 a0 48 42 eb ed  |../uN.....%.HB..|
00000040  d9 99 e2 35 4a 38 ea 6a  66 22 35 59 71 0a cc 6b  |...5J8.jf"5Yq..k|
00000050  5a 52 11 5c 48 4b 8f e7  6d 09 cd b9 91 31 34 31  |ZR.\HK..m....141|
00000060  de 5e f8 06 a0 42 7c e7  c0 33 be 84 70 0e 0c 27  |.^...B|..3..p..'|
00000070  59 00 0e 47 8f 0a 54 a0  37 7e 89 00 c8 2c 83 01  |Y..G..T.7~...,..|
00000080  15 85 19 7d 9a 01 95 3d  a7 3f 58 e2 70 1c 92 18  |...}...=.?X.p...|
00000090  51 2d 38 ac 6a 83 a0 07  a0 17 21 69 2c 02 44 7b  |Q-8.j.....!i,.D{|
000000a0  ad 21 cd 5b 36 60 1f d2  5b f6 30 97 22 c6 43 43  |.!.[6`..[.0.".CC|
000000b0  36 e4 fa 6f 36 1a 5a fa  a7 bc b0 85 e3 bc f7 7f  |6..o6.Z.........|
000000c0  58 bb b3 e1 ba 88 d5 ac  76 d3 9c 81 04 74 b0 c6  |X.......v....t..|
000000d0  df 1e e6 ad 56 1e e1 d6  46 88 90 96 3d 07 19 5d  |....V...F...=..]|
000000e0  8d ba 66 22 07 c7 0b be  ce 91 6f b3 a0 1f da ce  |..f"......o.....|
000000f0  95 a7 22 64 b6 6f 66 53  e8 75 93 09 09 e9 b7 9d  |.."d.ofS.u......|
00000100  36 75 ed a3 b6 22 25 d2  ae fa 86 76 71 ec 7c 2a  |6u..."%....vq.|*|
00000110  35 89 0c a3 98 7d a4 10  32 23 7e 56 32 4a 72 5d  |5....}..2#~V2Jr]|
00000120  8c d3 b3 04 d0 d1 64 a1  5c 0d d0 aa 49 ec 69 1b  |......d.\...I.i.|
00000130  66 fc 32 95 9c 96 05 85  3e a8 49 96 b1 19 23 04  |f.2.....>.I...#.|
00000140  df 0c 65 7a e2 b2 ec da  64 65 ca 29 88 32 e4 9d  |..ez....de.).2..|
00000150  4d 38 53 4c da bb 10 3e  89 6c 78 4e 4e 0f a1 98  |M8SL...>.lxNN...|
00000160  c4 ca 84 6a 4d d8 44 84  f7 61 02 4d de 93 99 9b  |...jM.D..a.M....|
00000170  4e 69 d5 74 da ca ec d6  21 25 21 86 b2 68 66 88  |Ni.t....!%!..hf.|
00000180  a6 9d 11 ed 61 84 6a 19  9d 94 45 a1 a0 96 c3 12  |....a.j...E.....|
00000190  15 0f b5 01 61 39 0c 62  32 52 e4 ca 99 33 24 26  |....a9.b2R...3$&|
000001a0  23 21 ab 4c 9a 32 89 6e  6b 0b 91 b5 48 cc 99 cd  |#!.L.2.nk...H...|
000001b0  85 01 6e 92 1b 36 46 36  49 ca dd 43 71 19 b6 ec  |..n..6F6I..Cq...|
000001c0  eb 5a 94 e5 a0 d6 a5 4c  b9 a2 d3 28 f1 23 a3 f7  |.Z.....L...(.#..|
000001d0  74 30 e0 9c f4 49 43 0e  53 8f 92 94 25 07 da 8d  |t0...IC.S...%...|
000001e0  48 52 ee d6 59 fc 85 09  8e 37 c1 03 4f 7c 50 be  |HR..Y....7..O|P.|
000001f0  bb c1 80 50 79 c7 81 1a  69 f5 07 c4 69 05 a1 39  |...Py...i...i..9|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

 sdc .
 sdd .
000001e0  07 ba ce c6 78 10 b9 df  51 94 94 a6 3a 8a 1d cd  |....x...Q...:...|
000001f0  20 72 4a 46 f9 c2 f8 6d  1a 6a b7 91 7a 43 98 ac  | rJF...m.j..zC..|
00000200

Unknown BootLoader  on sdb7

00000000  ae 3c 92 c1 43 ba 05 9e  be cb f2 54 d2 bc ce ec  |.<..C......T....|
00000010  f4 48 2d a1 21 52 54 22  c4 ed 89 67 31 bb 1a 12  |.H-.!RT"...g1...|
00000020  56 28 ed a9 9e 73 89 a0  3b 28 30 a6 25 7f c0 7b  |V(...s..;(0.%..{|
00000030  d8 89 2f 75 4e ae ba 19  bd a6 25 a0 48 42 eb ed  |../uN.....%.HB..|
00000040  d9 99 e2 35 4a 38 ea 6a  66 22 35 59 71 0a cc 6b  |...5J8.jf"5Yq..k|
00000050  5a 52 11 5c 48 4b 8f e7  6d 09 cd b9 91 31 34 31  |ZR.\HK..m....141|
00000060  de 5e f8 06 a0 42 7c e7  c0 33 be 84 70 0e 0c 27  |.^...B|..3..p..'|
00000070  59 00 0e 47 8f 0a 54 a0  37 7e 89 00 c8 2c 83 01  |Y..G..T.7~...,..|
00000080  15 85 19 7d 9a 01 95 3d  a7 3f 58 e2 70 1c 92 18  |...}...=.?X.p...|
00000090  51 2d 38 ac 6a 83 a0 07  a0 17 21 69 2c 02 44 7b  |Q-8.j.....!i,.D{|
000000a0  ad 21 cd 5b 36 60 1f d2  5b f6 30 97 22 c6 43 43  |.!.[6`..[.0.".CC|
000000b0  36 e4 fa 6f 36 1a 5a fa  a7 bc b0 85 e3 bc f7 7f  |6..o6.Z.........|
000000c0  58 bb b3 e1 ba 88 d5 ac  76 d3 9c 81 04 74 b0 c6  |X.......v....t..|
000000d0  df 1e e6 ad 56 1e e1 d6  46 88 90 96 3d 07 19 5d  |....V...F...=..]|
000000e0  8d ba 66 22 07 c7 0b be  ce 91 6f b3 a0 1f da ce  |..f"......o.....|
000000f0  95 a7 22 64 b6 6f 66 53  e8 75 93 09 09 e9 b7 9d  |.."d.ofS.u......|
00000100  36 75 ed a3 b6 22 25 d2  ae fa 86 76 71 ec 7c 2a  |6u..."%....vq.|*|
00000110  35 89 0c a3 98 7d a4 10  32 23 7e 56 32 4a 72 5d  |5....}..2#~V2Jr]|
00000120  8c d3 b3 04 d0 d1 64 a1  5c 0d d0 aa 49 ec 69 1b  |......d.\...I.i.|
00000130  66 fc 32 95 9c 96 05 85  3e a8 49 96 b1 19 23 04  |f.2.....>.I...#.|
00000140  df 0c 65 7a e2 b2 ec da  64 65 ca 29 88 32 e4 9d  |..ez....de.).2..|
00000150  4d 38 53 4c da bb 10 3e  89 6c 78 4e 4e 0f a1 98  |M8SL...>.lxNN...|
00000160  c4 ca 84 6a 4d d8 44 84  f7 61 02 4d de 93 99 9b  |...jM.D..a.M....|
00000170  4e 69 d5 74 da ca ec d6  21 25 21 86 b2 68 66 88  |Ni.t....!%!..hf.|
00000180  a6 9d 11 ed 61 84 6a 19  9d 94 45 a1 a0 96 c3 12  |....a.j...E.....|
00000190  15 0f b5 01 61 39 0c 62  32 52 e4 ca 99 33 24 26  |....a9.b2R...3$&|
000001a0  23 21 ab 4c 9a 32 89 6e  6b 0b 91 b5 48 cc 99 cd  |#!.L.2.nk...H...|
000001b0  85 01 6e 92 1b 36 46 36  49 ca dd 43 71 19 b6 ec  |..n..6F6I..Cq...|
000001c0  eb 5a 94 e5 a0 d6 a5 4c  b9 a2 d3 28 f1 23 a3 f7  |.Z.....L...(.#..|
000001d0  74 30 e0 9c f4 49 43 0e  53 8f 92 94 25 07 da 8d  |t0...IC.S...%...|
000001e0  48 52 ee d6 59 fc 85 09  8e 37 c1 03 4f 7c 50 be  |HR..Y....7..O|P.|
000001f0  bb c1 80 50 79 c7 81 1a  69 f5 07 c4 69 05 a1 39  |...Py...i...i..9|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

 sdc .
 sdd .
 sde .
 sdf .
```

---

### Post by DMonkey08 on 2009-02-06
I tried installing it with two different, burned cds that were verified for accuracy.

And my problem's not quit the same michael, since I'm not getting the menu at all.

---

### Post by michaelbgup on 2009-02-06
I thought it was similar enough. Same error number, grub problem due to installation/upgrade to 8.10 ubuntu.

I figure someone able to answer your question could answer mine with little extra trouble.

Have you tried booting into the LiveCD and doing the update-grub, grub-install in a shell?  Then you might get the same setup as me which is at least bootable with the CD.  

8.1 is pretty neat, my graphics drivers work a lot better than they did.

---

### Post by caljohnsmith on 2009-02-06
**Michaelbgup**, I know it may seem like your issue is similar to DMonkey08's problem, but actually it isn't; getting an error 15 before even seeing the Grub menu is much different than getting a Grub error 15 when you select an OS to boot in the Grub menu. But to answer you question, it looks like your issue is that your sda6 menu.lst file is currently configured to work only if you boot your 160 GB sdb drive on start up. If you instead boot your sda drive, you will still get the Grub menu because both your drives have Grub installed to the MBR (Master Boot Record), but choosing any of the OS entries will give you a Grub error 15. Therefore, I would recommend changing your menu.lst so you can boot from your sda drive:
```
gksudo gedit /boot/grub/menu.lst
```
And change all the Ubuntu entries to use (hd0,5) instead of (hd1,5) similar to:
```
title           Ubuntu 7.10, kernel 2.6.27-11-generic
root            [COLOR="Blue"](hd0,5)[/COLOR]
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=01547174-ea67-41ca-a4dc-1316c5bcf8bb ro quiet splash
initrd          /boot/initrd.img-2.6.27-11-generic
quiet
```
And just as important, change the "#groot=(hd1,5)" line:
```
#groot=[COLOR="Blue"](hd0,5)[/COLOR]
```
That way when you get a kernel upgrade your menu.lst shouldn't break again. After making the changes, you should be able to boot from your sda drive again. Let me know if that works or not.

**DMonkey08**, do you get any errors during the installation? Does the installer say it completes successfully, or what exactly happens? Are you changing any of the settings under the "Advanced" button near the end of the installation process? Are you only setting a mount point for root "/" and "swap" during the installation?

---

### Post by dburnett77 on 2009-02-06
> **DMonkey08 said:**
> I've tried several times to install Ubuntu 8.10 on two different computers, but on each computer grub gives me "grub error 15" on boot (no menu or anything), and have had to re-install 8.04.  Both computers are dual-booted with XP, and when I tried to upgrade 8.04, it gave me grub error 17.

8.10 looks really slick, and I would like to install.  I'm confused as to why this problem would happen on two separate computers.  Can anyone help :confused:?

Could be a microKernel that defeats uninstall, and corrupts installation.  I've had two myself just this week.

GParted is a boot disk you can use, and sometimes a manual configuration of your partitions will help.

If that is the problem, try writing a new boot sector by relaying the drive structure, via "new partition table".  Can be done with fdisk, parted, or in somedistros it's an option during partitioning.

---

### Post by caljohnsmith on 2009-02-06
> **dburnett77 said:**
> 
If that is the problem, try writing a new boot sector by relaying the drive structure, via "new partition table".  Can be done with fdisk, parted, or in somedistros it's an option during partitioning.
Unless you want to erase your existing partition table and start with a HDD that appears completely unformatted, DMonkey08, I would not recommend creating a new partition table with "new partition table." I've looked over your current partition table carefully, and I don't see anything wrong with it, but maybe dburnett77 sees something I'm not catching. Do you see something wrong with the partition table, dburnett77, or why are you recommending creating an entirely new one to erase the old one? Please explain your advice.

---

### Post by DMonkey08 on 2009-02-06
> **caljohnsmith said:**
> **DMonkey08**, do you get any errors during the installation? Does the installer say it completes successfully, or what exactly happens? Are you changing any of the settings under the "Advanced" button near the end of the installation process? Are you only setting a mount point for root "/" and "swap" during the installation?

Exactly what I do: I go into manual partition, and edit the ext3 partition, tell Ubuntu to use it as an ext3 partition, format it, and use it as root.  Then I go on, no errors or anything.  I don't recall clicking an "Advanced" button at any point.  The last time I tried to install it, it hung up while configure apt (I think it was doing something with the mirrors), but the system was already install, and it's installed completely before  with the same problem.

Edit: and BTW, it does not do anything to corrupt the hard drive, since after reinstalling 8.04 my Windows partition is just like I left it.

---

### Post by DMonkey08 on 2009-02-07
OK, problem solved.  I have no idea why, but I tried reinstalling it and it just worked this time :D.  Very odd, but whatever.

---

