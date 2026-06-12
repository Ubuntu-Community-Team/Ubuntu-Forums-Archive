---
title: "cant find vista recovery image"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by stlsaint on 2009-08-27
so upon further looking at my menu.lst i realized that i didnt see my vista recovery image that came with my machine...granted i truly feel that i will never need it now that ubuntu is in my life but i thought that i would get a good learning experience out of this by trying to add a stanza to my menu.lst to enable me to see it in GRUB at boot if at all possible because as soon as i hit vista loader it loads xp as it should but im wondering where is my recover image. Please correct me if im wrong or missing something here!
here is my setup...1. ubuntu,2. xp(just because) 3. ubuntu christian edition. 4 somewhere is my recovery image!! here is the stanza i wanted to add...

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista (loader)
rootnoverify	(hd0,4)
savedefault
makeactive
chainloader	+1

i used hd0,4 as xp is on hd0,3 from what i gather....but below is my menu.lst. in next post

---

### Post by stlsaint on 2009-08-27
I CUT OUT ALL THE USELESS STUFF FOR THIS POST!!

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista (loader)
rootnoverify	(hd0,3)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot

---

### Post by stlsaint on 2009-08-27
anything...

---

### Post by presence1960 on 2009-08-27
Download the boot info script from my signature line to desktop. Then open a terminal and run ```
sudo bash ~/Desktop/boot_info_script*.sh
```
The script will give you all the info you need to know in a file RESULTS.txt. if you can't interpret the info paste the entire contetns of the RESULTS.txt file it creates on the desktop back here.

---

### Post by presence1960 on 2009-08-27
```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda
root (hd0,7)
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash
initrd /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda
root (hd0,7)
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single
initrd /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda
root (hd0,7)
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash
initrd /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda
root (hd0,7)
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single
initrd /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda
root (hd0,7)
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda
root (hd0,7)
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single
initrd /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda
root (hd0,7)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda
root (hd0,7)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single
initrd /boot/initrd.img-2.6.28-11-generic
savedefault
boot
```

