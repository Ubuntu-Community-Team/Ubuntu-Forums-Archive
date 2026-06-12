---
title: "Formatting issues with dual boot?"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by space-litter on 2009-11-03
I have a Jaunty/Vista dual boot right now, and want to install the new GRUB and ext4 filing system along with Karmic. I also want to divide my /, /home, and /swap partitions. I was under the impression that by simply using a LiveCD and formatting my Linux partition, I could do this. The problem is, for some reason ntfs has hijacked two partitions already. Here is how my gparted reads:

sda1: 1.5 gigs (ntfs)
sda2: 69.4 gigs (ntfs)

sda5: 110.7 gigs (ext3)
sda6: 4.7 gigs (swap)

Obviously, I cannot have 3 linux partitions unless I can consolidate the ntfs partitions. Is there a way to do this in gparted? So far, I can delete/format sda1 during the install in gparted but I see no way to merge it with anything else. I don't want dead space.

---

### Post by space-litter on 2009-11-03
Also, sda2 is obviously the Vista/Longhorn loader. But I do not recall making sda1, and have no idea what its purpose is. Furthermore, nothing shows up in gparted.

---

### Post by arubislander on 2009-11-03
I'm assuming you want to do a fresh install of Karmic without preserving your Jaunty install. Then I would suggest when you reach the partitioning phase during the Karmic install you choose manual partitioning and delete sda5 and create two partitions in it's stead, one for / and one for /home. You can reuse the swap partition.

You cannot have more than 4 primary partitions, but it's clear by their numbering (sda5, sda6) that these are logical partitions, where the limit does not apply.

---

### Post by space-litter on 2009-11-03
I cannot create any new partitions until I eliminate one first. I have a single hard drive, so unless I can incorporate sda1 into sda2, i cannot create even one partition

---

### Post by sliketymo on 2009-11-03
sda1 is probably your windows MBR/Recovery/Diagnostic partition.
Here is some good info :

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by arubislander on 2009-11-03
> **space-litter said:**
> I cannot create any new partitions until I eliminate one first. I have a single hard drive, so unless I can incorporate sda1 into sda2, i cannot create even one partition

Correct me if I'm wrong, but my guess is you can't create any partitions because there is no unpartitioned space left on your hard disk.

It seems you already have an extended partition with partitions sda5 and sda6 as logical partitions on said extended partition.
If you don't care for the contents of sda5 you can delete that and create two partitions for / and /home in it's place.

---

### Post by space-litter on 2009-11-03
> **sliketymo said:**
> sda1 is probably your windows MBR/Recovery/Diagnostic partition.
Here is some good info :

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Ugh, so I am stuck with /home and / both being on the same partition unless I eliminate Vista? Or is there a way to merge sda1 and sda2? I did not notice a procedure for that in the link, but thank you for it as it was very informative.

As much as I would like to, going fully to Ubuntu is not an option for various reasons.

---

### Post by space-litter on 2009-11-03
> **arubislander said:**
> Correct me if I'm wrong, but my guess is you can't create any partitions because there is no unpartitioned space left on your hard disk.

It seems you already have an extended partition with partitions sda5 and sda6 as logical partitions on said extended partition.
If you don't care for the contents of sda5 you can delete that and create two partitions for / and /home in it's place.

I cannot "create" new partitions because 4 is the max for a single hard drive. I do not in fact care about sda5 as it is Jaunty and ext3, which I plan to format and replace with Karmic and ext4. Unfortunately though, I cannot convert it into a separate / and /home at this time due to ntfs hogging two rather than one partition.

---

### Post by space-litter on 2009-11-03
> **arubislander said:**
> I'm assuming you want to do a fresh install of Karmic without preserving your Jaunty install. Then I would suggest when you reach the partitioning phase during the Karmic install you choose manual partitioning and delete sda5 and create two partitions in it's stead, one for / and one for /home. You can reuse the swap partition.

You cannot have more than 4 primary partitions, but it's clear by their numbering (sda5, sda6) that these are logical partitions, where the limit does not apply.

