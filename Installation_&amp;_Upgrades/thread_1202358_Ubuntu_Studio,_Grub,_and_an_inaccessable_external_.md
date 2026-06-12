---
title: "Ubuntu Studio, Grub, and an inaccessable external HDD"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by aidanandrach on 2009-07-02
Hi all, hoping you can help!

Follows a fairly in-depth description, but my top priority is getting my external HDD back up running (in WinXP intitially).  But I'd love to get this whole system going if I can...

 I have Ubuntu Studio 9.04 installed on my home laptop &#8211; works really well, and I love it! I spend a lot of time on the road for work, so wanted this available on my work laptop as well... Obviously work would frown upon me dual-booting my work laptop, so I decided to install it on my external HDD and boot from there instead.


 My current situation is that I cannot boot in to Ubuntu Studio yet, and Win XP now wants to format my HDD every time I insert it...


 Did a bunch of reading before kicking this off, and all indications are that it should work well.


 Here's what I did:
1. Booted in to a live-CD of Ubuntu 8.04.
2. Used Gparted to shrink the existing NTFS partition on my external HDD from 149GB to 110GB. Had some minor issues here in that it wouldn't mount to begin with, but fixed that by going back in to WinXP and re-safely removing hardware.
3. Booted in to the Ubuntu Studio install disk (no live-CD of this is available)
4. Install went without a hitch, installing to a new ext3 partition in the empty space from 2. above.
5. Told Grub to install to (hd1,4) (which is the partition that I installed to in 4. above)
6. Tried to boot in to Ubuntu Studio &#8211; no go.
7. Re-ran install routine in recovery mode, and told Grub to this time install to (hd1,0), thinking that maybe my bios can only boot from the first partition.
 

So, here are the other facts:
a) Laptop supports USB-boot, and it is enabled (order: CD, USB, Internal HDD)
b) It seeks the USB device on boot, but reports "no boot sector found" or words to that effect.
c) At step 6. above, I could see both the NTFS and ext3 partitions in the live-CD, and all the Ubuntu Studio files, and the grub folders, were present and correct.
d) At this stage, I do not know for sure if the external HDD was funtional in Windows (but I think from memory it was)
e) After step 7. I can definitely NOT gain access to the external HDD in WinXP; it reports that the drive is not formatted and wants to format it.
 
So, lots of information! Where do I start guys?!? 

Cheers
Aidan

---

### Post by aidanandrach on 2009-07-02
Any thoughts guys?

Thanks in advance
Aidan

---

### Post by aidanandrach on 2009-07-02
So I booted back in to the liveCD.  I can see the Ext3 partition here quite happily.  'computer' does not see the NTFS one however.  Gparted recognised that the NTFS partition was there but gave me this messgae:
[IMG]http://i779.photobucket.com/albums/yy79/aidanandrach/Screenshot.png?t=1246588953[/IMG]

---

### Post by presence1960 on 2009-07-02
boot from the Live CD and download the boot Info Script32 to your desktop from here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Once on your desktop open a terminal and run this command: ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on your desktop. paste entire contents of that file back here. Once pasted here be sure to highlight all text you pasted here and click # on the toolbar to place code tags around the text (please make sure you do this so your text does not take up a whole page in your thread). This will provide all the info about your setup and boot process.

---

### Post by aidanandrach on 2009-07-02
Thanks Presence.

Here we go:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 302442831 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sdb5 and looks 
                       at sector 302295375 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652  de Dell Utility
/dev/sda2    *        176,715   156,296,384   156,119,670   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc9c7e37f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   251,128,079   251,128,017   7 HPFS/NTFS
/dev/sdb2         251,128,080   312,576,704    61,448,625   5 Extended
/dev/sdb5         251,128,143   309,958,109    58,829,967  83 Linux
/dev/sdb6         309,958,173   312,576,704     2,618,532  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0605" TYPE="vfat" 
/dev/sda2: UUID="82DC5DDADC5DC8D5" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb5: UUID="a5a0a16c-2ec5-4b44-9661-3e9e314a05ff" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="85360e4a-ed9f-4678-aaa3-5e878f0a45ff" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

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
# kopt=root=UUID=a5a0a16c-2ec5-4b44-9661-3e9e314a05ff ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a5a0a16c-2ec5-4b44-9661-3e9e314a05ff

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

