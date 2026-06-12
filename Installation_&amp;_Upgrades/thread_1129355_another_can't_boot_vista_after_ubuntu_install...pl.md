---
title: "another can't boot vista after ubuntu install...please help"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by jigyb007 on 2009-04-18
I know this problem has been has been posted over and over, but I still having difficulty booting into my Vista. I have two hard drives, one with vista and one with ubuntu. I installed ubuntu after intalling vista on the second harddrive. I went through the default setup not choosing any special customized boot options. So I am sure that grub is installed to the MBR of disk1. 

I see windows vista in the grub boot menu and after I select it, it goes through the loading screen with the "Windows Vista" logo with the green loading bar and it just flash the blue screen of death and the computer restarts. 

I tried using the windows vista dvd and selecting the repair option to fix the startup problem, but it still does the same thing. When I select vista it gives me a menu saying "A recent hardware or software change has caused a startup problem..and gives me the option to go into safemode, load last know good configuration, or start normally and none of them work. They all end up doing the same thing ending with a flash of the blue screen and a restart. 

Here is my boot/partion info

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ecab17e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   312,496,127   312,494,080   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb5d91e77

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   299,724,704   299,724,642  83 Linux
/dev/sdb2         299,724,705   312,496,379    12,771,675   5 Extended
/dev/sdb5         299,724,768   312,496,379    12,771,612  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0650B78E50B7834B" TYPE="ntfs" 
/dev/sdb1: UUID="01e651e0-0f18-4c60-a857-418fe91ef7d1" TYPE="ext3" 
/dev/sdb5: UUID="2497fd79-e62c-495d-89b9-e6cd4d7fdd5f" TYPE="swap" 

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
gvfs-fuse-daemon on /home/jigesh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jigesh)


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
# kopt=root=UUID=01e651e0-0f18-4c60-a857-418fe91ef7d1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=01e651e0-0f18-4c60-a857-418fe91ef7d1

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
uuid		01e651e0-0f18-4c60-a857-418fe91ef7d1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=01e651e0-0f18-4c60-a857-418fe91ef7d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		01e651e0-0f18-4c60-a857-418fe91ef7d1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=01e651e0-0f18-4c60-a857-418fe91ef7d1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		01e651e0-0f18-4c60-a857-418fe91ef7d1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=01e651e0-0f18-4c60-a857-418fe91ef7d1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=2497fd79-e62c-495d-89b9-e6cd4d7fdd5f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  77.4GB: boot/grub/menu.lst
  77.5GB: boot/grub/stage2
  77.4GB: boot/initrd.img-2.6.27-7-generic
  77.5GB: boot/vmlinuz-2.6.27-7-generic
  77.4GB: initrd.img
  77.5GB: vmlinuz


Please help...:confused:

---

### Post by ajgreeny on 2009-04-18
I have a suspicion that your problems come from having windows on the second disk though your fdisk output, mount information and grub show it to be on the first disk, and I wonder exactly what you meant by that.  What does the bios show as your first disk and what the second?  Also are we dealing with IDE or sata disks in the machine, as this could make a difference, I think.

Beyond those comments, I'm afraid I'm a bit lost, but I imagine others will have more detailed advice to give you.

---

### Post by jigyb007 on 2009-04-18
There both two 160 GB SATA disks. I have windows vista installed on the first one, which bios so as SATA-0. I have ubuntu on the second which shows as SATA-1.

I messed around with some bios settings, if I disable the second HDD the computer starts to boot, but comes up with an error that says grub failed to load. 

If I disable the first disk the computer does not boot at all. So I guess my computer is setup to boot off the first hard-drive but the MBR points it to second drive to load GRUB ? I am not sure if this is what the normal setup should be. Ubuntu boots completely fine when I select from the GRUB menu. Windows Vista is the one with the problems.

---

### Post by ronparent on 2009-04-18
What was the 2nd drive being used for prior to the Ubuntu install? Do you remember what showed in the partition manager prior to making room for the Ubuntu install. Are you offered opportunity for entry to a second bios on boot?

I am suspicious of a second drive identical to the first not being partitioned and in use by windows.

---

### Post by jigyb007 on 2009-04-18
It was being used by windows as a secondary drive storage some misc files. I use to just have it for music,movies,videos...pretty much just a bunch of multimedia files. I moved them over to an external HDD i just bought and booted up with the Linux Live CD. 

The installation detected the two HDD as sda and sdb. I selected to install to sdb using the "use entire disk" option. The ubuntu install formatted the second drive for me and automatically and partitioned the swap and ext3 areas on the second hardrive. 

I pretty much used mostly default options and just clicked next a bunch. I didn't really spend time configuring grub manually or partitioning drives manually.

---

### Post by ronparent on 2009-04-18
At this point the only way to tell what you had is if you can verify their setup in bios. If the bios raid or raid0 option is selected for SATA 1 and SATA 2, then, you in all likelyhood had windows installed on a raid0 arry. That is also known as a stripped array. By its nature is is used like a single drive with alternate sectors written to each of the component disks. If that is the case then your windows vista install was destroyed by separately partitioning the second drive. Also the windows Vista would have to be reinstalled. Dig around and let me know what you find. 

You wouldn't be the only one to have done this. Most of the time I get angry responses insisting they have only one drive!

---