Sorry, totally overlooked this. I do not see an option to split sda5 into two partitions in gparted...do I need to format it first or what?

---

### Post by space-litter on 2009-11-03
Also, do I need to format and replace the /swap to make it compatible with ext4, or does it simply adapt to whatever is using it?

---

### Post by presence1960 on 2009-11-03
boot from the Live CD and resize sda5 from gparted. You can not alter a mounted partition so boot from the Live Cd or gparted Live CD.

I would feel more comfortable if I knew a little more about your setup other than conjecture about what partitions may be what. Please do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by space-litter on 2009-11-03
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8eae67a6

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   148,622,876   145,548,829   7 HPFS/NTFS
/dev/sda3         148,633,380   390,716,864   242,083,485   5 Extended
/dev/sda5         148,633,443   380,788,694   232,155,252  83 Linux
/dev/sda6         380,788,758   390,716,864     9,928,107  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="40FA4A5DFA4A4EFA" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="50A051ECA051D954" LABEL="SQ004388V06" TYPE="ntfs" 
/dev/sda5: UUID="dfa4f7fb-1188-44e9-b827-25a74a46b54e" TYPE="ext3" 
/dev/sda6: UUID="36a86393-d2e4-416d-92a3-defca9852d82" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=chris)


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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e ro

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
# howmany=2

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

title		Ubuntu 9.04, kernel 2.6.30-02063003-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.30-02063003-generic root=UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e ro quiet splash 
initrd		/boot/initrd.img-2.6.30-02063003-generic
quiet

title		Ubuntu 9.04, kernel 2.6.30-02063003-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.30-02063003-generic root=UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e ro  single
initrd		/boot/initrd.img-2.6.30-02063003-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
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
UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=36a86393-d2e4-416d-92a3-defca9852d82 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 134.3GB: boot/grub/menu.lst
 134.3GB: boot/grub/stage2
 134.4GB: boot/initrd.img-2.6.24-24-generic
 134.4GB: boot/initrd.img-2.6.24-24-generic.bak
 134.3GB: boot/initrd.img-2.6.27-14-generic
 134.3GB: boot/initrd.img-2.6.28-15-generic
 134.4GB: boot/initrd.img-2.6.28-16-generic
 134.4GB: boot/initrd.img-2.6.30-02063003-generic
 134.4GB: boot/vmlinuz-2.6.24-24-generic
 134.4GB: boot/vmlinuz-2.6.27-14-generic
 134.4GB: boot/vmlinuz-2.6.28-15-generic
 134.3GB: boot/vmlinuz-2.6.28-16-generic
 134.4GB: boot/vmlinuz-2.6.30-02063003-generic
 134.4GB: initrd.img
 134.4GB: initrd.img.old
 134.3GB: vmlinuz
 134.4GB: vmlinuz.old
```

This is how my machine stands now, before the format/install. I have a LiveCD on hand but currently am still on Jaunty. When I encountered this issue, I canceled my install and came back here for input. I have been using Ubuntu for a while now, but still need my hand held for most things as it has usually run "out of the box" for me on this laptop. I freely admit that I am a newbie and in fact don't understand most of what I just posted for you lol. Formatting is especially daunting for me as it is imperative that Vista remain untouched and accessible after I do this fresh install.

Also, this is from a normal boot not the LiveCD. Not sure if that matters.

---

### Post by presence1960 on 2009-11-03
> **space-litter said:**
> ```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8eae67a6

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   148,622,876   145,548,829   7 HPFS/NTFS
/dev/sda3         148,633,380   390,716,864   242,083,485   5 Extended
/dev/sda5         148,633,443   380,788,694   232,155,252  83 Linux
/dev/sda6         380,788,758   390,716,864     9,928,107  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="40FA4A5DFA4A4EFA" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="50A051ECA051D954" LABEL="SQ004388V06" TYPE="ntfs" 
/dev/sda5: UUID="dfa4f7fb-1188-44e9-b827-25a74a46b54e" TYPE="ext3" 
/dev/sda6: UUID="36a86393-d2e4-416d-92a3-defca9852d82" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=chris)


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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e ro

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
# howmany=2

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

