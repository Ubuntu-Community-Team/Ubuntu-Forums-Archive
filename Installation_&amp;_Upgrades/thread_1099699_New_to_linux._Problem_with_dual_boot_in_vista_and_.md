---
title: "New to linux. Problem with dual boot in vista and unbuntu"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by hosinfefer on 2009-03-18
Hello everyone

I have a problem with setting up dual boot. I managed to get linux (64 bit desktop 8.10 i think) to a 300gb v.raptor drive. I also had a vista 64bit ult loaded to a second 300gb v.raptor drive. Now when my computer boots I see a boot loader program (is that grub) and it has 4 linux choices (looks like 2 differnt kernal ver. and 1 normal and 1 recovery mode for each totaling 4. I also see a windows vista\longhorn option. When I click on it, the cursor jumps to the top option which is the upgraded kernal on ubuntu. Is there a way to fix the MBR so I can boot into vista from that menu. There are some options for editing the vista selection...but I have not clue as to what im doing. 

System info
e8400 overclocked to 3.8 (does ubuntu see overclockes?)
8gb ocz 1110mhz (overclocked
gts 260 ocd
3 v.raptors and 1 1tb wd green


I also looked here [http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/](http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/) 
hope I did that post right.

thanks for your help guys

---

### Post by Therion on 2009-03-18
It sounds like everything is set up correctly.  

What you're seeing is GRUB, with the various boot options (Linux kernels/Ubuntu and Vista) and it sounds as if your Vista partition is being recognized (it's a bootable option in your GRUB screen).

But just to make sure we're clear on this...

You use the up/down arrow keys to select the boot option from GRUBS list of choices.  You don't click with your mouse.

---

### Post by hosinfefer on 2009-03-18
Yes i use the up and down arror to "highlight" the correct option. when I pick the new kernal unbuntu and hit enter it jumps right to the loading screen and with a few seconds im looking at my desktop. When i down arror to visa\longhorn and hit enter, the highlighted box jumps up to the top of the menu (newest ubuntu). Its almost like GRUB is biased towards linux hahaha. GRUB see vista..just wont do anything when i click on it. Is ther a way to "refresh" the boot record for windows. When I installed ubuntu I put the bootloader on the same partition as windows. Is that wrong?

---

### Post by meierfra. on 2009-03-18
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by hosinfefer on 2009-03-18
not sure if I have the live cd. I put in the cd i loaded ubuntu with and i have a few options. 
1) Try without any changes to the computer
2) install Ubuntu
3) check cd for integ.
4) test mem
5)boot from first hard drive


Now when I click on boot from first hard drive. GRUB comesa up. Above the vista\longhorn option is a selection called "other os". When I click on it I get an error that says "unrecoegnized device string, Press any key" it then takes me back to grub.

How do I get the option to copy the info down? do I have to boot from that cd and then hit something to get a cmd prompt?

---

### Post by meierfra. on 2009-03-18
Sorry, I was sleeping.  You don't need to boot into the LiveCD. Just boot into your regular Ubuntu and follow my instruction.

(Just for future reference. You seem to have a Live CD and the first option "(1) Try without any changes to the computer"  should boot you into the Ubuntu on the LiveCD)

---

### Post by hosinfefer on 2009-03-18
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 186892351 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdc1 starts at sector 34.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1dd67f33

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sda2         204,802,048   586,067,967   381,265,920   7 HPFS/NTFS

/dev/sda2 ends after the last cylinder of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b89f2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   562,258,934   562,258,872  83 Linux
/dev/sdb2         562,258,935   586,067,264    23,808,330   5 Extended
/dev/sdb5         562,258,998   586,067,264    23,808,267  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1   586,072,367   586,072,367  ee GPT

/dev/sdc1 ends after the last cylinder of /dev/sdc

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              34   586,067,264   586,067,231 Microsoft Windows

blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="D4C2166EC2165558" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="bb6216ae-8398-4fcb-8162-4ff7609c724e" TYPE="ext3" 
/dev/sdb5: UUID="c4098d45-1b7e-4c20-af72-90d7f3a38ec6" TYPE="swap" 
/dev/sdc1: UUID="49C0-B13B" TYPE="vfat" 

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
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/g/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=g)


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
# kopt=root=UUID=bb6216ae-8398-4fcb-8162-4ff7609c724e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bb6216ae-8398-4fcb-8162-4ff7609c724e

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
uuid		bb6216ae-8398-4fcb-8162-4ff7609c724e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bb6216ae-8398-4fcb-8162-4ff7609c724e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		bb6216ae-8398-4fcb-8162-4ff7609c724e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bb6216ae-8398-4fcb-8162-4ff7609c724e ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		bb6216ae-8398-4fcb-8162-4ff7609c724e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bb6216ae-8398-4fcb-8162-4ff7609c724e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		bb6216ae-8398-4fcb-8162-4ff7609c724e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bb6216ae-8398-4fcb-8162-4ff7609c724e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		bb6216ae-8398-4fcb-8162-4ff7609c724e
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
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=bb6216ae-8398-4fcb-8162-4ff7609c724e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=c4098d45-1b7e-4c20-af72-90d7f3a38ec6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  95.6GB: boot/grub/menu.lst
  95.6GB: boot/grub/stage2
  95.6GB: boot/initrd.img-2.6.27-11-generic
  95.6GB: boot/initrd.img-2.6.27-7-generic
  95.6GB: boot/vmlinuz-2.6.27-11-generic
  95.6GB: boot/vmlinuz-2.6.27-7-generic
  95.6GB: initrd.img
  95.6GB: initrd.img.old
  95.6GB: vmlinuz
  95.6GB: vmlinuz.old
=============================== StdErr Messages: ===============================

/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/`0?q*.1?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/`0?q*.1?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/42?q*.xñ?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/42?q*.xñ?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/8?q*.hb?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/8?q*.hb?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/ds?q*.¿ñ?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/ds?q*.¿ñ?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/l??q*.?¬?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/l??q*.?¬?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/îm?q*.???: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/p?q*.4"?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/p?q*.4"?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/?¬?q*.º?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/?¬?q*.º?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/??q*.°?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/??q*.°?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/ÿ^?q*.ä??: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/ÿ^?q*.ä??: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/ÿ¬?q*.ñœ?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/ÿ¬?q*.ñœ?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/?q*.$0?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/?q*.$0?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/£?q*.dr?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/£?q*.dr?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/??q*.?r?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/??q*.?r?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/°?q*.xñ?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/°?q*.xñ?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/ér?q*.?s?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/ér?q*.?s?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: sdc1/xñ?q*.?s?: binary operator expected
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
/home/g/Desktop/boot_info_script27.sh: line 1157: [: too many arguments
```

dont know what all that means...but does that help :(

---

### Post by meierfra. on 2009-03-18
> but does that help

It does. You installed grub the boot sector of the Vista partition. That makes  Vista unbootable. So you will have reinstall Grub, and fix  the boot sector of the Vista partition. I suggest to install Grub the MBR of the Ubuntu partition to keep Vista and Ubuntu independent from each other.

**Fix the Vista Boot sector**

 Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"Backup BS"
Type "Y" to confirm
  
then press "q" a few times to quit  testdisk.
 (If it does not give you  the "Backup BS"  option, it means that the original and backup boot sector are identical. Just let me know and I will tell you other methods  to fix your boot sector.) 


**Installing Grub to the MBR of the Ubuntu partition:  **


Open a terminal in ubuntu (Applications->Accessories->Terminal)

```
sudo grub 
```

and at the "grub>" prompt.


```
root (hd1,0)
setup (hd1)
quit

```


**Edit menu.lst **
(this is necessary since you will be booting from the Ubuntu Drive)


```
gksudo gedit /boot/grub/menu.lst
```


Add the following two items to menu.lst

title		Windows Vista/Longhorn (loader)  (hd1)
root		(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)   
chainloader	+1

title		Windows Vista/Longhorn (loader)  (hd2)
root		(hd2,0)
map             (hd0) (hd2)
map             (hd2) (hd0)   
chainloader	+1

Save the file and reboot.
You should boot directly into Vista.
Reboot again, and  set your bios to boot from the Ubuntu drive. You should get the Grub Menu. Try out both Vista entries. One of them should work. You can deleted the others from menu.lst.

---

### Post by hosinfefer on 2009-03-18
Worked like a charm. I had to turn off my raid in bios. That was messing me up some. Now I boot off the linux drive which has grub and I can pick which one i want to load. 

One more question on this topic. In grub I now have 3 vista..2 dont work
Can I just go into the gksudo gedit /boot/grub/menu.lst command and delete out the 2 bad vista entries??


THanks for all your help. Awsome to have dual booting working finally.

---

### Post by meierfra. on 2009-03-18
> Worked like a charm.

Great. 

> In grub I now have 3 vista..2 dont work
Can I just go into the gksudo gedit /boot/grub/menu.lst command and delete out the 2 bad vista entries??

Yup. That's exactly what you need to do.
Have fun with Ubuntu and Vista.

---

