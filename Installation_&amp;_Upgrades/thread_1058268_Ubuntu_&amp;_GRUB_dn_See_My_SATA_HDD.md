---
title: "Ubuntu &amp; GRUB d/n See My SATA HDD"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by AC-BC on 2009-02-02
Hi All,

I recently installed Ubuntu 8.10-64 on my box.  It was supposed to be a duel boot with XP.

But upon installation, neither Ubuntu nor GRUB made ANY reference to my primary SATA HDD -- upon which is already installed, and working perfectly, Windows XP.

I have (the pertinent stuff):
* DFI LANParty DK-X48 mobo
* Intel Q9300 -- Core 2 Quad CPU
* 4 G, DDR-2/64 RAM
* 1 WD 300GB, SATA HDD on Ch.1/Master -- w/ Windows XP installed
* 1 WD 300GB, PATA HDD on Ch.4/Master -- Part 1 (Pri): Data; 2 (Log): Ubuntu; 3 (Log): Swap
* 1 WD 40GB, PATA HDD on Ch.4/Slave -- Data (Parts: 1 Pri, 2 Log)
* 1 Samsung, SATA DVD-R/W

Ubuntu sees the SATA DVD without any problem.  Why don't Ubuntu and GRUB see my primary HDD?

As a result of this, Ubuntu installed GRUB to the 40G drive, where it saw the remnants of an old and disfunctional XP installation.  But when I set that drive to boot first, GRUB dies in the first stage -- won't load either XP or Ubuntu.

I reinstalled GRUB to the 300G PATA drive, and can now boot to Ubuntu.  However, since it still does not see my primary drive (SATA Ch.1), I have to go into BIOS and switch drive boot order each time I want to switch from Ubuntu to XP or visa-versa -- a royal pain in the bytes.

(There are some other, unrelated problems with the Ubuntu install, that I'll post under a different thread.)

Does anyone have a solution for this problem?

Thanks,
AC-BC

---

### Post by caljohnsmith on 2009-02-02
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to booting Windows from Grub might be.

---

### Post by AC-BC on 2009-02-02
There's no such file(s).

```
~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: ~/Desktop/boot_info_script*.sh: No such file or directory
```

---

### Post by caljohnsmith on 2009-02-02
You have to first download the "boot_info_script024.sh" to your desktop before you can run that command. Please see the link in my previous post.

---

### Post by AC-BC on 2009-02-02
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3972cd75

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    63,569,204    63,569,142   7 HPFS/NTFS
/dev/sda2          63,569,205    78,156,224    14,587,020   f W95 Ext d (LBA)
/dev/sda5          63,569,268    65,625,524     2,056,257   b W95 FAT32
/dev/sda6          65,625,588    78,156,224    12,530,637  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1575649f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   409,609,304   409,609,242  83 Linux
/dev/sdb2         409,609,305   625,137,344   215,528,040   f W95 Ext d (LBA)
/dev/sdb5         409,609,368   620,928,314   211,318,947  83 Linux
/dev/sdb6         620,928,378   625,137,344     4,208,967  82 Linux swap / Solaris


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="127222D2F6D48589" TYPE="ntfs" 
/dev/sda5: UUID="8C99-FEA2" TYPE="vfat" 
/dev/sda6: SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="d08b9074-81ed-42bb-a8df-4d69c483d104" TYPE="ext3" 
/dev/sdb6: UUID="cf23261e-a9df-4785-9304-9def53cad66c" TYPE="swap" 
/dev/sdc1: UUID="2EF8-3725" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/bob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bob)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=bob)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptOut

=========================== sdb5/boot/grub/menu.lst: ===========================

splashimage (hd1,4)/boot/grub/splashimages/97137-Sexy.xpm.gz
default 2
timeout 10

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
# kopt=root=UUID=d08b9074-81ed-42bb-a8df-4d69c483d104 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d08b9074-81ed-42bb-a8df-4d69c483d104

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