title        Ubuntu 9.04, kernel 2.6.28-3-rt
uuid        a5a0a16c-2ec5-4b44-9661-3e9e314a05ff
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=a5a0a16c-2ec5-4b44-9661-3e9e314a05ff ro quiet splash 
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid        a5a0a16c-2ec5-4b44-9661-3e9e314a05ff
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=a5a0a16c-2ec5-4b44-9661-3e9e314a05ff ro  single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04, memtest86+
uuid        a5a0a16c-2ec5-4b44-9661-3e9e314a05ff
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
rootnoverify    (hd0,1)
savedefault
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=a5a0a16c-2ec5-4b44-9661-3e9e314a05ff /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=85360e4a-ed9f-4678-aaa3-5e878f0a45ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 154.7GB: boot/grub/menu.lst
 154.8GB: boot/grub/stage2
 154.7GB: boot/initrd.img-2.6.28-3-rt
 154.7GB: boot/vmlinuz-2.6.28-3-rt
 154.7GB: initrd.img
 154.7GB: vmlinuz

```

---

### Post by presence1960 on 2009-07-03
I am not versed in Ubuntu installs on a removable drive. but I can tell you this from looking at your results you posted. GRUB is installed to the boot sector of sdb1. it should be installed to the MBR of that removable disk. note the mounting failed message for sdb1 and unknown filetype. I would plug that drive in and install GRUB to the MBR by doing this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR, 
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

This will get GRUB on the MBR of your external drive where it will execute and point to your sdb5 menu.lst. After doing this go into BIOS and put removable or USB drive ahead of the HDD in disk boot order. This way when your disk is plugged in GRUB will appear, when it is unplugged your windows bootloader will take over. You may need to edit your windows entry in menu.lst to get it to boot windows from GRUB. But let's get your GRUB set first.

---

### Post by aidanandrach on 2009-07-03
Fantastic, thanks presence.  Is this also likely to correct the issue of no longer being able to see my NTFS partition in Windows?  Or is this data likely irretrievable?

Thanks, I'll give this a crack when I get home from work in a few hours...

Aida

---

### Post by aidanandrach on 2009-07-03
> **aidanandrach said:**
> Fantastic, thanks presence.  Is this also likely to correct the issue of no longer being able to see my NTFS partition in Windows?  Or is this data likely irretrievable?

Thanks, I'll give this a crack when I get home from work in a few hours...

Aida

OK, for the record, and for anyone who has this issue, I've now fixed the issue of not being able to access the NTFS partition through windows.  The boot sector for the drive was corrupt (presumable by my attempting to install Grub to it).  I tested and rebuilt this using TestDisk and the information at [http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

So, now on to trying to get it to boot from USB - will be trying presence's suggestion and will post back the results.

Cheers

---

### Post by aidanandrach on 2009-07-03
Bugger.  Thanks presence, but no go.  Grub seemed to do what was expected, and gave me the confirmation that it had been installed to the MBR.  But when I boot it my pc is still telling me that the USB drive is not bootable, and goes on to windows.

Any more thoughts?  Is it worth running that script again?

Thanks.

---

### Post by presence1960 on 2009-07-03
I would try repartitioning and reinstalling Ubuntu on the removable drive. I don't like the looks of that install at all. When you get to the Ready to install window on the installation click the advanced tab and choose to put grub on sdb. This will put it on the MBR of that disk.

P.S. I forgot to add the screenshot of the Ready to install window for your reference, so see my next post.

---

### Post by presence1960 on 2009-07-03
oops forgot to attach a screen shot of that window:

---

### Post by aidanandrach on 2009-07-03
For my own interest more than anything I reran that script to look at the differences before and after - posted below.
```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 1 on boot drive #119 for the stage2 
                       file. A stage2 file is at this location on /dev/sdb. 
                       Stage2 looks on the same partition for 
                       /boot/grub/stage2. No errors found in the Boot 
                       Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 sdb1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 sdb1 ntfs-3g force 0 0

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sdb5 and looks 
                       at sector 302295375 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652  de Dell Utility
/dev/sda2    *        176,715   156,296,384   156,119,670   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc9c7e37f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   251,128,079   251,128,017   7 HPFS/NTFS
/dev/sdb2         251,128,080   312,576,704    61,448,625   5 Extended
/dev/sdb5         251,128,143   309,958,109    58,829,967  83 Linux
/dev/sdb6         309,958,173   312,576,704     2,618,532  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0605" TYPE="vfat" 
/dev/sda2: UUID="82DC5DDADC5DC8D5" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="80C2F69090FA0800" LABEL="Aidan Schurr" TYPE="ntfs" 
/dev/sdb5: UUID="a5a0a16c-2ec5-4b44-9661-3e9e314a05ff" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="85360e4a-ed9f-4678-aaa3-5e878f0a45ff" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

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
# kopt=root=UUID=a5a0a16c-2ec5-4b44-9661-3e9e314a05ff ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a5a0a16c-2ec5-4b44-9661-3e9e314a05ff

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

