---
title: "GRUB Boot Problems"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by ticker on 2009-02-01
I recently installed Unbuntu 8.10 successfully alongside Vista, everything was running fine until about an hour ago when I installed Paragon Partition Manager 9 on Vista. This software had somehow installed its own boot loader without me realising that it had done so. Now when I rebooted the first time after this Paragon's boot loader showed up with the Vista option to boot and an option to remove this loader but no entry for Unbuntu. I booted to Vista which worked OK, on my next reboot I removed the Paragon loader and on my next reboot is where my problems really began because this time I got nothing at all, I was expecting my usual GRUB loader but instead all I did get was a never ending screen full of the word GRUB!

Any and all assistance in resolving this problem of mine will be greatly appreciated.

ticker

---

### Post by ajgreeny on 2009-02-01
I can see no reason why it should not be possible to reinstall grub over this paragon/windows bootloader using the ubuntu live CD, which I trust you have.

Follow this guide:-
Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by ticker on 2009-02-01
Thanks for the assistance AJ but I am afraid I did not have any success with your suggestions. 

Firstly, I could not boot from my LiveCD, 8.10, I got the following response,

1. Starting System Tools Backends system-tools-backends.ok
2. Starting deferred execution scheduler atd.ok
3. Starting Periodic command scheduler crond.ok
4. Enabling additional executable binary formats bin fmt-support. ok
5. Checking Battery state. ok
.........then the system just hangs, turning off the machine then gives me
Stopping Gnome display manager.

My system does boot from my LiveCD 8.04 however, but it does not find stage1 but does find stage2 and I am able to complete the process with success until I reboot again and I still get the screen full of repeating GRUBs'.

Thanks again for your assistance.
ticker

---

### Post by caljohnsmith on 2009-02-01
Did you make sure to run the grub command as root, i.e. "sudo grub" and not just "grub"? That can be a cause of Grub giving a "file not found" error when really the file exists. If that is not your case, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD 8.04 desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by ticker on 2009-02-01
Hi CalJohnSmith,

Thanks for the assistance that you have provided. I have run through the previous suggestion from AJ, this time finding stage1 and completeing successfully, but alas with the same results on reboot, a screen full of GRUBS again!!!

So I have followed your suggestion and provide the results.txt here

============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on boot drive #105 in 
    partition #225 for /e8del.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x773e149c

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Unknown
/dev/sda2    *      3,074,048   197,634,047   194,560,000   7 HPFS/NTFS
/dev/sda3         197,634,048   390,719,487   193,085,440   7 HPFS/NTFS

/dev/sda3 ends after the last cylinder of /dev/sda

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5d379805

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   209,005,649   209,005,587   f W95 Ext d (LBA)
/dev/sdb5               4,096   201,189,119   201,185,024   7 HPFS/NTFS
/dev/sdb6         201,198,123   209,005,649     7,807,527  82 Linux swap / Solaris
/dev/sdb2         209,005,650   390,716,864   181,711,215  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 8086 MB, 8086617600 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794175 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             44    15,679,439    15,679,396   b W95 FAT32


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24472446

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32     4,028,415     4,028,384   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F83655903655512C" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="460258AE0258A529" LABEL="Vista" TYPE="ntfs" 
/dev/sda3: UUID="869C5C8B9C5C779F" LABEL="Data" TYPE="ntfs" 
/dev/sdb2: UUID="643b205d-4b75-40e7-8230-a87da8d82118" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="7C7656F77656B19E" LABEL="WEB SITES" TYPE="ntfs" 
/dev/sdb6: TYPE="swap" UUID="ef15a53c-ce97-449b-9432-02a1467769a3" 
/dev/sdc1: LABEL="FLASH DRIVE" UUID="7801-9E81" TYPE="vfat" 
/dev/sdd1: SEC_TYPE="msdos" LABEL="FLASH DRIVE" UUID="618B-70C8" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

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
/dev/sdd1 on /media/FLASH DRIVE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdc1 on /media/FLASH DRIVE_ type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

=========================== sdb2/boot/grub/menu.lst: ===========================

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
default		6

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
# kopt=root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=643b205d-4b75-40e7-8230-a87da8d82118

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdb2 :
UUID=643b205d-4b75-40e7-8230-a87da8d82118	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda3 :
UUID=869C5C8B9C5C779F	/media/Data	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdc1 :
UUID=07D3-021B	/media/DellUtility	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sda2 :
UUID=460258AE0258A529	/media/Vista	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb5 :
UUID=7C7656F77656B19E	/media/WEB\040SITES	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=F83655903655512C	/media/WinRE	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdc2 :
UUID=68ACEB2BACEAF30C	/media/disk	ntfs-3g	defaults,nosuid,nodev,uhelper=hal,locale=en_GB.UTF-8	0	0
UUID=5C69-3454	/media/TUFTYDRIVE2	vfat	defaults,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush	0	2
#Entry for /dev/sdb6 :
UUID=ef15a53c-ce97-449b-9432-02a1467769a3	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0



