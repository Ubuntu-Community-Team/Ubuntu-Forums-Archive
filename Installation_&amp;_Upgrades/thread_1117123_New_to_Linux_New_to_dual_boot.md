---
title: "New to Linux New to dual boot"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by Serious4Play on 2009-04-05
First off let me say I am pretty much a total newbie to Linux. I have an older system that I have wiped clean due to various XP issues. The system has 3 HDD's in it. I have reformatted the HDD that had the OS installed and reinstalled XP first (successfully) then I installed Intrepid (successfully). After the Intrepid install there was no grub menu and the pc would boot straight to XP. So I did a bit of reading and used ```
sudo grub
grub> root (hd2,1)
setup (hd2)
```

This added Ubuntu to a grub menu and I was then able to select it and boot into Ubuntu. Now when I select XP the system won't boot saying there is an issue with NTLDR. Did a bit more reading and I'm still lost so I am attaching my boot info summary and hopefully someone can help.

Thanks,
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x207a2460

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d115b39

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9f519f51

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   112,647,779   112,647,717   7 HPFS/NTFS
/dev/sdc2         112,647,780   143,364,059    30,716,280  83 Linux
/dev/sdc3         143,364,060   238,725,899    95,361,840  83 Linux
/dev/sdc4         238,725,900   240,107,489     1,381,590  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8A2C1F9E2C1F847B" LABEL="Vol 2" TYPE="ntfs" 
/dev/sdb1: UUID="58B0300CB02FEF66" LABEL="Vol 1" TYPE="ntfs" 
/dev/sdc1: UUID="80BC92ACBC929BEA" TYPE="ntfs" 
/dev/sdc2: UUID="d10cd70c-00b5-4daa-80ce-eab449869c1b" TYPE="ext2" 
/dev/sdc3: UUID="dbc1bb6b-7b31-474a-870b-b49a12fdab82" TYPE="ext3" 
/dev/sdc4: UUID="429370af-2d16-4570-a5c7-f8df8d2209f2" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc2 on / type ext2 (rw,relatime,errors=remount-ro)
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
/dev/sdc3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kag/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kag)
/dev/scd1 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=kag)
/dev/sdc1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdc2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d10cd70c-00b5-4daa-80ce-eab449869c1b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d10cd70c-00b5-4daa-80ce-eab449869c1b

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
uuid		d10cd70c-00b5-4daa-80ce-eab449869c1b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d10cd70c-00b5-4daa-80ce-eab449869c1b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		d10cd70c-00b5-4daa-80ce-eab449869c1b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d10cd70c-00b5-4daa-80ce-eab449869c1b ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d10cd70c-00b5-4daa-80ce-eab449869c1b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d10cd70c-00b5-4daa-80ce-eab449869c1b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d10cd70c-00b5-4daa-80ce-eab449869c1b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d10cd70c-00b5-4daa-80ce-eab449869c1b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d10cd70c-00b5-4daa-80ce-eab449869c1b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=d10cd70c-00b5-4daa-80ce-eab449869c1b /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdc3
UUID=dbc1bb6b-7b31-474a-870b-b49a12fdab82 /home           ext3    relatime        0       2
# /dev/sdc4
UUID=429370af-2d16-4570-a5c7-f8df8d2209f2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc2: Location of files loaded by Grub: ===================


  69.2GB: boot/grub/menu.lst
  69.2GB: boot/grub/stage2
  69.2GB: boot/initrd.img-2.6.27-11-generic
  69.2GB: boot/initrd.img-2.6.27-7-generic
  69.2GB: boot/vmlinuz-2.6.27-11-generic
  69.3GB: boot/vmlinuz-2.6.27-7-generic
  69.2GB: initrd.img
  69.2GB: initrd.img.old
  69.2GB: vmlinuz
  69.3GB: vmlinuz.old 
```

---

### Post by 73ckn797 on 2009-04-05
One simple way to fix grub and windows dual boot is to download and burn a CD of "Super Grub Disk" from [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) .

---

### Post by CyberMando on 2009-04-05
It looks like things are in very good shape except the Ntloader. It appears that XP is installed on sdb1, not sda1. When you installed XP had you set the BIOS to boot from that disk? XP usess a file, boot.ini, to boot that refers to hard diskc somewhat like grub does. I suspect that file points to sda1 rather than sdb1. IIRC that file is in sdb1 and can be edited.

---

### Post by ronparent on 2009-04-05
I see no obvious problems with your menu.lst. Your windows install is where the root designates it. Also the ntldr seems to be in order. You might want to edit menu.lst (sudo gedit menu.lst) to the form as follows: 

title       Windows XP (hd2)  ##your own title need not be changed
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1 

If that doesn't work, we can try something else?

---

### Post by Serious4Play on 2009-04-05
> **ronparent said:**
> I see no obvious problems with your menu.lst. Your windows install is where the root designates it. Also the ntldr seems to be in order. You might want to edit menu.lst (sudo gedit menu.lst) to the form as follows: 

title       Windows XP (hd2)  ##your own title need not be changed
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1 

If that doesn't work, we can try something else?