title Ubuntu 8.10, kernel 2.6.27-9-generic
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=d08b9074-81ed-42bb-a8df-4d69c483d104 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=d08b9074-81ed-42bb-a8df-4d69c483d104 ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=d08b9074-81ed-42bb-a8df-4d69c483d104 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=d08b9074-81ed-42bb-a8df-4d69c483d104 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Ubuntu Linux Command Line ( No GUI )
root (hd1,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=d08b9074-81ed-42bb-a8df-4d69c483d104 init=/bin/bash

title Other operating systems:
root

title Microsoft Windows XP Home Edition
root (hd0,0)
chainloader +1
savedefault
makeactive


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=d08b9074-81ed-42bb-a8df-4d69c483d104 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=cf23261e-a9df-4785-9304-9def53cad66c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 262.5GB: boot/grub/menu.lst
 262.4GB: boot/grub/stage2
 262.4GB: boot/initrd.img-2.6.27-7-generic
 262.4GB: boot/initrd.img-2.6.27-9-generic
 262.5GB: boot/vmlinuz-2.6.27-7-generic
 262.5GB: boot/vmlinuz-2.6.27-9-generic
 262.4GB: initrd.img
 262.4GB: initrd.img.old
 262.5GB: vmlinuz
 262.5GB: vmlinuz.old

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200

Unknown BootLoader  on sdb1

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

 sdd .
 sde .
 sdf .
 sdg .

```

---

### Post by caljohnsmith on 2009-02-02
I don't understand, because you said in your first post that you installed Grub to the 300 GB Ubuntu drive, yet according to the script your Ubuntu drive does not have Grub in the MBR; your 40 GB Windows drive still has Grub in the MBR. From the script output, I can see you ran the script while you were in your sdb5 Ubuntu install. So have you tried the Windows entry in your Grub menu on startup? If so, what happens?

---

### Post by AC-BC on 2009-02-02
Yes, I've tried the windows entry.  It freezes up.  Which is not a surprise, because that is old and no longer valid -- it was from an entirely different system.

My problem is not what GRUB ***shows***!  It's what it ***doesn't show***.  My current Windows XP is on another drive entirely (a SATA, that the BIOS lists as Channel 1).  There are 3 HDD in the system.  Only 2 are showing up in any GRUB or Ubuntu analysis (the PATA drives, which BIOS shows as Channel 4).  And yet, the Windows system on that drive boots just fine (but I have to juggle the BIOS every time I want to use it, or switch back).

Sorry, I may have made a mistake on where GRUB was loaded.  I don't remember clearly what I did.

AC-BC

---

### Post by caljohnsmith on 2009-02-02
You're definitely right then, Ubuntu does not see your Windows SATA drive. How about going into your BIOS, and can you change the Windows SATA drive to use "AHCI"? If you can do that, boot back into Ubuntu, and please post:
```
sudo fdisk -lu
```

---

### Post by AC-BC on 2009-02-02
Yes, it has the "AHCI" option.  What will this do to the data that is already on the drive?  (I haven't booted to XP after selecting that option).


```
 sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3972cd75

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    63569204    31784571    7  HPFS/NTFS
/dev/sda2        63569205    78156224     7293510    f  W95 Ext'd (LBA)
/dev/sda5        63569268    65625524     1028128+   b  W95 FAT32
/dev/sda6        65625588    78156224     6265318+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1575649f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   409609304   204804621   83  Linux
/dev/sdb2       409609305   625137344   107764020    f  W95 Ext'd (LBA)
/dev/sdb5       409609368   620928314   105659473+  83  Linux
/dev/sdb6       620928378   625137344     2104483+  82  Linux swap / Solaris

Disk /dev/sdc: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              44    15679439     7839698    b  W95 FAT32

```

---

### Post by caljohnsmith on 2009-02-02
So even with AHCI enabled Ubuntu was not able to see your Windows SATA drive it looks like. How about going into your BIOS, and please let me know all the settings you have available for that SATA drive; look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. We can work from there.

---

### Post by AC-BC on 2009-02-03
All I could find is:
   Under SATA Mode: IDE, RAID, AHCI
   If IDE is chosen, then "Onboard JMB36X Controller" becomes available for for (En/Dis)able.
I left it set at AHCI.
There is an auto-detect for the PATA drives.
And "ACPI Suspend Type" is set to "S3(STR)", the other possible setting is "S1(POS)".

However, in browsing my BIOS, I found that the drive designation has changed:
Ch.1 M is now SCSI-0 (Where WinXP is installed)
Ch.4 M is now Ch.0 M
Ch.4 S is now Ch.0 S (Where Ubuntu 8.10 is installed)

Setting the boot order to: Ch.0-M, Ch.0-S, SCSI-0, allows me to boot to GRUB/Ubuntu.

---

### Post by caljohnsmith on 2009-02-03
I would try setting the Windows SATA drive to use the "IDE" mode. Then again boot into Ubuntu, run fdisk, and see if fdisk shows the Windows drive yet. If not, I would also try the "RAID" mode for the Windows SATA drive, because I've heard some people getting SATA drives to work that way. Let me know how that goes.

---

### Post by AC-BC on 2009-02-03
Setting it to IDE was how it has been set, originally.  When I set it to RAID, that drive disappeared from the list entirely (and still doesn't show in the fdisk listing).

---

### Post by caljohnsmith on 2009-02-03
I don't know then what you can do to get Ubuntu to recognize the Windows SATA drive. As long as you know your original BIOS settings, you could try changing the setting for "Onboard JMB36X Controller" while using IDE mode, and/or try chaning the "ACPI suspend type". Good luck and sorry I can't be of much more help.

---

### Post by AC-BC on 2009-02-03
Thank you for all your help.  After trying those settings, I guess i'll have to try contacting DFI.  Maybe a BIOS upgrade is necessary.

Thanks again,
AC-BC

BTW, I have some other Ubuntu problems you may be able to sink your teeth into.   ;-)

I'll post them to a new thread.

---