=================== sdb2: Location of files loaded by Grub: ===================


 183.2GB: boot/grub/menu.lst
 183.2GB: boot/grub/stage2
 183.3GB: boot/initrd.img-2.6.27-7-generic
 183.3GB: boot/initrd.img-2.6.27-9-generic
 183.3GB: boot/vmlinuz-2.6.27-7-generic
 183.3GB: boot/vmlinuz-2.6.27-9-generic
 183.3GB: initrd.img
 183.3GB: initrd.img.old
 183.3GB: vmlinuz
 183.3GB: vmlinuz.old

---

### Post by caljohnsmith on 2009-02-01
Ticker, can you change your BIOS to boot the Ubuntu sdb drive on start up instead of your Vista sda drive? In other words, can you change your BIOS boot order to boot sdb first? If so, I think that might solve your problem, because it appears you have Grub correctly installed all ready to your sdb drive. How about giving that a shot and let me know how far you get.

---

### Post by ticker on 2009-02-02
Hi CalJohnSmith,

You are a hero, that saved my skin!! Worked a treat and now I can forget any thoughts I had about reinstalling!!

Many thanks again for your swift and spot on advice.

GBY

ticker

---

### Post by caljohnsmith on 2009-02-02
Glad to hear that worked OK, ticker, but I think there is one more thing you will want to take care of. I don't know if you've noticed yet, but I don't think the Vista entry in your Grub menu works any more. You'll need to update your menu.lst in order to boot Vista since you are now booting the Ubuntu drive on start up:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your current Vista entry with the two following entries:
```
title       Windows Vista (hd1)
rootnoverify     (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,1)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Reboot, try both Vista entries from the Grub menu, and most likely one should work. When you find which one works, you can delete the other one from your menu.lst when you get back into Ubuntu. If you have any other problems with it, let me know. Otherwise let me know how it goes.

---

### Post by ticker on 2009-02-04
Yeah I had noticed that I could not boot into Vista and I had been fishing around for an answer to this problem before I got to read your last post. I have followed your instructions as you advised but I am afraid that both options that I entered into the menu.lst gave me the same result when I tried to boot from each of them and this is the message I received:

ERROR 11: unrecognised device string

Thanks again CalJohn for all your help.

ticker

---

### Post by caljohnsmith on 2009-02-04
A Grub error 11 is almost always due to a typo in the menu.lst OS entry; can you copy/paste the entries that I posted? If not, be sure that all the (hd0)'s use zero and not a capital letter O for example. Please check your entries for typos, and I think that might resolve the problem. Let me know how that goes.

---

### Post by ticker on 2009-02-09
Hi Caljohn, been so busy lately that I've only just found time to get back to you.  After removing the original entry for Vista in Grub and double checking for typo's in the new entry's I am still getting Error 11 on both of the two new Vista entries on reboot. So I am at a loss at what next to try, do you have any further suggestions?  Help!!

Thanks again foe all your help.

ticker

---

### Post by caljohnsmith on 2009-02-09
Can you copy/paste the entire contents of your menu.lst to your next post? I think that will help clarify what the problem might be.

---

### Post by ticker on 2009-02-12
Hi there again Caljohn,
  
I'm afraid I have hit another problem trying to get the listing you requested of me.
Instead I get the following,

ubuntu@ubuntu:~$ sudo bash |/desktop/boot_info_script*.sh
bash: /desktop/boot_info_script*.sh: No such file or directory
bash: echo: write error: Broken pipe

So what should I do now? Further assistance Caljohn will be greatly appreciated.

ticker

---

### Post by caljohnsmith on 2009-02-12
> **ticker said:**
> 
ubuntu@ubuntu:~$ sudo bash [COLOR="Red"]|[/COLOR]/[COLOR="Red"]d[/COLOR]esktop/boot_info_script*.sh
bash: /desktop/boot_info_script*.sh: No such file or directory
bash: echo: write error: Broken pipe

It looks like you are mistyping, because you put a "pipe" or "|" in the above command where you don't need one (that should be a tilde ~ instead); also, "desktop" needs to be capitalized since Linux is case sensitive. It should simply be:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by ticker on 2009-02-13
Hi there again,

Silly mistake, sorry!!

Here are the results that you asked for earlier.

ticker

============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on boot drive #105 in 
    partition #225 for /e8del.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x773e149c

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Unknown
/dev/sda2    *      3,074,048   197,634,047   194,560,000   7 HPFS/NTFS
/dev/sda3         197,634,048   390,719,487   193,085,440   7 HPFS/NTFS

/dev/sda3 ends after the last cylinder of /dev/sda

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5d379805

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   209,005,649   209,005,587   f W95 Ext d (LBA)
/dev/sdb5               4,096   201,189,119   201,185,024   7 HPFS/NTFS
/dev/sdb6         201,198,123   209,005,649     7,807,527  82 Linux swap / Solaris
/dev/sdb2    *    209,005,650   390,716,864   181,711,215  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24472446

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     4,028,415     4,028,384   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F83655903655512C" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="460258AE0258A529" LABEL="Vista" TYPE="ntfs" 
/dev/sda3: UUID="869C5C8B9C5C779F" LABEL="Data" TYPE="ntfs" 
/dev/sdb2: UUID="643b205d-4b75-40e7-8230-a87da8d82118" TYPE="ext3" 
/dev/sdb5: UUID="7C7656F77656B19E" LABEL="WEB SITES" TYPE="ntfs" 
/dev/sdb6: UUID="ef15a53c-ce97-449b-9432-02a1467769a3" TYPE="swap" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="FLASH DRIVE" UUID="618B-70C8" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda3 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/Vista type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/WEB SITES type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/WinRE type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ticker/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ticker)
/dev/sdc1 on /media/FLASH DRIVE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

=========================== sdb2/boot/grub/menu.lst: ===========================

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
default saved

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
# kopt=root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=643b205d-4b75-40e7-8230-a87da8d82118

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
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=643b205d-4b75-40e7-8230-a87da8d82118 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		643b205d-4b75-40e7-8230-a87da8d82118
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

title		Windows Vista (hd1)
rootnoverify	(hd1,1)
map		(hd0)(hd1)
map		(hd1)(hd0)
chainloader	+1

title		Windows Vista (hd2)
rootnoverify	(hd2,1)
map		(hd0)(hd2)
map		(hd2)(hd0)
chainloader	+1




=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdb2 :
UUID=643b205d-4b75-40e7-8230-a87da8d82118	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda3 :
UUID=869C5C8B9C5C779F	/media/Data	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdc1 :
UUID=07D3-021B	/media/DellUtility	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sda2 :
UUID=460258AE0258A529	/media/Vista	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb5 :
UUID=7C7656F77656B19E	/media/WEB\040SITES	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=F83655903655512C	/media/WinRE	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdc2 :
UUID=68ACEB2BACEAF30C	/media/disk	ntfs-3g	defaults,nosuid,nodev,uhelper=hal,locale=en_GB.UTF-8	0	0
UUID=5C69-3454	/media/TUFTYDRIVE2	vfat	defaults,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush	0	2
#Entry for /dev/sdb6 :
UUID=ef15a53c-ce97-449b-9432-02a1467769a3	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0



=================== sdb2: Location of files loaded by Grub: ===================


 183.3GB: boot/grub/menu.lst
 183.2GB: boot/grub/stage2
 183.3GB: boot/initrd.img-2.6.27-11-generic
 183.3GB: boot/initrd.img-2.6.27-7-generic
 183.3GB: boot/initrd.img-2.6.27-9-generic
 183.3GB: boot/vmlinuz-2.6.27-11-generic
 183.3GB: boot/vmlinuz-2.6.27-7-generic
 183.3GB: boot/vmlinuz-2.6.27-9-generic
 183.3GB: initrd.img
 183.3GB: initrd.img.old
 183.3GB: vmlinuz
 183.3GB: vmlinuz.old
```