Why don't you eliminate all the above by chainloading like this:

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title          Ubuntu 9.04
rootnoverify   (hd0,7)
chainloader    +1
```

what that will do is bring up GRUB for that distro when you choose the chainloader option. Then you won't have to edit the GRUB on MBR which comes up when you boot each time that other distro updates it's kernels. it is a lot neater & no editing the menu.lsts

P.S. just a suggestion

---

### Post by stlsaint on 2009-08-27
thanks presence..so it was where i thought it to be so now im thinking that my stanza is correct and i plan on putting it under my other stanza for xp...but just to be safe would you mind taking a look...i already made a backup of my menu lst so im not scared of losing anything but it would be great to not have to go thru the mess!! here are my results...had to edit it some...

============================= Boot Info Summary: ==============================

 Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

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
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6e236e23

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    63,472,814    63,472,752   7 HPFS/NTFS
/dev/sda3          63,472,815   373,189,949   309,717,135   5 Extended
/dev/sda5         126,945,693   128,937,689     1,991,997  82 Linux swap / Solaris
/dev/sda6         128,937,753   373,189,949   244,252,197  83 Linux
/dev/sda7          63,472,941    65,464,874     1,991,934  82 Linux swap / Solaris
/dev/sda8          65,464,938   126,945,629    61,480,692  83 Linux
/dev/sda4    *    373,189,950   390,716,864    17,526,915   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="39D981B42084ABFF" LABEL="BLACK" TYPE="ntfs" 
/dev/sda4: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="114e545a-c0ca-4479-a984-5e0741635027" TYPE="swap" 
/dev/sda6: UUID="a69a99ad-3b01-4561-9096-35d9ad710995" TYPE="ext3" 
/dev/sda7: UUID="f0370262-4094-454f-a91b-a08f0e7ea113" TYPE="swap" 
/dev/sda8: UUID="56e32a96-f663-412c-a241-eeabee7a1c54" SEC_TYPE="ext2" TYPE="ext3" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdb1: UUID="B858B2B558B271AC" LABEL="FreeAgent Drive" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/stlsaint/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stlsaint)
/dev/sr0 on /media/cdrom0 type udf (rw,nosuid,nodev,utf8,user=stlsaint)
/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda6/boot/grub/menu.lst: ===========================
 End Default Options 

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a69a99ad-3b01-4561-9096-35d9ad710995 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a69a99ad-3b01-4561-9096-35d9ad710995
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista (loader)
rootnoverify	(hd0,3)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-15-generic on /dev/sda8
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-15-generic  recovery mode  (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-14-generic on /dev/sda8
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-13-generic on /dev/sda8
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-11-generic on /dev/sda8
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=a69a99ad-3b01-4561-9096-35d9ad710995 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=114e545a-c0ca-4479-a984-5e0741635027 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=f0370262-4094-454f-a91b-a08f0e7ea113 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 103.0GB: boot/grub/menu.lst
 102.9GB: boot/grub/stage2
 103.0GB: boot/initrd.img-2.6.28-11-generic
 102.9GB: boot/initrd.img-2.6.28-13-generic
 103.0GB: boot/initrd.img-2.6.28-14-generic
 102.9GB: boot/initrd.img-2.6.28-15-generic
 102.9GB: boot/vmlinuz-2.6.28-11-generic
 102.9GB: boot/vmlinuz-2.6.28-13-generic
 103.0GB: boot/vmlinuz-2.6.28-14-generic
 102.9GB: boot/vmlinuz-2.6.28-15-generic
 102.9GB: initrd.img
 103.0GB: initrd.img.old
 102.9GB: vmlinuz
 102.9GB: vmlinuz.old

=========================== sda8/boot/grub/menu.lst: ===========================

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
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=56e32a96-f663-412c-a241-eeabee7a1c54

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		56e32a96-f663-412c-a241-eeabee7a1c54
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		56e32a96-f663-412c-a241-eeabee7a1c54
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		56e32a96-f663-412c-a241-eeabee7a1c54
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		56e32a96-f663-412c-a241-eeabee7a1c54
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		56e32a96-f663-412c-a241-eeabee7a1c54
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		56e32a96-f663-412c-a241-eeabee7a1c54
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		56e32a96-f663-412c-a241-eeabee7a1c54
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		56e32a96-f663-412c-a241-eeabee7a1c54
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56e32a96-f663-412c-a241-eeabee7a1c54 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista (loader)
rootnoverify	(hd0,3)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-14-generic on /dev/sda6
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=ef108790-716f-46d1-be93-ccd81ff0d035 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=ef108790-716f-46d1-be93-ccd81ff0d035 ro single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-13-generic on /dev/sda6
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=ef108790-716f-46d1-be93-ccd81ff0d035 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-13-generic  recovery mode  (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=ef108790-716f-46d1-be93-ccd81ff0d035 ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic on /dev/sda6
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ef108790-716f-46d1-be93-ccd81ff0d035 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ef108790-716f-46d1-be93-ccd81ff0d035 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, memtest86+ (on /dev/sda6
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=56e32a96-f663-412c-a241-eeabee7a1c54 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=114e545a-c0ca-4479-a984-5e0741635027 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=f0370262-4094-454f-a91b-a08f0e7ea113 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  40.7GB: boot/grub/menu.lst
  40.6GB: boot/grub/stage2
  40.6GB: boot/initrd.img-2.6.28-11-generic
  40.7GB: boot/initrd.img-2.6.28-13-generic
  40.7GB: boot/initrd.img-2.6.28-14-generic
  40.6GB: boot/initrd.img-2.6.28-15-generic
  40.6GB: boot/vmlinuz-2.6.28-11-generic
  40.7GB: boot/vmlinuz-2.6.28-13-generic
  40.7GB: boot/vmlinuz-2.6.28-14-generic
  40.7GB: boot/vmlinuz-2.6.28-15-generic
  40.6GB: initrd.img
  40.7GB: initrd.img.old
  40.7GB: vmlinuz
  40.7GB: vmlinuz.old

================================ sda4/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

### Post by stlsaint on 2009-08-27
would the above be correct to add?

---

### Post by presence1960 on 2009-08-27
sorry about the delay. I thought I noticed something fishy about your sda1 info from the script. I have an HP a810n that is not being used. It has a recovery partition and XP and jaunty on it. So I had to unplug my daughters rig and put the HP on there and run the script. here is what I got:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

[COLOR="Red"]sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com
[/COLOR]
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

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
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa7a57e45

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    11,454,344    11,454,282   b W95 FAT32
/dev/sda2    *     11,454,345    48,805,469    37,351,125   7 HPFS/NTFS
/dev/sda3          48,805,470    78,156,224    29,350,755   5 Extended
/dev/sda5          48,805,533    51,809,624     3,004,092  82 Linux swap / Solaris
/dev/sda6          51,809,688    78,156,224    26,346,537  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1967 MB, 1967128576 bytes
40 heads, 56 sectors/track, 1715 cylinders, total 3842048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bad43

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *              1     3,842,047     3,842,047   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="HP_RECOVERY" UUID="595B-27B6" TYPE="vfat" 
/dev/sda2: UUID="F6AC4059AC401691" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sda5: UUID="b1f5e153-5c0d-4d7c-95e1-dbbf3a185312" TYPE="swap" 
/dev/sda6: UUID="e2b19c06-661b-4e45-89f5-7c9013b25a48" TYPE="ext3" 
/dev/sdb1: SEC_TYPE="msdos" UUID="06F5-5305" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/jada/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jada)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

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
# kopt=root=UUID=e2b19c06-661b-4e45-89f5-7c9013b25a48 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e2b19c06-661b-4e45-89f5-7c9013b25a48

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		e2b19c06-661b-4e45-89f5-7c9013b25a48
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=e2b19c06-661b-4e45-89f5-7c9013b25a48 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		e2b19c06-661b-4e45-89f5-7c9013b25a48
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=e2b19c06-661b-4e45-89f5-7c9013b25a48 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		e2b19c06-661b-4e45-89f5-7c9013b25a48
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e2b19c06-661b-4e45-89f5-7c9013b25a48 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e2b19c06-661b-4e45-89f5-7c9013b25a48
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e2b19c06-661b-4e45-89f5-7c9013b25a48 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e2b19c06-661b-4e45-89f5-7c9013b25a48
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Windows Recovery
#rootnoverify	(hd0,0)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=e2b19c06-661b-4e45-89f5-7c9013b25a48 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b1f5e153-5c0d-4d7c-95e1-dbbf3a185312 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  36.4GB: boot/grub/menu.lst
  36.5GB: boot/grub/stage2
  36.5GB: boot/initrd.img-2.6.28-11-generic
  36.5GB: boot/initrd.img-2.6.28-15-generic
  36.5GB: boot/vmlinuz-2.6.28-11-generic
  36.5GB: boot/vmlinuz-2.6.28-15-generic
  36.5GB: initrd.img
  36.5GB: initrd.img.old
  36.5GB: vmlinuz
  36.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde 
```