title		Ubuntu 9.04, kernel 2.6.30-02063003-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.30-02063003-generic root=UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e ro quiet splash 
initrd		/boot/initrd.img-2.6.30-02063003-generic
quiet

title		Ubuntu 9.04, kernel 2.6.30-02063003-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.30-02063003-generic root=UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e ro  single
initrd		/boot/initrd.img-2.6.30-02063003-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
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
UUID=dfa4f7fb-1188-44e9-b827-25a74a46b54e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=36a86393-d2e4-416d-92a3-defca9852d82 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 134.3GB: boot/grub/menu.lst
 134.3GB: boot/grub/stage2
 134.4GB: boot/initrd.img-2.6.24-24-generic
 134.4GB: boot/initrd.img-2.6.24-24-generic.bak
 134.3GB: boot/initrd.img-2.6.27-14-generic
 134.3GB: boot/initrd.img-2.6.28-15-generic
 134.4GB: boot/initrd.img-2.6.28-16-generic
 134.4GB: boot/initrd.img-2.6.30-02063003-generic
 134.4GB: boot/vmlinuz-2.6.24-24-generic
 134.4GB: boot/vmlinuz-2.6.27-14-generic
 134.4GB: boot/vmlinuz-2.6.28-15-generic
 134.3GB: boot/vmlinuz-2.6.28-16-generic
 134.4GB: boot/vmlinuz-2.6.30-02063003-generic
 134.4GB: initrd.img
 134.4GB: initrd.img.old
 134.3GB: vmlinuz
 134.4GB: vmlinuz.old
```

This is how my machine stands now, before the format/install. I have a LiveCD on hand but currently am still on Jaunty. When I encountered this issue, I canceled my install and came back here for input. I have been using Ubuntu for a while now, but still need my hand held for most things as it has usually run "out of the box" for me on this laptop. Formatting is especially daunting for me as it is imperative that Vista remain untouched and accessible after I do this fresh install.

OK sda1 is a toshiba system partition, I would leave that alone. You can install 9.10 two ways, both inside the extended partition. First you can install 9.10 over the 9.04. Or you can keep 9.04 by booting from the Ubuntu Live Cd or gparted Live CD and choosing resize for sda5 to create space for 9.10. Then create a partition(s) for 9.10 from that free space (/ and /home), you only need one swap partition so the one you have is good to go.

First I would back up my home directory. Then using this guide both before the install of 9.10 and after it you can easily have all your installed software that is in the repositories installed for you:

To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```


This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```


It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository. I did this with Jaunty and a lot of packages I installed manually on Hardy were available in the Jaunty repos. So I didn't search for many applications after the fresh install. Did it for karmic 9.10 too!

recap:
1. backup home and any other files you can't lose
2. use guide above to create list of installed packages
3. set up your partitions using gparted from Live CD or gparted live CD
4. install 9.10 using "manual" option at install window
5. restore backup of /home 
6. use instructions from above to install the list of saved packages from Jaunty.

5 & 6 above will keep all your program settings the way they were in jaunty since /home contains most of the config files for software.

---

### Post by GrantBarry on 2009-11-03
The reason why the partition does not get mounted is because the partition ID is 27 (which is a hidden NTFS ID).

"Toshiba System Volume" is probably a factory partition (used to install and run diagnostics) or it could be to help restore your Vista system.

It's probably best to leave the partition config.

If you feel like living on the edge, you can change the partition ID/Type from 27 to 7 and the partition should show up under Windows and Linux. You do **NOT** need to format the partition, simply change the type using FDISK under Ubuntu or DISKPART (As Administrator) under Windows.

---

### Post by space-litter on 2009-11-06
Thank you everyone; I am now on 64-bit and running well! I still have a few issues but they are for another thread. I did end up leaving both NTFS partitions just to be safe. How do I mark a thread solved?

---

### Post by arubislander on 2009-11-10
> **space-litter said:**
> How do I mark a thread solved?

Under Thread Tools there should be an entry allowing you to do so.

---

