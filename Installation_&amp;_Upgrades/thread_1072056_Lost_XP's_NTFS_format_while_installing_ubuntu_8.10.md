---
title: "Lost XP's NTFS format while installing ubuntu 8.10 in another partition"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by alfrz on 2009-02-17
I really need help on this one, and it seems that I have had very very bad luck with HD's lately, and this one time I cannot find where I messed up.

(1)
Here is the story, I had 4 partitions on my laptop for a while:
```

sda1: windows xp   NTFS 60GB
sda2: ubuntu 8.04  EXT3 30GB
sda3: debian       EXT3  9GB
sda4: linux-swap         1GB
(all primary partitions)

```
Naturally y had to format windows xp because it was too old and we all know what happens with windows if you play too much with it, so I decided to clear up my computer and start over again.

(2)
I backup all my data and y re-install windows, then y install ubuntu 8.04 over my debian partition and linux suse, just to check it out (didn't last long). So my computer ended like this with now trouble so far:
```

sda1: windows xp   NTFS 60GB
sda2: Suse 11.1    EXT3 30GB
sda3: Ubuntu 8.04  EXT3  9GB
sda4: linux-swap         1GB

```
(3)
Then I've got tired of suse as my "primary linux desktop" so I installed ubuntu over it, so, with no trouble so far:
```

sda1: windows xp   NTFS 60GB
sda2: Ubuntu 8.04  EXT3 30GB
sda3: Ubuntu 8.04  EXT3  9GB (to eventually re-install debian)
sda4: linux-swap         1GB

```
(4)
At this point I had very important work done in my XP partition. That exact same day I've found on my mail-box the brand new ubuntu 8.10, and I couldn't resist to install it (since my computer is almost clean) and this is where the trouble began:
```

sda1: windows xp   NTFS 60GB
sda2: Ubuntu 8.10  EXT3 30GB
sda3: Ubuntu 8.04  EXT3  9GB (to eventually re-install debian)
sda4: linux-swap         1GB

```
After installing ubuntu 8.10 I restart my pc, and I've founded that in the grub there was no "Other operting systems: Windows XP Home Edition" so y start my brand new ubuntu 8.10 to check it out.
There was nothing written on my /boot/grub/menu.list about windows so I started by adding a few lines to it:

```

title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Then y restart and try to open windows, but the grub tells me that it is not a bootable partition, so I go again back to ubuntu.
This time I tried to mount via gnome my XP's partition, and everything I found is a f****** "lost+found" directory in it! **where did my files go!?**
So I started gparted to try to figure out the problem.
It said that that specific partition was under ext3 format and that about 26.79GB were in use (that was the only thing that make sense)
So I ran the fdisk -l command and I get the next message:
```

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfce28df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7282    58492633+   7  HPFS/NTFS
/dev/sda2   *        7283       11119    30820702+  83  Linux
/dev/sda3           11120       11856     5919952+  83  Linux
/dev/sda4           11857       11978      979965   82  Linux swap / Solaris

```

I've started to lose too much hair over this one, could anyone give me a clue over this one please?????????[-o<
I have too much important data to lose on my XP partition, I don't care if I lose the os, but I must get my files back!

---

### Post by cariboo on 2009-02-17
You somehow unmarked /dev/sda1 as bootable. Boot from your LiveCD and open System-->Administration-->Partition Editor and mark /dev/sda1 as bootable, and your problem should be solved.

Jim

---

### Post by alfrz on 2009-02-17
I've tried that, and it is already marked as bootable, besides, I haven't figured out a way to recover the data, because I cannot access it in any way.

I could ask gparted to check and repair the file system, but as it identifies it as an ext3 partition, I don't know what it might do...

---

### Post by caljohnsmith on 2009-02-17
In order to troubleshoot your problem, I think it would help to get a clearer picture of your setup; how about booting your Ubuntu Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully give some clues what might have happened to your Windows installation.

---

### Post by alfrz on 2009-02-17
Too Bad!!! I was in a little bit of a hurry to recover my data, or to start over again.

I've decided to let gparted try to fix it with no success :-({|= , this is the log info I've got after doing it (if it is of any interest for anyone):
```


GParted 0.3.8

Libparted 1.8.9

Check and repair filesystem (ext3) on /dev/sda1  00:00:38    ( SUCCESS )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 116985329
size: 116985267 (55.78 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00:21    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda1
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

11 inodes used (0.00%)
0 non-contiguous inodes (0.0%)
# of inodes with ind/dind/tind blocks: 0/0/0
104971 blocks used (1.36%)
0 bad blocks
1 large file

0 regular files
2 directories
0 character device files
0 block device files
0 fifos
0 links
0 symbolic links (0 fast symbolic links)
0 sockets
--------
2 files
e2fsck 1.41.3 (12-Oct-2008)
grow filesystem to fill the partition  00:00:17    ( SUCCESS )
     	
resize2fs /dev/sda1
     	
Resizing the filesystem on /dev/sda1 to 14623158 (4k) blocks.
The filesystem on /dev/sda1 is now 14623158 blocks long.

resize2fs 1.41.3 (12-Oct-2008)

========================================

```

---

### Post by alfrz on 2009-02-17
caljohnsmith: this is what apperars in RESULTS.txt after I run the script, I hope you don't think too bad about me because the mess on my computer:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders, total 192426570 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcfce28df

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   116,985,329   116,985,267   7 HPFS/NTFS
/dev/sda2    *    116,985,330   178,626,734    61,641,405  83 Linux
/dev/sda3         178,626,735   190,466,639    11,839,905  83 Linux
/dev/sda4         190,466,640   192,426,569     1,959,930  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="fd37a737-d12b-4c6c-8258-1cfbc19640f2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="bb7fbd07-cded-4a08-9917-18c0b59607a9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="0a7c0e92-465b-43df-9f42-9b97fbac49c1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="8aa5739e-6299-44c1-8b1d-fd4e46229243" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

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


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=bb7fbd07-cded-4a08-9917-18c0b59607a9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bb7fbd07-cded-4a08-9917-18c0b59607a9

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
uuid		bb7fbd07-cded-4a08-9917-18c0b59607a9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bb7fbd07-cded-4a08-9917-18c0b59607a9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		bb7fbd07-cded-4a08-9917-18c0b59607a9
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bb7fbd07-cded-4a08-9917-18c0b59607a9 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		bb7fbd07-cded-4a08-9917-18c0b59607a9
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3554c4f6-1d8f-4a06-b9ac-b0061dd2b0bd ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
#title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda3)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3554c4f6-1d8f-4a06-b9ac-b0061dd2b0bd ro single 
#initrd		/boot/initrd.img-2.6.24-23-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
#title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (on /dev/sda3)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3554c4f6-1d8f-4a06-b9ac-b0061dd2b0bd ro quiet splash 
#initrd		/boot/initrd.img-2.6.24-19-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
#title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda3)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3554c4f6-1d8f-4a06-b9ac-b0061dd2b0bd ro single 
#initrd		/boot/initrd.img-2.6.24-19-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

#title         Windows XP Home Edition
#root          (hd0,0)
#makeactive
#chainloader   +1

title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bb7fbd07-cded-4a08-9917-18c0b59607a9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=8aa5739e-6299-44c1-8b1d-fd4e46229243 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  75.0GB: boot/grub/menu.lst
  74.9GB: boot/grub/stage2
  74.7GB: boot/initrd.img-2.6.27-11-generic
  74.5GB: boot/initrd.img-2.6.27-7-generic
  74.6GB: boot/vmlinuz-2.6.27-11-generic
  74.6GB: boot/vmlinuz-2.6.27-7-generic
  74.7GB: initrd.img
  74.5GB: initrd.img.old
  74.6GB: vmlinuz
  74.6GB: vmlinuz.old

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
# kopt=root=UUID=0a7c0e92-465b-43df-9f42-9b97fbac49c1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0a7c0e92-465b-43df-9f42-9b97fbac49c1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0a7c0e92-465b-43df-9f42-9b97fbac49c1 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bb7fbd07-cded-4a08-9917-18c0b59607a9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0a7c0e92-465b-43df-9f42-9b97fbac49c1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=8aa5739e-6299-44c1-8b1d-fd4e46229243 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  94.0GB: boot/grub/menu.lst
  94.1GB: boot/grub/stage2
  95.2GB: boot/initrd.img-2.6.24-16-generic
  93.7GB: boot/initrd.img-2.6.24-16-generic.bak
  93.8GB: boot/vmlinuz-2.6.24-16-generic
  95.2GB: initrd.img
  93.8GB: vmlinuz

```

---

### Post by caljohnsmith on 2009-02-17
Unfortunately, it looks like you completely formatted your Windows sda1 partition as ext3 somehow. If you want to try and recover files from it, probably your best bet is to use a tool like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")". You can download and run photorec in Ubuntu by doing:
```
sudo apt-get install testdisk
sudo photorec /dev/sda1
```
Also, you'll need some place to save all the recovered files to that is at least as large as your sda1 partition. Good luck and let me know how it goes.

---

### Post by alfrz on 2009-02-17
I have a problem, the file extension that I am looking for is .crd (from Corel Draw X4, I hate it by the way) That is exactly what I am trying to recover.
Is there any way to specify the format to PhotoRec so that it can find it?
Do I miss any files from my NTFS-ish disc due to the fragmentation?

---

### Post by caljohnsmith on 2009-02-18
> **alfrz said:**
> I have a problem, the file extension that I am looking for is .crd (from Corel Draw X4, I hate it by the way) That is exactly what I am trying to recover.
Is there any way to specify the format to PhotoRec so that it can find it?
Do I miss any files from my NTFS-ish disc due to the fragmentation?
To my knowledge photorec has no problem dealing with NTFS file fragmentation, so I don't think that is an issue. I don't think photorec can look specifically for .crd files though. One thing you could try is to run "file" on one of your .crd files:
```
file coreldrawfile.crd
```
If "file" is able to correctly identify the .crd file as a Corel Draw file, you could write a short bash loop so that "file" goes through all the recovered files to check which ones are Corel Draw. If you need some help with that, let me know, and also let me know the output of the "file" command on a Corel Draw file.

---

### Post by alfrz on 2009-02-18
I think that I've already done that (my way...)
```

$ls -lashR ./Data_recovery/ > files.txt

```
And under a text editor I searched for any .crd file (I've used vim). I went playing a bit with PhotoRec and it seems that it mises the directory table in the NTFS partitions and it only goes through the partition's blocks trying to find anything familiar.
Most of the recovered files where .txt incomplete files (must of them turned to be xml or html) but I couldn't find anything like the .crd file format.
How do PhotoRec works? can I specify the format to it so that it can find a different format than the ones that are already defined? 
I've found the whole list of defined file types is found in:
```

$ sudo photorec /dev/sda1
[Poceed  ]
[Intel   ]
[File Opt]

```

---

### Post by caljohnsmith on 2009-02-18
I think you might have misunderstood, because the "file" command does not care what the extension on the file you give it, "file" actually analyzes the file to try and figure out what it is. I think that's important in your case, because you can't necessarily trust the file names nor the extensions on the files photorec recovers. Also, if ".crd" is not listed under photorec's recognized file types, I don't think there is any way to add it.

---

### Post by alfrz on 2009-02-23
Sorry for keeping u waiting, but I had too much work to get done with, since I've lost most of it on my HD.

I'm so sad that I couldn't recover my .crd files, and that I had to start over with that particular project (specially because I've almost lost my job over it).

I have a little knowledge over hard drives, and I know that you can loose the reference for a particular file, but it can still be written on the HD (if nothing else overwrited it). I guessed that if I know the particular binary format of a file (not only the extention), say a .crd file, I could manage to make PhotoRec identify those kind of files other than only mp3, txt, jpg, etc. I'm sure that there is some way to do this, but right now I sincerely don't have the time to find out.

The good thing to say is that I could recover a great part of my media files (mp3), pictures (jpg), and lots of programming I've made on php, html, xml, & python (recovered as .txt and in pieces, but that's not too bad).

Thank u very much for helping me, and the key, I would say, was the great program **_PhotoRec_**.

I didn't find any relation between installing ubuntu 8.10 and losing my NTFS partition, I'm going to make some testing (with an obvious previous backup) and if I find any interesting result, I will publish it that same day.

---

