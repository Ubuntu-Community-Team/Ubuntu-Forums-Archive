---
title: "Question about Grub and triple booting Vista, Seven, and Ubuntu."
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by nicholaswj on 2009-09-13
I recently installed Ubuntu, Vista, and 7 (Seven) and everything is working great.

My question is, once I boot into Grub, I have the options of Ubuntu or Windows Loader. Once I choose Windows Loader, I then can choose Vista or 7. How/Can I have all three options be listed on grub instead of two boot loaders?

Thanks!

(I did search, and couldn't find anything relating to this... if there is something, maybe I'm using the wrong terms as I don't know them :confused:)

---

### Post by presence1960 on 2009-09-13
> **nicholaswj said:**
> I recently installed Ubuntu, Vista, and 7 (Seven) and everything is working great.

My question is, once I boot into Grub, I have the options of Ubuntu or Windows Loader. Once I choose Windows Loader, I then can choose Vista or 7. How/Can I have all three options be listed on grub instead of two boot loaders?

Thanks!

(I did search, and couldn't find anything relating to this... if there is something, maybe I'm using the wrong terms as I don't know them :confused:)
Unfortunately you probably can't. microsoft has it set up when you install 2 windows OSs that one of them boots both. You can try adding the windows entry that isn't listed in GRUB menu but it probably will not boot from it.

If you do this I can give you something to try:

Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by thegreatsnafu on 2009-09-13
Hi,


It looks like you install Vista and 7 on the same partition. If so, the longhorn loader has to handle your Windows partition. Sorry... :([FONT=Verdana][/FONT]

---

### Post by nicholaswj on 2009-09-14
All four partitions are on the same HDD but they all have separate partitions...?

[COLOR=Black]presence1960, I'll tr[/COLOR]y that next i'm in ubuntu.

---

### Post by nicholaswj on 2009-09-17
Here ya go! Help :S

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf3988e5e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14cb14cb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sdb2         204,802,048   409,602,047   204,800,000   7 HPFS/NTFS
/dev/sdb3         409,609,305   484,488,269    74,878,965  83 Linux
/dev/sdb4         484,488,270   488,392,064     3,903,795  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="B18A-98B0" TYPE="vfat" 
/dev/sdb1: UUID="D00872BC0872A160" LABEL="Windows Vista" TYPE="ntfs" 
/dev/sdb2: UUID="6EFC15E4FC15A6FD" LABEL="Windows 7" TYPE="ntfs" 
/dev/sdb3: UUID="3a74296d-9a1d-4bab-8592-575b5d61fe5a" TYPE="ext3" 
/dev/sdb4: UUID="141a2178-c439-4696-bbc7-49fbcc332b9a" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nick)


=========================== sdb3/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3a74296d-9a1d-4bab-8592-575b5d61fe5a

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        3a74296d-9a1d-4bab-8592-575b5d61fe5a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        3a74296d-9a1d-4bab-8592-575b5d61fe5a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3a74296d-9a1d-4bab-8592-575b5d61fe5a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3a74296d-9a1d-4bab-8592-575b5d61fe5a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3a74296d-9a1d-4bab-8592-575b5d61fe5a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb4 during installation
UUID=141a2178-c439-4696-bbc7-49fbcc332b9a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 222.4GB: boot/grub/menu.lst
 222.4GB: boot/grub/stage2
 222.4GB: boot/initrd.img-2.6.28-11-generic
 222.3GB: boot/initrd.img-2.6.28-15-generic
 222.3GB: boot/vmlinuz-2.6.28-11-generic
 222.3GB: boot/vmlinuz-2.6.28-15-generic
 222.3GB: initrd.img
 222.4GB: initrd.img.old
 222.3GB: vmlinuz
 222.3GB: vmlinuz.old

```

---

### Post by presence1960 on 2009-09-17
Ok, reboot your machine & go into BIOS. You want to make the disk (sdb) with Windows & ubuntu first in the hard disk boot order. Save changes to CMOS & continue booting. Boot into ubuntu and open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```
that is a lowercase L in .lst

scroll down to your windows entry and change this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```
to:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows Vista (loader)
rootnoverify    (hd0,0)
chainloader     +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title           Windows XP (loader)
rootnoverify    (hd0,1)
chainloader     +1
```

Then reboot & try both windows entries from the GRUB menu.

---

### Post by nicholaswj on 2009-09-17
All partitions/OS's are on the single HDD, which is currently first on the boot list.

I'll go ahead and try that though...

---

### Post by presence1960 on 2009-09-17
> **nicholaswj said:**
> All partitions/OS's are on the single HDD, which is currently first on the boot list.

I'll go ahead and try that though...

if you are booting the disk that has all 3 OSs on it first then you need to change your windows entries in menu.lst as I suggested. Since sdb is booting first in BIOS it is actually (hd0) not (hd1). When using (hdx,y) in GRUB x = device and y = partition. It is the actual order of hard disk boot in BIOS that determines the x designation because that is the order of the disks when you start your machine, in spite of what Ubuntu or fdisk report.

**You only need map lines in the windows entry when windows is not on the disk that boots first.** Since both windows installs are on the disk booting first in BIOS eliminate the map lines and adjust the (hdx,y) as i suggested as well as getting rid of savedefault & makeactive- they are not necessary.

---

### Post by ArthurFR on 2009-09-18
I have the same problem with Mandriva.
The mapping removal doesn't work, seven wants only a seven bootloader.

I can boot seven only when I wrote in all the dd mbr with the seven dvd (even if my boot drive is well set in the bios), so I think I'll install grub on usb key, and then Seven may "not see" the change and boot with a good signature.

I will also try to disconnect all my non-systems HD and reinstall seven bootloader, adn grub. I have seven and mandriva on my single HD laptop and grub works well.

Love Windows ](*,)

---

### Post by bumanie on 2009-09-18
I have a triple boot (vista, xp, ubuntu). What I did was install vista, then xp. Next repaired vista's bootloader with a repair disk. Then used easybcd (from [Neosmart]("http://neosmart.net/dl.php?id=1")) and added xp bootloader files to vista's. Next installed ubuntu as per a 'normal' dual boot, where grub installed to the mbr where grubs root is (hdx,x) depending on your partition numbers and setup (hd0). Hope it helps. Easybcd should be able to handle vista/win7 bootloader files without issue.

---

### Post by nicholaswj on 2009-09-18
> **presence1960 said:**
> if you are booting the disk that has all 3 OSs on it first then you need to change your windows entries in menu.lst as I suggested. Since sdb is booting first in BIOS it is actually (hd0) not (hd1). When using (hdx,y) in GRUB x = device and y = partition. It is the actual order of hard disk boot in BIOS that determines the x designation because that is the order of the disks when you start your machine, in spite of what Ubuntu or fdisk report.

**You only need map lines in the windows entry when windows is not on the disk that boots first.** Since both windows installs are on the disk booting first in BIOS eliminate the map lines and adjust the (hdx,y) as i suggested as well as getting rid of savedefault & makeactive- they are not necessary.

It didn't work.

I forget which was which (Vista Loader and XP Loader), but one would give me an error 22: no such partition, and the other just wouldn't work and would reboot.

Rememeber though, I'm not running XP, I'm running Vista and Seven.

---

### Post by nicholaswj on 2009-09-18
> **bumanie said:**
> I have a triple boot (vista, xp, ubuntu). What I did was install vista, then xp. Next repaired vista's bootloader with a repair disk. Then used easybcd (from [Neosmart]("http://neosmart.net/dl.php?id=1")) and added xp bootloader files to vista's. Next installed ubuntu as per a 'normal' dual boot, where grub installed to the mbr where grubs root is (hdx,x) depending on your partition numbers and setup (hd0). Hope it helps. Easybcd should be able to handle vista/win7 bootloader files without issue.

I'd rather not reinstall everything... I did install Vista First, then Seven, then Ubuntu.

Will it still work for me?

---

### Post by presence1960 on 2009-09-18
> **nicholaswj said:**
> It didn't work.

I forget which was which (Vista Loader and XP Loader), but one would give me an error 22: no such partition, and the other just wouldn't work and would reboot.

Rememeber though, I'm not running XP, I'm running Vista and Seven.

Are you sure the sdb disk is set to boot first in BIOS, because if it is not and sda is booting first that is the exact error you should get?

here is why I ask, see the text in red:

============================= Boot Info Summary: ==============================

 => [COLOR="Red"]Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.[/COLOR]
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.


P.S. the name in the title line has no effect on whether that entry in menu.lst will boot or not, it is only there for your reference to choose when the GRUB menu comes up. You can edit the titles to whatever you wish. So you can fix them anytime.

---

### Post by nicholaswj on 2009-09-18
I also tried changing which HDD would boot within the BIO. I first kept it the way it was and received those errors.

When I selected the other HDD, it would say no MBR.

---

### Post by presence1960 on 2009-09-18
> **nicholaswj said:**
> I also tried changing which HDD would boot within the BIO. I first kept it the way it was and received those errors.

When I selected the other HDD, it would say no MBR.

let's see what has changed since you did all this. can you post the output of another boot Info Script please so we can see exactly what has been done since the original script was run.

something is definitely wrong because GRUB was installed on the MBR of both drives.

---

### Post by nicholaswj on 2009-09-20
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf3988e5e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14cb14cb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sdb2         204,802,048   409,602,047   204,800,000   7 HPFS/NTFS
/dev/sdb3         409,609,305   484,488,269    74,878,965  83 Linux
/dev/sdb4         484,488,270   488,392,064     3,903,795  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="B18A-98B0" TYPE="vfat" 
/dev/sdb1: UUID="D00872BC0872A160" LABEL="Windows Vista" TYPE="ntfs" 
/dev/sdb2: UUID="6EFC15E4FC15A6FD" LABEL="Windows 7" TYPE="ntfs" 
/dev/sdb3: UUID="3a74296d-9a1d-4bab-8592-575b5d61fe5a" TYPE="ext3" 
/dev/sdb4: UUID="141a2178-c439-4696-bbc7-49fbcc332b9a" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nick)


