---
title: "can't boot windows after ubuntu installation"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by super_awesome on 2009-07-02
Here is my setup before installing ubuntu:
partition 1: User (user files documents etc)
partition 2: OS (windows and program files)
partition 3: Page File (swap space for windows)
I decided to go the manual route and resize my user partion to allow space for ubuntu. Installs fine, edited menu.list to where windows was first. i didn't change anything in the actual boot settings. I tried to boot windows and I came up with the missing hal.dll crap. So i tried editing both the boot.ini and menu.list in just about every way i could think of, to no avail. I opened gparted to see the partition table to find that there are 5 partitions somehow. number 5 being an extended partition of number 1 i guess. So then i tried to use my windows cd to run the recovery console, couldn't figure out where it was, all i could find was the "automated" windows recovery console. After giving up on that i tried to boot into ubuntu again and now grub is gone! I am really close to just reinstalling both, but i am very determined to fix this at the same time. someone please help me.
thank you in advance.

---

### Post by hal10000 on 2009-07-02
First of all you should post the output of the command [COLOR="Red"]sudo fdisk -l[/COLOR], so that we can see the state of your partitions and can give you further help.

---

### Post by presence1960 on 2009-07-02
To get a better look at your actual setup download the Boot Info Script032.sh to your desktop by going here: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)

After download to desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on your desktop. This file will contain all necessary info about your setup and boot info. Paste the contents of the file back here. After pasting here highlight all text and click the # button on the toolbar to place Code tags around the text. Then submit your reply.

---

### Post by super_awesome on 2009-07-06
Thanks everyone for the replies. Sorry it took me a while but here it is:

UPDATE: I got grub reinstalled and got ubuntu to boot again, but still no love for windows.

**--Please ignore dev sdb, and sdc these are irrelevant (flash drives)--**

_here is the partition table from fdisk:_

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        1917    15390270    5  Extended
/dev/sda2   *        1918        6294    35158252+   7  HPFS/NTFS
/dev/sda3            6295        7099     6466162+  83  Linux
/dev/sda4            7100        7296     1582402+   b  W95 FAT32
/dev/sda5   *           2        1917    15390238+   7  HPFS/NTFS

```

_and here is the results from that script:_

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 114045435.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedaaedaa

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065    30,796,604    30,780,540   5 Extended
/dev/sda5    *         16,128    30,796,604    30,780,477   7 HPFS/NTFS
/dev/sda2    *     30,796,605   101,113,109    70,316,505   7 HPFS/NTFS
/dev/sda3         101,113,110   114,045,434    12,932,325  83 Linux
/dev/sda4         114,045,435   117,210,239     3,164,805   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 256 MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders, total 501759 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  99       501,247       501,149   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="7A9EB39E7311DC95" LABEL="USER" TYPE="ntfs" 
/dev/sda3: UUID="97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37" TYPE="ext4" 
/dev/sda4: LABEL="Page_File" UUID="7E8F-1405" TYPE="vfat" 
/dev/sda5: UUID="2A2802BA280284D3" LABEL="OS" TYPE="ntfs" 
/dev/sdb1: LABEL="256MB" UUID="4083-E6D5" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tristan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tristan)
/dev/sdb1 on /media/256MB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda5/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda3/boot/grub/menu.lst: ===========================

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
timeout		30

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
# kopt=root=UUID=97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37

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


###Windows####
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
rootnoverify	(hd0,2)
savedefault
chainloader	+1

###Linux####
title		Ubuntu 9.04
uuid		97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

#title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
#uuid		97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37
#kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37 ro  single
#initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

#title		Ubuntu 9.04, memtest86+
#uuid		97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37
#kernel		/boot/memtest86+.bin
#quiet

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=97adc6fa-6a8e-4ff6-a42f-d58eeb8d6c37 /               ext4    relatime,errors=remount-ro 0       1

=================== sda3: Location of files loaded by Grub: ===================


  54.8GB: boot/grub/menu.lst
  53.5GB: boot/grub/stage2
  53.5GB: boot/initrd.img-2.6.28-11-generic
  54.6GB: boot/initrd.img-2.6.28-13-generic
  53.6GB: boot/vmlinuz-2.6.28-11-generic
  52.3GB: boot/vmlinuz-2.6.28-13-generic
  54.6GB: initrd.img
  53.5GB: initrd.img.old
  52.3GB: vmlinuz
  53.6GB: vmlinuz.old
```

