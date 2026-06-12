---
title: "Grub loads some OSs, not all / missing partition"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by Trevski13 on 2009-01-31
so, I have an HP laptop, it came with windows vista, yay (sarcasm), eventually vista half died, though I don't think that's important to this. So the other day I descided to install Windows 7 (along side Vista), so I booted to a live CD, re-arranged the partitions (I'll post before and after later), marked Vista as hidden, then rebooted and installed 7. that all worked fine. I then marked 7's partition as hidden and installed XP, which also worked fab. (note that these were independent of eachother (as far as I know) and did not know of eachother's existance). then I installed Ubuntu 8.10, and (obviously) grub. So now we get to the problem, Ubuntu works fine, absolutely no problems there, currently XP and Vista also work flawlessly into the system (although one was mislabled), but 7 isn't listed, I tried modifying the booted partition (temp. changing "(hd0,2)" (xp) to (hd0,x) and never was able to boot to 7.... so I seem to have a missing partiton.... it's there in linux and xp, but I can't boot to it. so that's the I'll probably be asked to later but for now I won't post my whole menu.lst file, but here's a basic info:

it was partioned:
sda1 Vista         boot flag
sda2 HP_RECOVERY

under Ubuntu each is now listed as:
sda1 Vista         boot flag
sda2 extended
----sda5 Windows 7
----sda6 XP Pro
----sda7 Ubuntu
----sda8 Linux-Swap
sda3 HP_RECOVERY

and under Grub: 
vista boots at hd0,0
error 12 Invalid dev. req. at hd0,1
XP boots at hd0,2
error 22 No such partition at hd0,3
error 12 again at hd0,4~hd0,7

each of the windows boot sequences are:
root  (hd0,X)
savedefault
makeactive
chainloader +1

I hope that's enough information, but if not, I'll post what you need. Thanks in advance for your help (-_-)

---

### Post by caljohnsmith on 2009-02-01
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to booting Win 7 from Grub might be.

---

### Post by Trevski13 on 2009-02-01
all right, here it is:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b63cc28

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   363,647,339   363,647,277   7 HPFS/NTFS
/dev/sda2         363,647,340   462,896,909    99,249,570   5 Extended
/dev/sda5    *    363,647,403   404,741,609    41,094,207   7 HPFS/NTFS
/dev/sda6         404,741,673   425,320,874    20,579,202   7 HPFS/NTFS
/dev/sda7         425,320,938   454,703,759    29,382,822  83 Linux
/dev/sda8         454,703,823   462,896,909     8,193,087  82 Linux swap / Solaris
/dev/sda3         462,896,910   488,392,064    25,495,155   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e6285

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="74EA07821CC18A82" TYPE="ntfs" 
/dev/sda3: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="50B39FA07B5A9518" LABEL="Windows 7" TYPE="ntfs" 
/dev/sda6: UUID="47B429814E93846B" LABEL="XP Pro" TYPE="ntfs" 
/dev/sda7: LABEL="Ubuntu" UUID="328fd59c-7eb4-44ca-8cf5-380cade5ed88" TYPE="ext3" 
/dev/sda8: UUID="cfb29756-2403-40e9-afb9-1fb516487e83" TYPE="swap" 
/dev/sdb1: UUID="281B-7B66" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/trevor/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=trevor)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=328fd59c-7eb4-44ca-8cf5-380cade5ed88 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=328fd59c-7eb4-44ca-8cf5-380cade5ed88

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		328fd59c-7eb4-44ca-8cf5-380cade5ed88
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=328fd59c-7eb4-44ca-8cf5-380cade5ed88 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		328fd59c-7eb4-44ca-8cf5-380cade5ed88
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=328fd59c-7eb4-44ca-8cf5-380cade5ed88 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		328fd59c-7eb4-44ca-8cf5-380cade5ed88
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows XP Pro
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows 7
root		(hd0,5)
savedefault
makeactive
chainloader	+1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=328fd59c-7eb4-44ca-8cf5-380cade5ed88 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=cfb29756-2403-40e9-afb9-1fb516487e83 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location  of files loaded by Grub: ===================


 224.5GB: boot/grub/menu.lst
 224.5GB: boot/grub/stage2
 224.4GB: boot/initrd.img-2.6.27-7-generic
 224.4GB: boot/initrd.img-2.6.27-7-generic.dpkg-bak
 224.5GB: boot/initrd.img-2.6.27-7-generic.new
 224.5GB: boot/vmlinuz-2.6.27-7-generic
 224.4GB: initrd.img
 224.5GB: vmlinuz

================================ sda3/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by caljohnsmith on 2009-02-01
Part of the issue is that you have Windows 7 installed to a logical partition (sda5), and whenever you install any version of Windows to a logical partition, Windows will put its boot files in some primary NTFS/FAT partition (and if it can't, it won't let you install). But the bottom line is I would recommend following step 2 of [this tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") for how to restore your Win 7 boot files, and you can skip step 3 of that tutorial since your Windows boot sector is fine according to the script results. Also, I would recommend checking out this recent thread of someone with the exact same issue as you:

[http://ubuntuforums.org/showthread.php?p=6657699](http://ubuntuforums.org/showthread.php?p=6657699)

Good luck and let me know how it goes.

---

### Post by Trevski13 on 2009-03-10
I apologize for not responding quickly.  As of now Everything Works well (enough) I was able to add windows 7 to the boot-loader (on the vista partition (default option vista)) however, I was not satisfied with this and made another (very small) partition copied the boot loader, and then edited it to load 7 by default. so now my choice in Grub loads the OS I want, no dealing (for the most part) with multiple boot-loader menus. So thank you for your help. I just want to say that the instructions were slightly hard to understand, though I did figure it out. again, thanks, and I've actually come out of this with (I believe) a strong understanding of Booting, Partitions, the MBR, etc. :D

---

### Post by Neo_The_User on 2009-03-10
Typing this into the terminal in Ubuntu will find all OSes and add them in the boot loader automatically.

```

sudo update-grub

```

It will probe everything and search for all OSes, partitions (most likely), and kernels.

---

### Post by Trevski13 on 2009-03-10
> **Neo_The_User said:**
> Typing this into the terminal in Ubuntu will find all OSes and add them in the boot loader automatically.

```

sudo update-grub

```

It will probe everything and search for all OSes, partitions (most likely), and kernels.

...thank you *"Captain Obvious"*!  IF you had actually read the thread (and not just the title), you'd know that: 1. the problem was with the Windows boot-loader (or could have be a partition problem, though it really wasn't), not Grub (meaning updating/reinstalling grub wouldn't have fixed anything), and 2.the problem has already been resolved...

Thanks for the thought, but please read the _ENTIRE_ thread before leaving a reply. (I apologize if this comes off as being mean/cynical. I mean no insult by it, only "constructive criticism".)

---

### Post by Neo_The_User on 2009-03-10
> **Trevski13 said:**
> ...thank you *"Captain Obvious"*!  IF you had actually read the thread (and not just the title), you'd know that: 1. the problem was with the Windows boot-loader (or could have be a partition problem, though it really wasn't), not Grub (meaning updating/reinstalling grub wouldn't have fixed anything), and 2.the problem has already been resolved...

Thanks for the thought, but please read the _ENTIRE_ thread before leaving a reply. (I apologize if this comes off as being mean/cynical. I mean no insult by it, only "constructive criticism".)

I admit that I didn't read everything. Stupid of me to make such a reply. I'm sorry. You shouldn't be apologizing. My fault.

---