Notice the output in red. That is my recovery partition. It has boot files. I noticed yours does not. Hopefully yours will still boot. Add the entry in menu.lst for the recovery partition just as you would for windows. See if it will boot when you select it. just make sure you don't go thru with the process-LOL. If it doesn't boot, hopefully you made a set of bootable CD/DVDs as most manufacturers give you that option. If not then boot into windows and see if that option is still available and burn them now.

P.S. My HP gave me the ability to burn a recovery Tools CD. With that CD I can partition XP and run the recovery console. useful tools in case you need to run the recovery console because you can't do it from the recovery partition or the bootable CD/DVDs because all they will do is restore the factory image to your hard disk.

---

### Post by stlsaint on 2009-08-27
i will do as you posted but the recovery is for vista and i have xp installed so i wouldnt be able to burn the cd's but i was sure to make a image of the recovery partition prior to me deleting the installed vista OS so im covered if the worse happens!thanks i will post with results!

---

### Post by presence1960 on 2009-08-27
> **stlsaint said:**
> i will do as you posted but the recovery is for vista and i have xp installed so i wouldnt be able to burn the cd's but i was sure to make a image of the recovery partition prior to me deleting the installed vista OS so im covered if the worse happens!thanks i will post with results!

Let me know what happens. Your sda1 says it is an XP partition not Vista. But as long as you made a backup of the recovery partition you can always restore it.

---

### Post by stlsaint on 2009-08-27
ok so i added the stanza as stated in my original post and i got the option for vista loader in Grub but when i selected it i get this...

Error 12: Requested invalid device
Press any key to continue...

guess it was wrong...any way on how to fix...when i press F11 at startup to start system recovery it goes straight into grub which i thought it would but just had to see...

---

### Post by presence1960 on 2009-08-27
Good thing you made that backup. I would restore that backup then try booting that partition from GRUB. I kind of figured it would not boot because sda1 has no bootfiles or directory.

---

### Post by stlsaint on 2009-08-27
thats weird tho because when i boot into the livecd partition editor still shows my recovery as hp recovery and it has some files on there and i have been very careful to never touch it so how did the boot files get moved...oh well..im at work now so i will do it when i get home and post results...thanks again!!

---

### Post by Mark Phelps on 2009-08-28
> **presence1960 said:**
> Let me know what happens. Your sda1 says it is an XP partition not Vista. But as long as you made a backup of the recovery partition you can always restore it.

While true, that partition contains the Vista boot loader files.

So, if that partition came preinstalled with Vista, then it has the correct boot loader files on it. Why the script says it is an "XP partition", I do not know.

---