---

### Post by presence1960 on 2009-07-06
I am assuming your windows is installed to sda2. If it is in sda5 that is no good, you really don't want windows in an extended partition. Edit your windows entry in menu.lst to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
chainloader	+1


```

remember numbering for disks and partitions starts at 0 for GRUB. the first HDD is (hd0), the first partition on that HDD is (hd0,0), the second is (hd0,1) etc. The second HDD would be (hd1) and then for partitions would follow the same as above (hd1.0), (hd1,1) etc.

---

### Post by super_awesome on 2009-07-08
thanks for the reply, but I've tried that. I've tried hd0,0 through hd0,5 in the grub list with no luck whatsoever. I get different error messages however, I once got it to to say "starting windows...." but it didn't move past that screen. Maybe my boot.ini file is wrong? I have tried it in as many ways as i could think of though so I'm really stuck.

---

### Post by merlinus on 2009-07-08
Back up critical data and reinstall.  Better than bashing your brains out....

Window will flat out not run if installed into a logical partition.

---

### Post by super_awesome on 2009-07-08
one more reason to hate windblowz. but out of curiosity, how did that happen? I had windows installed first, then I installed ubuntu. Did ubuntu move windows to an extended partition?

---

### Post by merlinus on 2009-07-08
If you have necessary apps that absolutely need windows, then you might try virtualbox, a linux vm.

BTW, in looking again at the fdisk output, only one of the ntfs partitions is logical.  So which one is windows, sda2 or sda5?  If the latter, then reinstall.  If the former, perhaps there are a few more things to try.

But I wonder how an extended partition got to be first on your hdd???

---

### Post by super_awesome on 2009-07-08
that's where i got confused... When i reinstalled windows the last time, it gave the operating system partition the "D:" label because my user partition was already there as "C:". I think that somehow that has something to do with it. Here is what my partitions look like in gparted, see attachment.

---

### Post by merlinus on 2009-07-08
Looks to me like windows is installed in sda5, which is a logical partition.  And you are probably correct about what happened, i.e. windows installing to drive d rather than c.

So the windows install created the extended partition...

---

### Post by super_awesome on 2009-07-08
nice. well at least i have backups and a separate partition. i guess i know how i'll be spending my evening. oh well... i appreciate everyone's help and input. great community here.

---

### Post by merlinus on 2009-07-08
Good luck, and let us know how it goes.

---

### Post by super_awesome on 2009-07-10
ok so here's my plan, let me know what you guys think:

backup anything i may need on my 'OS' partition
delete 'OS' and 'Page file' partitions
merge both to one partition
reinstall windows to new partition
reinstall grub

i don't think having the windows swap space on a separate partition was of that great gain anyway. it just lead to problems so i'll just use it on the same partition windows is on.

so that should work right? I have all my personal files on the separate 'user' partition plus they're backed up so worst case scenario I'll just wipe it all and reinstall everything. thank you all for your input.

---

### Post by merlinus on 2009-07-10
Sounds good to me, and bonne chance!

---

### Post by super_awesome on 2009-07-10
if it were up to me however, i would leave out windows completely, but i have to ween my wife (and myself i guess) off of windows. that will take some time...

---

### Post by super_awesome on 2009-07-13
well after all that; i'm still running in to the same problem. I deleted all partitions except for ubuntu and user and installed windows. windows worked fine until i reinstalled grub. then i had just ubuntu again. i tinkered until i was just so uber-frustrated i couldn't look at it anymore. I give up for now. I am installing nothing but windows on the hdd for now. if i want to use ubuntu, i'll run it off my flash drive.
thanks for the input guys.

---

### Post by Sonicjet on 2009-08-01
Hey,I am haveing the same problem and I think I know whats going on...your windows boot is linited to 256 ram,AKA not enough for vista,thus a forced restart,I have windows 7 x64 with this prob jut it will Barely boot,just barely,it automatically shuts all unnessary things off,like aero,and is runing at ~230Mb,Let me figue out how to fix it and I'll post your fix.

---

