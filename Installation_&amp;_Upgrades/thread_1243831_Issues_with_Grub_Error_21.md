---
title: "Issues with Grub Error 21"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by Jvellos on 2009-08-18
Hello, all. 

I recently got a new laptop, an HP pavilion DV6. Along with it, I got an external hard drive, a 1 TB Kanguru which I was going to install Ubuntu on. (For more specific info about both, see [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4184090&CatId=136](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4184090&CatId=136) for the hard drive and [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4824081&CatId=1900](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4824081&CatId=1900) for the laptop.)

So, they arrive in the mail Monday, and, after firing up and configuring Vista, I plug in the external drive and put in the Ubuntu CD. I tell Ubuntu to install itself to the external drive, partitioning 100 GB as EXT3 for Ubuntu, 5 GB for swap space, and leaving the rest formatted for Windows. The installation then proceeds, and appears to go normally. However, when I restart the computer, I get the message:
Grub Loading Stage 1.5

Grub Loading please wait....
Error 21

And now the only way I can boot is off the Ubuntu disk. I have Googled the error and found that it means that the disk cannot be found, and I have attempted the solutions proposed at [http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html), [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8978](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8978), and a few others (everything that shows up on the first few pages of Google). I cannot use SuperGrub because the only computer which I have that can burn a disk is the one that needs the Ubuntu disk to run. I cannot use the Windows Vista disk recovery console to run fixmbr, because the computer did not come with a Vista recovery CD. I have never before had to deal with Grub issues, and I know nothing of how to configure it. The information I get from putting "man grub" into the terminal is confusing at best. In short, I need someone to tell me what to do to configure Grub so that it allows me to boot into Vista on the internal HD, and boot into Ubuntu when my external drive is plugged in. 

Thanks,
Jvellos

EDIT: I realize that the way I phrased that might not be clear. By "the only way I can boot is off the Ubuntu disk," I mean, "the only way I can boot is off the Ubuntu Live CD." Sorry for any confusion.

---

### Post by presence1960 on 2009-08-18
It appears that you put the GRUB bootloader on the Vista internal disk. But to be sure exactly how your current setup is and to see your boot process boot off the Ubuntu Live Cd with the external drive plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and click on the link in my signature line to download the Boot Info Script 0.32 to the desktop. Once downloaded to desktop open a terminal & run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. paste the entire contents of that file back here. Once pasted highlight all the text and click # on the toolbar to place code tags around the text.

---

### Post by Jvellos on 2009-08-18
Thanks, Presence. Here's the output you requested:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
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

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05067d34

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   598,802,431   598,800,384   7 HPFS/NTFS
/dev/sda2         598,802,432   625,135,615    26,333,184   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d3cdf

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,931,703,794 1,931,703,732  83 Linux
/dev/sdb2       1,931,703,795 1,953,520,064    21,816,270   5 Extended
/dev/sdb5       1,931,703,858 1,953,520,064    21,816,207  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3FDBAD5436E8BEDE" TYPE="ntfs" 
/dev/sda2: UUID="B6CCEA69CCEA237B" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sdb1: UUID="210aefcc-26d3-47d2-a7ce-43af78a0a357" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="6b0fc677-6b4a-4d7c-a5a2-fad44da1b1f5" TYPE="swap" 

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
# kopt=root=UUID=210aefcc-26d3-47d2-a7ce-43af78a0a357 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=210aefcc-26d3-47d2-a7ce-43af78a0a357

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
uuid        210aefcc-26d3-47d2-a7ce-43af78a0a357
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=210aefcc-26d3-47d2-a7ce-43af78a0a357 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        210aefcc-26d3-47d2-a7ce-43af78a0a357
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=210aefcc-26d3-47d2-a7ce-43af78a0a357 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        210aefcc-26d3-47d2-a7ce-43af78a0a357
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=210aefcc-26d3-47d2-a7ce-43af78a0a357 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=6b0fc677-6b4a-4d7c-a5a2-fad44da1b1f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 988.8GB: boot/grub/menu.lst
 988.9GB: boot/grub/stage2
 988.8GB: boot/initrd.img-2.6.28-11-generic
 988.8GB: boot/vmlinuz-2.6.28-11-generic
 988.8GB: initrd.img
 988.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  df 3c 0d 00 00 00 00 01  |.........<......|