=========================== sdb3/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3a74296d-9a1d-4bab-8592-575b5d61fe5a

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        3a74296d-9a1d-4bab-8592-575b5d61fe5a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        3a74296d-9a1d-4bab-8592-575b5d61fe5a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3a74296d-9a1d-4bab-8592-575b5d61fe5a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3a74296d-9a1d-4bab-8592-575b5d61fe5a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3a74296d-9a1d-4bab-8592-575b5d61fe5a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=3a74296d-9a1d-4bab-8592-575b5d61fe5a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb4 during installation
UUID=141a2178-c439-4696-bbc7-49fbcc332b9a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 222.4GB: boot/grub/menu.lst
 222.4GB: boot/grub/stage2
 222.4GB: boot/initrd.img-2.6.28-11-generic
 222.3GB: boot/initrd.img-2.6.28-15-generic
 222.3GB: boot/vmlinuz-2.6.28-11-generic
 222.3GB: boot/vmlinuz-2.6.28-15-generic
 222.3GB: initrd.img
 222.4GB: initrd.img.old
 222.3GB: vmlinuz
 222.3GB: vmlinuz.old
```

---

### Post by presence1960 on 2009-09-20
> **nicholaswj said:**
> I also tried changing which HDD would boot within the BIO. I first kept it the way it was and received those errors.

[COLOR="Red"]When I selected the other HDD, it would say no MBR[/COLOR].

I can't see how that could be happening because GRUB is installed on the MBR of both disks and both GRUBs point to the same partition. See here from your last output:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

```

