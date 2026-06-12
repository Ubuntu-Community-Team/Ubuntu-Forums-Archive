---
title: "GRUB error 17 again"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by grubnoob on 2009-07-21
I had a little dream where I installed Ubuntu (9.04, 64-biy) without any fuss. In this dream I would learn to use Ubuntu, including those cool terminal commands which don't make any sense to me. In this dream my computer was Windows free, just good old Ubuntu. But a piece of code called GRUB doesn't share this dream. So now I'm stuck with a fresh Ubuntu install on a dedicated 80 GB harddisk with a boot loader that doesn't know how to boot one operating system.

I have six harddisks installed on my computer. Two are IDE drives, 80 and 200 GB, and the remaining four are SATA. The 7th drive is my DVD drive connected to the computer via a SATA controller card.

The boot order according to my BIOS is the 80 GB IDE and then the DVD-drive.

I've followed some tutorials but they are not helping me. [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945) and [http://ubuntuforums.org/archive/index.php/t-5134.html](http://ubuntuforums.org/archive/index.php/t-5134.html) were followed in vain. I don't understand the sda1, hda1, hd0, etc. etc. so I probably made wrong changes. Still have the same error though. So I need specific guidelines for my specific situation. Is there anyone who knows for sure how to help me solve this problem?

I'd be glad to provide you with any information you require through the Live CD, as long as I get the step-by-step instructions should they involve the terminal commands.

---

### Post by presence1960 on 2009-07-21
to get a clearer picture of your setup boot off the live CD & download to your desktop the Boot Info Script 0.32 from here: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)
Once downloaded to desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will produce a RESULTS.txt file on your desktop. Paste the entire contents of that file back here. After pasting here be sure to highlight all text and then click the # sign to place code tags around the text. This info will show us exactly what you have . Also can you look in BIOS and list the boot order of your hard disks in BIOS please.

P.S. If your disk with Ubuntu is plugged into the sata controller card that won't work, it must be plugged into the motherboard for it to boot. I know you said you have an IDE 80 GB drive, but with all those HDD there is the chance you have another 80 GB drive. Either way the disk that has Ubuntu on it must be plugged directly into a motherboard IDE or Sata socket.

---

### Post by grubnoob on 2009-07-22
Sorry for taking such a long time with the answer, my internet was down. Here are the results. I won't be in for a couple of hours. But I'll get back as soon as I can.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #5 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf

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
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0cb60cb5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37d237d1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3e975627

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3de0082c

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb108b6ed

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   156,296,384   156,296,322  83 Linux


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7b156d4

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   390,716,864   390,716,802   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="725BDE7FFF5BE387" TYPE="ntfs" 
/dev/sdb1: UUID="9014CEC314CEAB92" LABEL="w" TYPE="ntfs" 
/dev/sdc1: UUID="92B8C397B8C3786D" LABEL="s" TYPE="ntfs" 
/dev/sdd1: UUID="0C3C2E713C2E55CC" LABEL="h" TYPE="ntfs" 
/dev/sde1: UUID="180457e1-b1ab-4f22-83f9-7d0f5088a00c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdf1: UUID="F8143EA9143E6B30" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sde1/boot/grub/menu.lst: ===========================

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
# root        (hd0,1)
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
# kopt=root=UUID=180457e1-b1ab-4f22-83f9-7d0f5088a00c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=180457e1-b1ab-4f22-83f9-7d0f5088a00c

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        180457e1-b1ab-4f22-83f9-7d0f5088a00c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=180457e1-b1ab-4f22-83f9-7d0f5088a00c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        180457e1-b1ab-4f22-83f9-7d0f5088a00c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=180457e1-b1ab-4f22-83f9-7d0f5088a00c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        180457e1-b1ab-4f22-83f9-7d0f5088a00c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde1 during installation
UUID=180457e1-b1ab-4f22-83f9-7d0f5088a00c /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde1: Location of files loaded by Grub: ===================


  23.9GB: boot/grub/menu.lst
  23.9GB: boot/grub/stage2
  23.9GB: boot/initrd.img-2.6.28-11-generic
  23.9GB: boot/vmlinuz-2.6.28-11-generic
  23.9GB: initrd.img
  23.9GB: vmlinuz
