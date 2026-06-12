---
title: "Yet another Windows 7 and GRUB thread."
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Mr Connolly on 2009-11-01
Installed Windows 7, had Ubuntu only before. Restored GRUB. Can't get GRUB to recognise Windows 7 - just flickers at me then goes back to the GRUB straight away when I choose my Windows 7 option. 

Provided below are my GRUB, boot info script results and my fdisk. If anybody can help me out here you will earn my eternal love. Thanks.

First off, let me give you the helpful parts;



```

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
timeout        3

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
# kopt=root=UUID=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

//Note here is that I did originally have it above the END DEBIAN AUTOMAGIC. This comment has been added in for the code box.
title         Windows 7
root         (hd0,2)
savedefault
makeactive
chainloader+1

``````

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000235c7

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   353,590,649   353,590,587  83 Linux
/dev/sda2    *    353,590,650   476,471,834   122,881,185   7 HPFS/NTFS
/dev/sda3         476,471,835   488,392,064    11,920,230   5 Extended
/dev/sda5         476,471,898   488,392,064    11,920,167  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa35fa35

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   398,283,479   398,283,417   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e" TYPE="ext3" 
/dev/sda2: UUID="2D1B23CF66F63C21" TYPE="ntfs" 
/dev/sda5: UUID="9b1e1561-0c7f-404d-b778-2ee89fa851bf" TYPE="swap" 
/dev/sdb1: UUID="7EBC2727BC26D983" LABEL="Sam" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sam/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sam)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title         Windows 7
root         (hd0,2)
savedefault
makeactive
chainloader+1

### END DEBIAN AUTOMAGIC KERNELS LIST
title         Windows 7
root         (hd0,2)
savedefault
makeactive
chainloader+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9b1e1561-0c7f-404d-b778-2ee89fa851bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  29.7GB: boot/grub/menu.lst
  76.8GB: boot/grub/stage2
  29.7GB: boot/initrd.img-2.6.28-11-generic
  29.7GB: boot/initrd.img-2.6.28-15-generic
  29.6GB: boot/initrd.img-2.6.28-16-generic
  29.7GB: boot/vmlinuz-2.6.28-11-generic
  29.7GB: boot/vmlinuz-2.6.28-15-generic
  29.7GB: boot/vmlinuz-2.6.28-16-generic
  29.6GB: initrd.img
  29.7GB: initrd.img.old
  29.7GB: vmlinuz
  29.7GB: vmlinuz.old

``````


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000235c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       22010   176795293+  83  Linux
/dev/sda2   *       22011       29659    61440592+   7  HPFS/NTFS
/dev/sda3           29660       30401     5960115    5  Extended
/dev/sda5           29660       30401     5960083+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa35fa35

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24792   199141708+   7  HPFS/NTFS

```

---

### Post by raymondh on 2009-11-01
[B]
Am assuming your win 7 is on 1st HD, second partition.[/B]

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

**You have this set-up:**

### END DEBIAN AUTOMAGIC KERNELS LIST
title         Windows 7
root         (hd0,[COLOR="Red"]2[/COLOR])
savedefault
makeactive
chainloader+1 


**Grub starts counting from zero.  Try editing the above line to reflect:**

(hd0,1)

To edit the menu.lst, open terminal and type

```
gksudo gedit /boot/grub/menu.lst
```

Regards,

---

### Post by Mr Connolly on 2009-11-01
Tried that, it just flickers. hd(0,2) returns error no' 12 can't remember the full message.

---

### Post by Mr Connolly on 2009-11-02
I'm sorry to do this but bump, still no solution found. Tried above. No other suggestions from anyone? Also, just upgraded to GRUB2 so here's my rectified menu.lst;

```


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
timeout        3

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
# kopt=root=UUID=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e

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
##      altoptions=(single-user) single
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

title        Chainload into GRUB 2
root        dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Debian GNU/Linux, kernel 2.6.28-16-generic
uuid        dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e ro quiet splash
initrd        /boot/initrd.img-2.6.28-16-generic

title        Debian GNU/Linux, kernel 2.6.28-16-generic (recovery mode)
uuid        dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e ro single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Debian GNU/Linux, kernel memtest86+
root        dd34b6a0-907c-4c9a-a1fa-53be6e77bb2e
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
title         Windows 7
root         (hd0,1)
savedefault
makeactive
chainloader+1


```

---

### Post by oldfred on 2009-11-02
For old grub with menu.lst the entry is rootnoverify for Vista or Win7. Root worked for XP. Also since you have the boot flag on (*) in fdisk listing you do not need the makeactive line.

If you have changed to grub2 there is no menu.lst. A file grub.cfg is built like the automagic area in old grub.

Grub2 info by ranch hand and many links to other grub2 info sites
[http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211)

reinstall grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