So either disk booting first in BIOS should bring up GRUB. Now depending which disk boots first will alter your windows settings in menu.lst

---

### Post by RockDoctor on 2009-11-10
Ok, I think this question has been asked but not answered, so I'm going to try again. I have Vista, Fedora, Ubuntu, and Windows 7 on my desktop PC which has only a single hard drive. My primary bootloader is grub-0.97. Windows 7 was the last-installed OS. Right now, if I want to boot into Windows 7, I have to chainload the Windows bootloader on the Vista partition, and select Windows 7 from the Windows bootloader. This is not what I want. 

I want to boot into Windows 7 or Vista (and, obviously Fedora or Ubuntu) directly from grub. I duplicated the stanza to load Vista in grub.conf (aka menu.lst) and changed the partition to which it pointed so that I have two stanzas for Windows, one for Vista and one for 7. The stanza for 7 doesn't work. Something is missing in the Windows 7 partition. What is/are the missing items?

---

### Post by oldfred on 2009-11-10
You can't. Or maybe with a lot of work. Windows combines its boot so you only get one windows menu. So win7 has been combined with Vista so you can choose. In doing the combining it makes the win7 partition not separately bootable.

One work around that I saw was to turn the boot flag off on the Vista partition and then install Win7. You then cannot get to either windows from Windows but each can be booting in grub. 
Also it may be possible to do the repair of Win7 and get the boot files back into the Win7 partition. turn off the boot flag for Vista and try the repair of Win7. You will then have to reinstall grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by RockDoctor on 2009-11-10
Thanks for the reply. I may give your suggestion a try some day, but for now, I'll put up with the ugliness whenever I boot Vista or Win7.

---