Just so I'm clear...when I type ```
sudo gedit menu.lst
``` into terminal a blank text window opens up. Now I can simply copy and paste these lines
```
Windows XP (hd2)  ##your own title need not be changed
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
``` save and reboot? Sorry for my ignorance but I really am new to all this...haven't worked in command lines since the days of apple IIe ;)

---

### Post by 73ckn797 on 2009-04-05
The command to open menu.lst is:

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by CyberMando on 2009-04-05
I see now that you had posted the boot.ini and it is looking for dis0, partition one when XP is actually on disk1, partition1.

---

### Post by ronparent on 2009-04-05
I'm reading his posting differently. I see winXP with ntldr, etc. on sdc1 -ie (hd2,0).

---

### Post by Serious4Play on 2009-04-05
I tried changing the menu.lst as suggested and rebooted. Still no change. I still receive the missing NTLDR press to reboot message.

---

### Post by CyberMando on 2009-04-05
You are right. XP is on sdc1. Does grub have a message about ntloader, or would that message be from XP? It looks to me like grub is handing off to ntloader but ntloader is not finding anything to boot on sda1, which is where boot.ini is telling it to look.

---

### Post by Serious4Play on 2009-04-05
The message NTLDR is missing press CTRL + ALT + DEL, is what I get after choosing XP from the grub menu. Prior to using the ```
find /boot/grub/stage1
root(hd2,1)
setup (hd2)
``` The PC would boot directly to XP and no grub menu would come up at all.

---

### Post by CyberMando on 2009-04-05
It has been years since I messed with boot.ini but I think if you change the rdisk entry to 2 (as below) it will find NTLDR.

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdc2/boot/grub/menu.lst: ===========================

---

### Post by Serious4Play on 2009-04-05
Not sure if it's the correct method but I opened the boot.ini in a text editor and changed the 0 to a 2 restarted and still no luck. I really appreciate all the help so far. I have to head out to work now so no time to try anything else tonight.

Thanks again...I'll check back later.

---

### Post by meierfra. on 2009-04-05
> the PC would boot directly to XP and no grub menu would come up at all.

This means that you are booting from /dev/sdc, the hard drive containing XP and Ubuntu. Grub, during boot up, always sees the boot drive as (hd0).  So  the correct entry to use in menu.lst is

title Windows XP 
rootnoverify (hd0,0)
chainloader +1


You also need to reverse the changes in boot.ini (so change the 2 back to 0).

---

### Post by ronparent on 2009-04-05
The situation you describe in posting 11 would occure if the bios on your computer directed loading from the mbr of sda - loading windows. Since you installed the grub mbr to sdc the grub bootloader would not be found unless you shuffled the boot order in bios! What happens, if without making further change, you reconfigure grub with setup (hd0). To recap:


Code:

find /boot/grub/stage1
root(hd2,1)
setup (hd0)

---

### Post by CyberMando on 2009-04-05
Could a newbie really get into this situation? Where did he get this info?
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

That is in the first part of his post and seems to indicate that grub is on sda and sdc, and that Windows is on the MBR of sdb. Looking at the other info he has provided the piece I quoted above seems to be accurate. Did he type that in or is there a program to extract that info?

---

### Post by ronparent on 2009-04-05
I defer to meierfra who seems to have the best handle on this right now.

---

### Post by CyberMando on 2009-04-05
Interesting puzzle and advertising meierfra.:)
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by meierfra. on 2009-04-05
> Where did he get this info?
From the [boot info script]("https://sourceforge.net/projects/bootinfoscript")  (Seems you already figured this out while I was typing this :). )

> Could a newbie really get into this situation? 
Yes.  The Ubuntu installer has no knowledge of the actually order of the hard drives in the bios and by default installs grub to the MBR of  /dev/sda.   
But the OP's bios are set to boot from /dev/sdc1. So originally the Computer ignored grub and booted into Windows. The OP then used "root (hd2,1), setup (hd2)" to install grub to the MBR of /dev/sdc.  This brought up the Grub menu, but the windows item on menu.lst still assume that the boot drive is /dev/sda. So to be able to boot into XP, the Windows item needs to be edited.


> => Windows is installed in the MBR of /dev/sdb

This only says that the boot code in the MBR of /dev/sdb  is the code Windows uses to boot a hard drive. It does not say the Windows OS is installed on /dev/sdb


> sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM


This says that the Windos XP is installed on /dev/sdc1 and also that all the necessary boot files for XP can be found on /dev/sdc1.

---

### Post by Serious4Play on 2009-04-06
Got it!!! I restored the boot.ini and replaced ```
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

with ```
title Windows XP
rootnoverify (hd0,0)
chainloader +1

``` in the menu.lst as directed by meierfra and just like that...

Thank you meierfra and everyone else who helped.

---

### Post by meierfra. on 2009-04-06
> Got it!!! 
Great. Have fun with XP and Ubuntu

---

### Post by Serious4Play on 2009-04-06
Thanks, hope to have fun with Ubuntu...only reason XP is still installed is for those programs that there is just no alternative...

---