000001c0  01 00 83 fe ff ff 3f 00  00 00 b4 75 23 73 00 fe  |......?....u#s..|
000001d0  ff ff 05 fe ff ff f3 75  23 73 ce e3 4c 01 00 00  |.......u#s..L...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by presence1960 on 2009-08-18
Ok you did install GRUB to MBR of your internal disk (sda). You have a recovery partition (sda2) which will restore your hard disk to factory image. We can fix this without doing that. The reson you can't boot without your external plugged in is GRUB is on the MBR of sda and that takes over when you boot and it looks to your Ubuntu partition on sdb (external drive) for menu.lst. You need to restore windows bootloader to MBR of sda. Unfortunately you have a recovery partition and don't have access to recovery console. Fortunately there is a work around for that. Go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download the iso for your version of vista. Burn it as an image to CD/DVD.

When the CD/DVD is burned boot from it with your external disk unplugged. Follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista. This will put Vista's bootloader back on MBR of your internal disk. When completed reboot without the CD/DVD and you should boot directly into windows. You are halfway done!

With the external disk plugged in boot the Ubuntu Live Cd. You are going to install GRUB to MBR of the external disk (sdb). Follow this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR of sdb.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Now one more adjustment. Boot again with no CD and go into BIOS. You want to set your external drive to boot ahead of the internal drive. This will accomplish what you want. If you boot with the external drive unplugged windows bootloader will boot directly into windows. if you boot with the external plugged in GRUB will take over and you can boot into Ubuntu. Any problems or questions post back here

---

### Post by presence1960 on 2009-08-18
For future reference: when you install Ubuntu again and you reach the Ready to install window (see pic below) click the advanced tab to choose where to install GRUB. In your case it would be sdb - which equates to MBR of the second hard disk.

---

### Post by Jvellos on 2009-08-19
All right, I've used my friend's laptop to download and burn the Vista repair disc. I followed the instructions, and can now access my Vista install again. I then followed your instructions for reconfiguring Grub, and it said that it was successful. I then went into the BIOS and set "USB Hard Drive" above "Notebook Hard Drive" in the boot priority list. However, I still cannot boot to the Ubuntu installation there. The computer has an option in the startup menu that allows you to select from boot devices manually (overriding the BIOS preferences), and I only see the options "Notebook Hard Drive" and "Internal CD-ROM Drive." Apparently, the BIOS does not see the USB drive as a bootable device. Is there some 'bootable' flag I need to set on the external drive? Do I need to update my BIOS? In short, what's going on here, and how do I fix it?

---

### Post by presence1960 on 2009-08-19
> **Jvellos said:**
> All right, I've used my friend's laptop to download and burn the Vista repair disc. I followed the instructions, and can now access my Vista install again. I then followed your instructions for reconfiguring Grub, and it said that it was successful. I then went into the BIOS and set "USB Hard Drive" above "Notebook Hard Drive" in the boot priority list. However, I still cannot boot to the Ubuntu installation there. The computer has an option in the startup menu that allows you to select from boot devices manually (overriding the BIOS preferences), and I only see the options "Notebook Hard Drive" and "Internal CD-ROM Drive." Apparently, the BIOS does not see the USB drive as a bootable device. Is there some 'bootable' flag I need to set on the external drive? Do I need to update my BIOS? In short, what's going on here, and how do I fix it?

In my BIOS the setting is under it's own heading of "USB or Removable" I have that as fist boot, then CD then hard disk. within each category I can set order of those particular devices within that category. See if your BIOS is that way.

---

### Post by Jvellos on 2009-08-19
All right. In order to access the Boot Order menu, I go through the following:

```
1. Once I'm in the BIOS, I go over to the System Configuration menu.

2. From there, I select Boot Options.

3. Within Boot Options, I have the following options:
   A. f10 and f12 Delay (sec)
   B. CD-ROM Boot (enabled or disabled, currently enabled)
   C. Floppy Boot (enabled or disabled, currently disabled)
   D. Internal Network Adapter (enabled or disabled, currently disabled)
   E. Boot Order

4. I select Boot Order, and see this list, in order of priority:
   A. USB diskette on key/USB hard disk
   B. Notebook Hard Drive
   C. Internal CD/DVD-ROM Drive
   D. External CD/DVD-ROM Drive
   E. ! USB Floppy Drive
   F. ! Network Adapter 
```*Note: the exclamation point next to the last two options simply means that they are disabled in the previous menu.*

---

### Post by presence1960 on 2009-08-19
> **Jvellos said:**
> All right. In order to access the Boot Order menu, I go through the following:

```
1. Once I'm in the BIOS, I go over to the System Configuration menu.

2. From there, I select Boot Options.

3. Within Boot Options, I have the following options:
   A. f10 and f12 Delay (sec)
   B. CD-ROM Boot (enabled or disabled, currently enabled)
   C. Floppy Boot (enabled or disabled, currently disabled)
   D. Internal Network Adapter (enabled or disabled, currently disabled)
   E. Boot Order

4. I select Boot Order, and see this list, in order of priority:
   A. USB diskette on key/USB hard disk
   B. Notebook Hard Drive
   C. Internal CD/DVD-ROM Drive
   D. External CD/DVD-ROM Drive
   E. ! USB Floppy Drive
   F. ! Network Adapter 
```*Note: the exclamation point next to the last two options simply means that they are disabled in the previous menu.*

4a should do it. if not, i hate to do this to you, but could you run the boot info script again please wiyh external plugged in..

---

### Post by Jvellos on 2009-08-19
I've already set the USB hard drive above the notebook hard drive in priority, that's why it comes first in the list. I'll reboot with the Live CD and give you the output in a minute.

---

### Post by Jvellos on 2009-08-19
Here's the output again, Presence:```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
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

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05067d34

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   598,802,431   598,800,384   7 HPFS/NTFS
/dev/sda2         598,802,432   625,135,615    26,333,184   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d3cdf

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,931,703,794 1,931,703,732  83 Linux
/dev/sdb2       1,931,703,795 1,953,520,064    21,816,270   5 Extended
/dev/sdb5       1,931,703,858 1,953,520,064    21,816,207  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3FDBAD5436E8BEDE" TYPE="ntfs" 
/dev/sda2: UUID="B6CCEA69CCEA237B" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sdb1: UUID="210aefcc-26d3-47d2-a7ce-43af78a0a357" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="6b0fc677-6b4a-4d7c-a5a2-fad44da1b1f5" TYPE="swap" 

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
# kopt=root=UUID=210aefcc-26d3-47d2-a7ce-43af78a0a357 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=210aefcc-26d3-47d2-a7ce-43af78a0a357

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
uuid        210aefcc-26d3-47d2-a7ce-43af78a0a357
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=210aefcc-26d3-47d2-a7ce-43af78a0a357 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        210aefcc-26d3-47d2-a7ce-43af78a0a357
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=210aefcc-26d3-47d2-a7ce-43af78a0a357 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        210aefcc-26d3-47d2-a7ce-43af78a0a357
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=210aefcc-26d3-47d2-a7ce-43af78a0a357 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=6b0fc677-6b4a-4d7c-a5a2-fad44da1b1f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 988.8GB: boot/grub/menu.lst
 988.9GB: boot/grub/stage2
 988.8GB: boot/initrd.img-2.6.28-11-generic
 988.8GB: boot/vmlinuz-2.6.28-11-generic
 988.8GB: initrd.img
 988.8GB: vmlinuz