### Post by jigyb007 on 2009-04-18
Hey thanks for your input. Although I know for fact I did not have a raid0 or raid1 setup. I ordered the computer with two same size drives on purpose and I disabled the raid option in bios. They were configured as two distinct SATA drives. Windows also detected them as two drives and not as a single big drive as it would be in a raid setup. 


I setup a lot of computers before so I know about stuff like that, and pretty familiar with computer hardware and software. Unfortunately my linux skills aren't that great. I can't find a solution to this problem, I've spent almost all day today trying to fix it and spent so many hours last night and this morning reading forums and trying all different solutions. But still nothing...

I really think it has something to do with my boot config, I am pretty sure I messed up my MBR but I don't really know how to fix it. I tried with the windows vista CD but that did not help.

---

### Post by ronparent on 2009-04-18
Whew. That is good news - no raid. Studying your initial post:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:  

It appears that something happened that windows doesn't like. It most likely doesn't have much to do with the Ubuntu install??!! You might try a file system check. Probably best with a windows startup disk. But one of the Ubuntu utilities might also do. I regret I can't help with systax.

---

### Post by jigyb007 on 2009-04-18
What if I go back and do a "fixmbr" from the windows vista disk and bump into recovery mode. I am scared to try this because if this doesn't work I won't be able to get into Windows or Ubuntu, but if you (or someone else) knows if this would work in getting back into vista it be great. Than I can reinstall grub ? Is this a good idea ?

---

### Post by ronparent on 2009-04-18
Doing 'fixmbr' will only rewrite the mbr. I doubt that will address your problem which is with the current state of Vista. No harm done if you do because the find > root > setup sequence in grub from a live cd terminal will easily restore your current mbr. I still think you need a file system check of the Vista partition.

---

### Post by jigyb007 on 2009-04-18
Hmm...I ran chkdsk in the recovery command prompt off the vista CD. It found some "errors" with the MFT (not really sure what that is) so I ran chkdsk c: /F to fix all errors. From the chkdsk results seem like everything is fixed and the filesystem on the harddrive is good and error free. I am still getting the same problem however. 

I am a little hesitant to do a fixmbr because it will make my linux harddrive unusable and I have to install everything again.

---

### Post by ronparent on 2009-04-18
Why don't you run the 'Boot Info Summary:' again to see if there has been a change in status?

If you want to do a fixmbr, don't worry about it: the restoration of grub is relatively trivial with a live cd. The issue however is probably with Vista independent of the linux installation. I admit that I haven't yet broken a Vista install (I guess that I'm not trying hard enough) so I am out of ideas on that count.

---

### Post by jigyb007 on 2009-04-19
there seems to have been one change. There is no problem mounting the ntfs driver anymore. I'll most the results again. 

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ecab17e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   312,496,127   312,494,080   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb5d91e77

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   299,724,704   299,724,642  83 Linux
/dev/sdb2         299,724,705   312,496,379    12,771,675   5 Extended
/dev/sdb5         299,724,768   312,496,379    12,771,612  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0650B78E50B7834B" TYPE="ntfs" 
/dev/sdb1: UUID="01e651e0-0f18-4c60-a857-418fe91ef7d1" TYPE="ext3" 
/dev/sdb5: UUID="2497fd79-e62c-495d-89b9-e6cd4d7fdd5f" TYPE="swap" 

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
gvfs-fuse-daemon on /home/jigesh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jigesh)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jigesh)


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
# kopt=root=UUID=01e651e0-0f18-4c60-a857-418fe91ef7d1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=01e651e0-0f18-4c60-a857-418fe91ef7d1

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
uuid		01e651e0-0f18-4c60-a857-418fe91ef7d1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=01e651e0-0f18-4c60-a857-418fe91ef7d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		01e651e0-0f18-4c60-a857-418fe91ef7d1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=01e651e0-0f18-4c60-a857-418fe91ef7d1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		01e651e0-0f18-4c60-a857-418fe91ef7d1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=01e651e0-0f18-4c60-a857-418fe91ef7d1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=2497fd79-e62c-495d-89b9-e6cd4d7fdd5f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  77.4GB: boot/grub/menu.lst
  77.5GB: boot/grub/stage2
  77.4GB: boot/initrd.img-2.6.27-7-generic
  77.5GB: boot/vmlinuz-2.6.27-7-generic
  77.4GB: initrd.img
  77.5GB: vmlinuz

I tried running a fixmbr off the vista recovery command line and it didn't work. Maybe they took fixmbr out of the vista cd ? Does anyone know ?

---

### Post by ajgreeny on 2009-04-19
```
=> Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

```I'm not familiar with this output from the utility you used, but note that grub is on sda and windows is installed in the MBR of sdb.  Is this normal or could you simply boot into windows by choosing the other hard disk as first boot device in BIOS.  I did notice this before my first post, but didn't say anything then as I didn't know about the utility used.  However, as nothing seems to be getting you very far, it seems worth mentioning now.

---

### Post by jigyb007 on 2009-04-19
Alright I was finally able to boot into vista. I changed my bios settings to use ATA instead of AHCI mode in BIOS. Seems to resolved my problem. My question now is....why has this problem happened all the sudden ? I never messed with the AHCI or ATA drivers in Vista or did I ever change the settings in the BIOS until now..so I am not sure why this problem popped out of nowhere right after the linux install. 

Anyway now that it is resolved should I try to get Vista to use AHCI mode ? Is that much better to use than ATA ? Thanks for all the input and help.

---