title        Ubuntu 9.04, kernel 2.6.28-3-rt
uuid        a5a0a16c-2ec5-4b44-9661-3e9e314a05ff
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=a5a0a16c-2ec5-4b44-9661-3e9e314a05ff ro quiet splash 
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid        a5a0a16c-2ec5-4b44-9661-3e9e314a05ff
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=a5a0a16c-2ec5-4b44-9661-3e9e314a05ff ro  single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04, memtest86+
uuid        a5a0a16c-2ec5-4b44-9661-3e9e314a05ff
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
rootnoverify    (hd0,1)
savedefault
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=a5a0a16c-2ec5-4b44-9661-3e9e314a05ff /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=85360e4a-ed9f-4678-aaa3-5e878f0a45ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 154.7GB: boot/grub/menu.lst
 154.8GB: boot/grub/stage2
 154.7GB: boot/initrd.img-2.6.28-3-rt
 154.7GB: boot/vmlinuz-2.6.28-3-rt
 154.7GB: initrd.img
 154.7GB: vmlinuz

```If I just remove that Ext3 partition and try again, would that be enough?  Or am I likely to have to redo the NTFS one as well?  I'd like to avoid this if I can - I don't fancy shifting ~100GB of data off and back on again...

---

### Post by presence1960 on 2009-07-04
what is on sdb1? The first script it had no filesystem, now it is NTFS. I would move the files off that sdb1 and format the entire sdb drive, then set up a new partition scheme. After that i would reinstall Ubuntu making surewhen you get to the ready to install window of the installation process you click advanced and choose sdb so GRUB is installed to MBR of the sdb disk. Currently you have Windows bootloader on sdb- not what you want!

---

### Post by aidanandrach on 2009-07-04
Thanks, yes, sdb is/was a data drive, formated as ntfs.  Mainly filled with media at the moment.  When I ran the original script I was completely unable to access this in windows, as the boot sector was corrupt.  I rebuilt this with TestDisk and it's now OK, which is why it's showing up as NTFS now.

So, at this point I'm going to use Gparted to remove the Ext3 partition from the drive and restore the ntfs partition to the full 160GB again.

I'll then revisit my options for getting Ubuntu Studio up and running again - but I'm not game to go playing around with this drive too much more.  As above, shifting 100GB of data off is not my cup of tea at the moment!!  I suspect it's in a fragile state thanks to my tinkering - as you point out, it thinks there's a windows master boot record, but grub appears to also be loaded in to it...

Presence, thanks a load for all your help, input and advice - it may not be running the way I want yet, but you've helped me learn a load in the past couple of days :)

Cheers
Aidan

---

### Post by aidanandrach on 2009-07-05
Here's an update:

At this point I've given up on trying to install on the external HDD>

Instead, I've installed standard Ubuntu 9.04 via wubi on the internal HDD, which worked well.  I've then uploaded all the Ubuntu Studio packages, and the real time kernel, to give me a wubi version of Ubuntu Studio.  So far is going well, although I have had a couple of lock-ups for no apparent reason.  Will monitor and see how we go...

Might have a crack at installing the same way on to the external HDD...  Actually, with 16GB USB sticks being so cheap, maybe I'll do that instead...

Thanks for all the help - inspiring for a new convert to Ubuntu to find so much support here :)

---

### Post by presence1960 on 2009-07-05
> **aidanandrach said:**
> Here's an update:

At this point I've given up on trying to install on the external HDD>

Instead, I've installed standard Ubuntu 9.04 via wubi on the internal HDD, which worked well.  I've then uploaded all the Ubuntu Studio packages, and the real time kernel, to give me a wubi version of Ubuntu Studio.  So far is going well, although I have had a couple of lock-ups for no apparent reason.  Will monitor and see how we go...

Might have a crack at installing the same way on to the external HDD...  Actually, with 16GB USB sticks being so cheap, maybe I'll do that instead...

Thanks for all the help - inspiring for a new convert to Ubuntu to find so much support here :)

Glad you got it working. Enjoy Ubuntu!

---