```

---

### Post by presence1960 on 2009-07-22
What is the boot order of your hard disks in BIOS? I am assuming you can boot into Ubuntu but not windows because you have no windows entry in your menu.lst & no boot files or directory for windows on any of your hard disks. Below is a snippet of my RESULTS.txt file showing what a good windows entry looks like. Get back with that info please and a description of what won't boot for you. I will be in work today so I won't be back until the evening. Post back the info please.

 > => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
   [COLOR="Red"] Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
[/COLOR]
sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

Note the entry in red. Windows is installed on sda2 and has bootfiles/dir. Yours is missing. I need an exact description of which OS won't boot and the exact order of your hard disk boot order in BIOS.

---

### Post by grubnoob on 2009-07-22
I have only one OS installed on my computer and it's Ubuntu on the 80 GB harddisk with ext3. The other harddisks are with NTFS but they are for storing my files. The order of my harddrive in the BIOS is:

1) IDE1 Master: 80 GB
2) IDE1 Slave: 200 GB
and then the remaining are SATA drives...

Where do I need to make changes for GRUB to boot Ubuntu?

---

### Post by presence1960 on 2009-07-22
> **grubnoob said:**
> I have only one OS installed on my computer and it's Ubuntu on the 80 GB harddisk with ext3. The other harddisks are with NTFS but they are for storing my files. The order of my harddrive in the BIOS is:

1) IDE1 Master: 80 GB
2) IDE1 Slave: 200 GB
and then the remaining are SATA drives...

Where do I need to make changes for GRUB to boot Ubuntu?

linux is on sde (80GB) which is set to boot first in your boot order in BIOS, but you have GRUB installed to sda. So when you boot your machine GRUB will not load because sde is set to boot first. You want to restore GRUB to sde so when you boot GRUB will take over. Do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd4,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd4,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd4)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

This should get you good to go. Numbering for drives and partitions start at 0 for GRUB. The first partition on the first disk = (hd0,0) the second partition on the first disk = (hd0,1), etc. The first partition on the second disk = (hd1,0), the second partition on the second disk = (hd1,1),etc. I think you get the idea. Ubuntu is on sde (hd4) on the first partition hence (hd4,0) for ubuntu.

Did you ever consider converting some of those storage drives to ext3 and maybe leave 1 or 2 as NTFS?

---

### Post by grubnoob on 2009-07-23
I was thinking about converting them eventually, it'll take some cleaning though. Throwing out garbage, moving around the keeping stuff then formatting. But it will happend I'm sure.

About GRUB... Dude, it works!!! Last time I tried to install Ubuntu was about a year ago. I had the same problem but I just gave up and didn't give it a go. I really appreciate your help!

---

### Post by presence1960 on 2009-07-23
> **grubnoob said:**
> I was thinking about converting them eventually, it'll take some cleaning though. Throwing out garbage, moving around the keeping stuff then formatting. But it will happend I'm sure.

About GRUB... Dude, it works!!! Last time I tried to install Ubuntu was about a year ago. I had the same problem but I just gave up and didn't give it a go. I really appreciate your help!

Glad you got it working...enjoy Ubuntu!

---

### Post by presence1960 on 2009-07-23
Next time you install Ubuntu, when you get to the window "Ready to install" click the advanced button. Then choose which hard drive to install GRUB to. In your present setup you would choose sde to install GRUB to MBR of that drive. See attached screenshot.

---

### Post by grubnoob on 2009-07-23
I think I understand now, thanks for the latter post.

Amazing with the forums. You're probably sitting in a different country now, yet we were able to solve this. The internetz is just awesome :)

Thank you, not only for solving my problem but also for telling me how to avoid it!

---

