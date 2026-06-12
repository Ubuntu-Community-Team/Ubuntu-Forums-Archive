---
title: "Help! GRUB screwed up my Windows Install!"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by ub0 on 2009-02-14
I had Windows XP on a separate hard drive and just installed Ubuntu 8.10 with GRUB on another hard drive...and thought I could do a dual boot.

GRUB didn't recognize my Windows XP installation, so I manually added it in there:

```

title		Windows XP Pro SP2
root		(hd0,0)
makeactive
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		397648e4-aba8-4639-ad51-8ae6222f912d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=397648e4-aba8-4639-ad51-8ae6222f912d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		397648e4-aba8-4639-ad51-8ae6222f912d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=397648e4-aba8-4639-ad51-8ae6222f912d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		397648e4-aba8-4639-ad51-8ae6222f912d
kernel		/boot/memtest86+.bin
quiet

```

When trying to boot in Windows, I now get "NTDLR is missing"....Does that mean I'm screwed and will have to reinstall Windows? How can I get this working???

I have 3 hard drives..the first one in the BIOS boot order is my SATA drive with Windows on it. The second is a 120GB IDE where I put Ubuntu, and the 3rd is a backup 320 GB drive NTFS partition for my backup windows files. 

Here's what my fdisk says:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d563d55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120000061440 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb83d441b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13991   112382676   83  Linux
/dev/sdb2           13992       14589     4803435    5  Extended
/dev/sdb5           13992       14589     4803403+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd14c7e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

```

---

### Post by caljohnsmith on 2009-02-14
How about trying these two entries for Windows:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Let me know exactly what happens when you choose them from the Grub menu, and we can work from there if necessary.

---

### Post by ub0 on 2009-02-14
> **caljohnsmith said:**
> How about trying these two entries for Windows:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Let me know exactly what happens when you choose them from the Grub menu, and we can work from there if necessary.

Hey - I just tried this and for the 1st option I get:

"Error 13: Invalid or unsupported executable format"

and for the 2nd option I get the same "NTDLR is missing" error....

---

### Post by caljohnsmith on 2009-02-14
OK, in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by ub0 on 2009-02-14
Here it is

................
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3d563d55

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120000061440 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb83d441b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   224,765,414   224,765,352  83 Linux
/dev/sdb2         224,765,415   234,372,284     9,606,870   5 Extended
/dev/sdb5         224,765,478   234,372,284     9,606,807  82 Linux swap / Solaris


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfd14c7e2

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="04C413A8C4139ACE" LABEL="SATA" TYPE="ntfs" 
/dev/sdb1: UUID="397648e4-aba8-4639-ad51-8ae6222f912d" TYPE="ext3" 
/dev/sdb5: UUID="6817b571-ef82-410d-abd3-db81c09b5138" TYPE="swap" 
/dev/sdc1: UUID="2270328B70326627" LABEL="backup" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/gangstapimp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gangstapimp)

=========================== sdb1/boot/grub/menu.lst: ===========================

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
timeout		5

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
# kopt=root=UUID=397648e4-aba8-4639-ad51-8ae6222f912d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=397648e4-aba8-4639-ad51-8ae6222f912d

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

title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1


title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		397648e4-aba8-4639-ad51-8ae6222f912d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=397648e4-aba8-4639-ad51-8ae6222f912d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		397648e4-aba8-4639-ad51-8ae6222f912d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=397648e4-aba8-4639-ad51-8ae6222f912d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		397648e4-aba8-4639-ad51-8ae6222f912d
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=397648e4-aba8-4639-ad51-8ae6222f912d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=6817b571-ef82-410d-abd3-db81c09b5138 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  38.6GB: boot/grub/menu.lst
  38.7GB: boot/grub/stage2
  38.7GB: boot/initrd.img-2.6.27-7-generic
  38.7GB: boot/vmlinuz-2.6.27-7-generic
  38.7GB: initrd.img
  38.7GB: vmlinuz

```

---

### Post by caljohnsmith on 2009-02-14
OK, your Windows partition is missing its boot files, so what might have happened is Windows originally put its boot files on the sdb drive, but then you installed Ubuntu and used that entire drive (and thus unintentionally deleted the Windows boot files). Anyway, to fix the problem, how about downloading the attached "WinXP_boot_files1.zip" to your Ubuntu desktop and do:
```
sudo mount /dev/sda1 /mnt
cd ~/Desktop
unzip WinXP_boot_files1.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Also, make sure you are using your original Grub entry to boot Windows:
```
title		Windows XP Pro SP2
root		(hd0,0)
makeactive
chainloader	+1

```
Then reboot, try XP from your Grub menu, and let me know how far you get. We can work from there if necessary.

---

### Post by ub0 on 2009-02-14
> **caljohnsmith said:**
> OK, your Windows partition is missing its boot files, so what might have happened is Windows originally put its boot files on the sdb drive, but then you installed Ubuntu and used that entire drive (and thus unintentionally deleted the Windows boot files). Anyway, to fix the problem, how about downloading the attached "WinXP_boot_files1.zip" to your Ubuntu desktop and do:
```
sudo mount /dev/sda1 /mnt
cd ~/Desktop
unzip WinXP_boot_files1.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Also, make sure you are using your original Grub entry to boot Windows:
```
title		Windows XP Pro SP2
root		(hd0,0)
makeactive
chainloader	+1

```
Then reboot, try XP from your Grub menu, and let me know how far you get. We can work from there if necessary.

Wow...that worked!!! Can't thak you enough1!!!

I know this isn't your fault or anything, but why doesn't this work by default? It doesn't make sense to me that the latest version of Ubuntu is unable to recognize where the Windows partition and MBR is...and then work around that so that GRUB loads up the correct partitions for each OS.

Having to do all these manual installs and tests wasn't that painful for me...but for someone completely new to Linux this would be a nightmare....Just seems like it should be a lot smarter and intuitive.

but anyway, thanks again!!!! you saved me!

---

### Post by darco on 2009-02-14
Excellent help there CalJohn!..Thats what makes Ubuntu the best forum for helping out fellow 'nix users!

darco

---

### Post by caljohnsmith on 2009-02-14
> **ub0 said:**
> 
I know this isn't your fault or anything, but why doesn't this work by default? It doesn't make sense to me that the latest version of Ubuntu is unable to recognize where the Windows partition and MBR is...and then work around that so that GRUB loads up the correct partitions for each OS.

I think you might be misunderstanding; it is not Ubuntu's fault that your Windows partition is missing its boot files if you accidentally installed Ubuntu to the drive where Windows had its boot files originally. It's entirely up to you as the user where you install Ubuntu to, so if you install Ubuntu over a partition that has Windows' boot files, that's not Ubuntu's fault. The problem is that Windows sometimes puts its boot files on a drive/partition that is different from the main Windows partition in order to boot. I think that is most likely what happened in your case. Anyway, I'm glad you can boot Windows now; cheers and enjoy your new Ubuntu install. :)

---