```

---

### Post by caljohnsmith on 2009-02-13
> **ticker said:**
> 
```

title		Windows Vista (hd1)
rootnoverify	(hd1,1)
map		(hd0[COLOR="Red"])([/COLOR]hd1)
map		(hd1[COLOR="Red"])([/COLOR]hd0)
chainloader	+1

title		Windows Vista (hd2)
rootnoverify	(hd2,1)
map		(hd0[COLOR="Red"])([/COLOR]hd2)
map		(hd2[COLOR="Red"])([/COLOR]hd0)
chainloader	+1
```

Spaces, my friend, you need spaces. :) There should be at least one space between the mapped (hdX) drives:
```

map	(hd0)   (hd1)
map	(hd1)   (hd0)
```
Try doing that for both entries and let me know how that goes. Also, one more thing to take care of would be to restore a Windows MBR to your Vista drive, so how about doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
And *please* be careful not to make any typos. :)

---

### Post by ticker on 2009-02-13
Hi CalJohn,

Ouch!, A very well deserved rap on the knuckles, I certainly warranted that one for such basic errors. I apologize if I have taken up more of your time than may have been necessary.

I would like to thank you for all your efforts on solving my problem and I would like to report that your solution has been completely successful, in the end it was the first new entry that worked.

Thanks again,
ticker

---

### Post by caljohnsmith on 2009-02-13
No problem, I'm really glad you can now boot Vista OK now. Cheers and enjoy your dual-boot Ubuntu/Vista setup. :)

---