```

---

### Post by makinasvp on 2009-08-19
nice...

---

### Post by presence1960 on 2009-08-19
For some reason everything looks perfect but your USB drive will not boot first. You may want to check with your manufacturer's documentation to see if your machine is capable of booting from USB and how to do it. According to the output you just posted everything is set right.

---

### Post by presence1960 on 2009-08-19
I just went to HP's web site and looked up your documentation. You do have it set correctly in BIOS as far as I can see and your install of both Windows & Ubuntu is correct. I would call HP since it is brand new and see if they can tell you how to get your USB hard disk to boot.

---

### Post by Jvellos on 2009-08-19
Yeah, I've been looking at the documentation, and my findings agree with yours. As near as I can tell, everything is configured the way it should be for this to work. It's after hours, so I'll have to wait until tomorrow to call them. I'll post with results tomorrow.

---

### Post by presence1960 on 2009-08-19
> **Jvellos said:**
> Yeah, I've been looking at the documentation, and my findings agree with yours. As near as I can tell, everything is configured the way it should be for this to work. It's after hours, so I'll have to wait until tomorrow to call them. I'll post with results tomorrow.

let us know what happens, we want your Ubuntu to work for you.

---

### Post by Jvellos on 2009-08-20
Well, I talked with the HP people, and they told me where to get a BIOS update, and that did the trick. When my drive is plugged in, I am now directed to Grub, and I have the options of either running Ubuntu or Vista. However, when I try to run Ubuntu, I get a different issue. The Ubuntu loading screen comes up, and the small white bar runs back and forth for perhaps ten or fifteen seconds before I get the following message (which I jotted down, word for word):
```
Gave up waiting for root device. Common problems:
   - Boot args (cat /proc/cmdline)
      - Check rootdelay= (did the system wait long enough?)
      - Check root= (did the system wait for the right device?)
   - missing modules (cat /proc/modules, ls /dev)
ALERT! /dev/disk/by-vvid/210aefcc-26d3-47d2-a7ce-431f75a0a357 does not exist. Dropping to a shell!

BusyBox v1.10.2(Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)
```I then tried booting it up in the 'recovery mode' which, after a ton of fast output, eventually stopped at ```
Begin: Waiting for root file subsystem.
[   5:024544] r8159 Gigabit Ethernet driver 2.3LK-NAPJ loaded
[   5:024544] r8159 0000: 09:00.0:PCI INT A->GSI18(level, low)-> IRQ 18
[   5:024544] eth0:RTL8102e at 0xffffc300040b0000, 00:23:8b:8c:48:77, XID 24c00000 IRQ 2299
Done.
Gave up waiting for root device. Common problems:
   - Boot args (cat /proc/cmdline)
      - Check rootdelay= (did the system wait long enough?)
      - Check root= (did the system wait for the right device?)
   - missing modules (cat /proc/modules, ls /dev)
ALERT! /dev/disk/by-vvid/210aefcc-26d3-47d2-a7ce-431f75a0a357 does not exist. Dropping to a shell!

BusyBox v1.10.2(Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)
```So, uh, what's going on here?

---

### Post by presence1960 on 2009-08-20
I know this is a pain, but you did all this work so far. If no one else can give a suggestion for that error, I would try reinstalling Ubuntu. This time when you get to the Ready to install window of the installer click the advanced tab and put GRUB on MBR of your external drive sdb. here is a screenshot of that window below.

That error says your Ubuntu partition does not exist. I checked the UUID # from your boot info script output and that UUID # is indeed the Ubuntu / partition. I would reinstall unless someone else can give you a fix for that.

---

### Post by Jvellos on 2009-08-20
Thanks again, Presence. I'll do that and post back when it's done.

---

### Post by Jvellos on 2009-08-20
I re-installed Ubuntu onto the external drive. It still doesn't work, I'm getting the same error after I get through Grub. Additionally, I've noticed two odd things:

1. When the drive is plugged in via eSATA (regardless of whether USB is plugged in beside it or not), I don't see it as bootable in the BIOS.

2. When eSATA is *not* plugged in (so the drive is only connected via USB), I do not see it as a drive within the Ubuntu installer. 

So it needs to be plugged in via eSATA to install the OS, but it needs to be plugged in only by USB to be booted from. (Yes, I've tried plugging both in. It installs, but won't boot.) Any suggestions?

---

### Post by Jvellos on 2009-08-21
I've now tried it with Kubuntu, to see if there's some difference that would make it work, there isn't. The BIOS refuses to work via eSATA, and the OS refuses to work via USB. Can anyone help?

---

