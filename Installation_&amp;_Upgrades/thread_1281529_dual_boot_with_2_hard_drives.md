---
title: "dual boot with 2 hard drives"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by ddeo on 2009-10-03
Hi all, I have been reading up on how to set up a dual boot (Windows 7 and Ubuntu) and it seems pretty straight forward, but I have not seen a solution for my exact set up.

I will be obtaining a copy of Windows 7 when it is released on the 22nd.  I have a laptop that has 2 internal hard drives.  I want to install Windows 7 on the C drive and Ubuntu on the D drive.  So I don't need to shrink any partitions because I want to dedicate this whole second drive to ubuntu.

I assume after I install windows I can then boot using the ubuntu live cd and find the second hhd and format it accordingly.

My question is what will windows think of this??  Will it have an error when booting into windows saying that the second drive is unrecognizable?

Also, I assume the second drive is a slave to the first, will this be a problem?

Please let me know if anyone out there has done this set up with 2 hard drives or knows how this might work.

Thanks in advance.  Ddeo

---

### Post by gadolinio on 2009-10-03
Hi. I dual boot with two different hard drives, with this structure:

DISK 1       1st partition       windows xp     NTFS
                2nd partition      data storage    NTFS
DISK 2       1st partition       ubuntu 8.10     ext3
                2nd partition      data storage    NTFS

In ubuntu i can see all the 4 partitions; from windows, i can only see the 3 which are formatted in NTFS. The ext3 one isn't seen from windows; partition magic does show it, but as unreadable or incorrectly formatted (anyway, this is just as a matter of interest: it doesn't cause me any trouble at all; it's as if that ext3 just didn't exist). 
When i turn the computer on, a prompt appears asking me which OS i want to start with (as default, ubuntu is automatically chosen after 10 seconds). I installed ubuntu after having windows already installed.
I can't tell you for sure, but i think i set both hard drives as master...
Hope you find this useful...

---

### Post by binary00mind on 2009-10-03
Hi ddeo, I have a laptop with 2 internal HD as well with 3 OS's Windows7 Xubuntu 9.04 and Ubuntu 9.10 and I can tell you that you will have no problems at all. 
here is my present layout: 
First HD 
/sda1 Win7
/sda5 / Xubuntu 9.04
/sda6 swap
/sda7 /home
/sda8 LVM
/sda3 NTFS storage
/sda4 NTFS storage

Second HD
/sdb1 / Ubuntu 9.10
/sdb5 /home 
/sdb6 swap 
/sdb7 LVM 
/sdb8 /var
/sdb9 NTFS storage 

Windows will totally ignore your Linux partitions, so no worry there. 

Would You reconsider and use alternate text CD installer instead of live CD? Much cleaner installation. 
Also you must decide where you will install your grub. 
You may install it on your second HD. If I were you that's what I would do. 
because if you install Windows7 after the Ubuntu and your grub is on the first HD, Windows will overwrite your grub.

---

### Post by ddeo on 2009-10-03
Hi gadolinio, thanks for your reply.  With your install did you install XP or Ubuntu first?  Also, why do you have a NTFS partition on Disk 2.  Is this storage for your ubuntu data or a second XP data storage partition?

---

### Post by ddeo on 2009-10-03
> **binary00mind said:**
> Would You reconsider and use alternate text CD installer instead of live CD? Much cleaner installation..

Hi Binary, thanks for your suggestion.  I think I will set up grub on disk 2 like you said.  What happens if I install windows 7 on disk 1 first then ubuntu on disk 2 after?

Also, don't know what the alternate text CD installer is.  can you clarify?  Thanks, ddeo

---

### Post by binary00mind on 2009-10-03
> **ddeo said:**
> Hi Binary, thanks for your suggestion.  I think I will set up grub on disk 2 like you said.  What happens if I install windows 7 on disk 1 first then ubuntu on disk 2 after?

Also, don't know what the alternate text CD installer is.  can you clarify?  Thanks, ddeoThe answer for the first question is that nothing bad will happen. Actually it is a good idea. When You will be installing Ubuntu, the installer will ask you where you want to install grub. you will type this: /dev/sdb 
then you should change the boot priority in the BIOS and put the second Hard Drive as a first choice. You may then boot to Ubuntu and Win7 from the same interface. 
Note, in the menu you will see Vista loader not Win7 loader, just ignore this and click on Vista and your Win7 will boot up. 

As for the second question what alternate text CD is? 
One can compare to DOS or Windows installation style and it is a breeze.  
Thought it is a different ISO image. 
You must download the alternate text image ISO and burn it first. I wish I knew where You live, I would give you link for the mirror.

---

### Post by binary00mind on 2009-10-03
I was trying to edit my own post but to no avail....

Hi ddeo...here is the main page with the list of mirrors. 
You can choose your download between ftp, torrent and/or http
here is the link:  [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by raymondh on 2009-10-03
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

Have fun :)

Regards,

---

### Post by binary00mind on 2009-10-04
That was very nice detailed page about the installation and dual boot. 
 
But despite the fact, that almost all of my computers are basically new 
I will choose alternate text installer any day, as long they are available and especially with dual boot and/or multiple Hard Disks. 
  
Here is the difference between the Live CD, Alternate text CD & Server CD...
[[COLOR="Blue"]here are the basics[/COLOR]](http://samiux.wordpress.com/2009/03/19/the-different-between-ubuntu-desktop-alternate-cd-and-server-cd/) 

How Alternate text CD installation interface looks like? 
This example is from the old Ubuntu 6.10 realese but not much has changed since then 
[[COLOR="Blue"]here is how to go about it[/COLOR]](http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html)

---

### Post by gadolinio on 2009-10-04
> **ddeo said:**
> Hi gadolinio, thanks for your reply.  With your install did you install XP or Ubuntu first?  Also, why do you have a NTFS partition on Disk 2.  Is this storage for your ubuntu data or a second XP data storage partition?

I bought the computer with XP installed; that was the offer :P   Then i bought another hard disk, and installed Ubuntu there. 
The reason for me to have both storage partitions in NTFS is that XP can use them. (Although i think i've heard of some program/patch/something to make windows read and write ext3, but it wasn't even worth invesitgating as i seldom use windows). So i chose NTFS which can be immediately used by both OS (ubuntu does it by using ntfs-3g driver, which is included in the liveCD).

I didn't have to configure anything to bual boot. After having installed ubuntu, i found that when booting the prompt asked me which OS i wanted to use. Then i found a program to configure that function with a graphic interface: the package is startupmanager (i think it was in synaptic). Anyway, everything works perfectly without modifications.

---

### Post by raymondh on 2009-10-05
> **gadolinio said:**
> I bought the computer with XP installed; that was the offer :P   Then i bought another hard disk, and installed Ubuntu there. 
The reason for me to have both storage partitions in NTFS is that XP can use them. (Although i think i've heard of some program/patch/something to make windows read and write ext3, but it wasn't even worth invesitgating as i seldom use windows). So i chose NTFS which can be immediately used by both OS (ubuntu does it by using ntfs-3g driver, which is included in the liveCD).

I didn't have to configure anything to bual boot. After having installed ubuntu, i found that when booting the prompt asked me which OS i wanted to use. Then i found a program to configure that function with a graphic interface: the package is startupmanager (i think it was in synaptic). Anyway, everything works perfectly without modifications.

If you want to "investigate" windows reading ext2/ext3:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

StartupManager (SUM) is a nice tool to have.  It also writes to the menu.lst.  

Happy Ubuntu-ing :)

---

### Post by ddeo on 2009-10-06
> **binary00mind said:**
> The answer for the first question is that nothing bad will happen. Actually it is a good idea. When You will be installing Ubuntu, the installer will ask you where you want to install grub. you will type this: /dev/sdb 
then you should change the boot priority in the BIOS and put the second Hard Drive as a first choice. You may then boot to Ubuntu and Win7 from the same interface. 
Note, in the menu you will see Vista loader not Win7 loader, just ignore this and click on Vista and your Win7 will boot up. 

As for the second question what alternate text CD is? 
One can compare to DOS or Windows installation style and it is a breeze.  
Thought it is a different ISO image. 
You must download the alternate text image ISO and burn it first. I wish I knew where You live, I would give you link for the mirror.

Hi binary00mind, thanks for your response.  It took me a while to get back because my cd drive is not working correctly and it tokk me some time to figure out to make a bootable USB.

In any case I just installed ubuntu on my second internal hdd.  This is what I did.  I downloaded the ubuntu 9.04 iso and created a bootable usb drive using unetbootin.  It worked perfectly.  When installing ubuntu I selected my second hdd from the drop down menu.  The interface was pretty slick.  It could see vista was installed on my 1st hdd and it gave me the option to install ubuntu along side with vista on the 1st hdd.  I chose to install it on the second and I used the default setting for partitioning.

It did fine with the install and I rebooted.  Unfortunately, the bios did not ask me which operating system to boot to.  I saw you message about changing the boot order of the 2 hdd but in my bios boot order there is only one hdd listed.

Do you know how to change it so that it asks upon start up which os??  Please advise.

After booting into Vista, it is exactly as you said, Windows no longer sees the 2nd hdd.

Thanks for any help.  Ddeo

---

### Post by ddeo on 2009-10-06
> **raymondhenson said:**
> [http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

Have fun :)

Regards,

Crazy...  looks like I have a lot of reading to do.  Do you know if my situation (please read my last post) is easily fixable or will I have to start over??

Thanks, Ddeo

---

### Post by raymondh on 2009-10-06
> **ddeo said:**
> Crazy...  looks like I have a lot of reading to do.  Do you know if my situation (please read my last post) is easily fixable or will I have to start over??

Thanks, Ddeo

Hi Ddeo,

Re-reading your last post .... there may be various reasons why your system/BIOS cannot detect your 2nd HD.  Some "off-my-head" tips:

1.  make sure your jumper settings (or sata connections) are correct and plugged in properly ... 'specially in a master-slave set-up.
2.  try setting the detection mode (in CMOS) to AUTO

Herman has a [BIOS page]("http://members.iinet.net.au/~herman546/p1.html#The_easiest_way_to_get_into_the_BIOS") as well.

[http://www.brunolinux.com/01-First_Things_To_Know/Change_BIOS_Settings.html](http://www.brunolinux.com/01-First_Things_To_Know/Change_BIOS_Settings.html)

My .02-cent thought ->  I like the idea of having GRUB installed on a separate HD.  That to me is an added security measure (i.e. no one touches ubuntu unless the operator knows to change the boot priority order in BIOS).  However, if the BIOS setting is something that cannot be changed ... you can *consider* re-installing GRUB in the MBR of the 1st (and readable) HD.  This, however, means that GRUB is now your bootloader for both OS'.  Let us know what you decide and we can go from there.

Regards,

---

### Post by ddeo on 2009-10-07
> **raymondhenson said:**
> Hi Ddeo,

Re-reading your last post .... there may be various reasons why your system/BIOS cannot detect your 2nd HD.  Some "off-my-head" tips:

1.  make sure your jumper settings (or sata connections) are correct and plugged in properly ... 'specially in a master-slave set-up.
2.  try setting the detection mode (in CMOS) to AUTO

Herman has a [BIOS page]("http://members.iinet.net.au/~herman546/p1.html#The_easiest_way_to_get_into_the_BIOS") as well.

[http://www.brunolinux.com/01-First_Things_To_Know/Change_BIOS_Settings.html](http://www.brunolinux.com/01-First_Things_To_Know/Change_BIOS_Settings.html)

My .02-cent thought ->  I like the idea of having GRUB installed on a separate HD.  That to me is an added security measure (i.e. no one touches ubuntu unless the operator knows to change the boot priority order in BIOS).  However, if the BIOS setting is something that cannot be changed ... you can *consider* re-installing GRUB in the MBR of the 1st (and readable) HD.  This, however, means that GRUB is now your bootloader for both OS'.  Let us know what you decide and we can go from there.

Regards,

Hi Raymond, thanks for your response.  I do wish to have ubuntu installed only on my 2nd hdd and windows on my first.  I don't know if grub is even installed on my second hdd because I just selected the defaults.  I am installing on a laptop that has 2 factory installed hdds.  I have never opened it up and don't kow what the jumpers are set at.  What should it be to make it work?  Both set to master?

Also, I already checked my bios and there is no setting for the second hdd in the boot order.  Sorry for my noob question but what is the difference between the bios and cmos?

Thanks, Dan

---

### Post by ddeo on 2009-10-07
> **binary00mind said:**
> I was trying to edit my own post but to no avail....

Hi ddeo...here is the main page with the list of mirrors. 
You can choose your download between ftp, torrent and/or http
here is the link:  [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Hi Binary, I am downloading the alternate text version now.  Maybe I will try reinstalling this way to see if there are more options that will fix my situation....  not sure...

Please let me know if you have any ideas as to why I cannot boot to ubuntu currently.  Thanks, Ddeo

---

### Post by presence1960 on 2009-10-07
why don't you do this so we can see exactly what your setup & boot process look like:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

We can go round & round much longer guessing at your setup & the solution or we can see exactly what you have and come up with a solution for your specific set up.

---

### Post by raymondh on 2009-10-07
Hi Ddeo,

I agree with presence1960.  Let's take a look at your bootinfoscript results first.  

I may have been too focused on the "cannot detect 2nd HD" issue .... the solution may be simpler and "right there".

Regards,

---

### Post by ddeo on 2009-10-07
> **presence1960 said:**
> why don't you do this so we can see exactly what your setup & boot process look like:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

We can go round & round much longer guessing at your setup & the solution or we can see exactly what you have and come up with a solution for your specific set up.

Hi Presence, thanks for your help.  Here is the contents of the file...

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3475f459

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    15,589,375    15,587,328  27 Hidden HPFS/NTFS
/dev/sda2    *     15,589,376   234,439,599   218,850,224   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe00fec31

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   224,829,674   224,829,612  83 Linux
/dev/sdb2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sdb5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     4,030,463     4,030,432   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="A4B6740FB673DFEA" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="C61E76311E761B1F" TYPE="ntfs" 
/dev/sdb1: UUID="dbdd9425-189f-41d0-9fd3-6c7b14cf6ea9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="799c6449-c18b-41f1-9029-43f2787b539c" TYPE="swap" 
/dev/sdc1: LABEL="USB20FD" UUID="2AEC-236C" TYPE="vfat" 

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
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
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
# kopt=root=UUID=dbdd9425-189f-41d0-9fd3-6c7b14cf6ea9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dbdd9425-189f-41d0-9fd3-6c7b14cf6ea9

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		dbdd9425-189f-41d0-9fd3-6c7b14cf6ea9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dbdd9425-189f-41d0-9fd3-6c7b14cf6ea9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		dbdd9425-189f-41d0-9fd3-6c7b14cf6ea9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dbdd9425-189f-41d0-9fd3-6c7b14cf6ea9 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		dbdd9425-189f-41d0-9fd3-6c7b14cf6ea9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
chainloader	+1


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
UUID=dbdd9425-189f-41d0-9fd3-6c7b14cf6ea9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=799c6449-c18b-41f1-9029-43f2787b539c none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  59.5GB: boot/grub/menu.lst
  59.5GB: boot/grub/stage2
  59.5GB: boot/initrd.img-2.6.28-11-generic
  59.5GB: boot/vmlinuz-2.6.28-11-generic
  59.5GB: initrd.img
  59.5GB: vmlinuz

```

---

### Post by presence1960 on 2009-10-07
Everything looks good, except for 1 thing. Reboot and go into BIOS. Set sdb as first in the hard disk boot order. Save changes to CMOS and exit. When you boot GRUB should come up. Boot into Ubuntu and when the desktop loads open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

Scroll down to the bottom to your windows entries and change them to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Recovery
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd1,1)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1


```

Ubuntu is installed on 2nd hard disk as well as GRUB on MBR of second hard disk. You need to make the second hard disk boot before the first in BIOS hard disk boot order. This will bring up GRUB. Then once you edit the windows entries in menu.lst from Ubuntu you will also be able to boot windows from GRUB.

---

### Post by ddeo on 2009-10-07
Hi Presence, thanks for culling through this file to determine the issue for me...

With that said, I already tried to change the boot order in my BIOS and unfortunately, there is only one hdd in the boot order list.  Do you know why this is?

Please advise.  Thanks, Dan

---

### Post by presence1960 on 2009-10-07
> **ddeo said:**
> Hi Presence, thanks for culling through this file to determine the issue for me...

With that said, I already tried to change the boot order in my BIOS and unfortunately, there is only one hdd in the boot order list.  Do you know why this is?

Please advise.  Thanks, Dan

well your dual boot is set up properly. I would tend to think it is a BIOS issue. I would refer to your motherboard documentation to find an answer or possibly see if there is a BIOS update.

It is definitely your BIOS or maybe even a jumper setting if you have IDE drives.

---

### Post by ddeo on 2009-10-07
Hmmmmmm...

Well I just checked and there is no update to my Bios and I have 2 internal SATA hdd.  Does this mean there are no jumper settings?  How is Master/Slave scenario set up?

Any other ideas??

Thanks, Ddeo

---

### Post by presence1960 on 2009-10-07
> **ddeo said:**
> Hmmmmmm...

Well I just checked and there is no update to my Bios and I have 2 internal SATA hdd.  Does this mean there are no jumper settings?  How is Master/Slave scenario set up?

Any other ideas??

Thanks, Ddeo

There are no master/slave settings with SATA. I would think if your 2nd hard disk is not showing in BIOS maybe the SATA port or controller is bad. Try switching the second hard disk to another SATA port and then see if it is recognized in BIOS.

---

### Post by raymondh on 2009-10-07
what is sdc?  Is it an external?  If so, can you disconect (safely eject) sdc ... shut down ... reboot ... access BIOS and see if the 2nd HD is listed?

Also, share with us your BIOS make.

Regards,

---

### Post by ddeo on 2009-10-08
> **raymondhenson said:**
> what is sdc?  Is it an external?  If so, can you disconect (safely eject) sdc ... shut down ... reboot ... access BIOS and see if the 2nd HD is listed?

Also, share with us your BIOS make.

Regards,

Hi Raymond, my laptop has 2 internal hdds factory installed.  I have never opened the laptop and I would like to avoid that if possible.  I am not sure what you mean by sdc?

I have a phoenix trustedcore setup utility for my bios in my Vaio.  Sony does not have any updates to the bios.  i went to the pheonix website and downloaded a scanner and ran it.  It said that there is an update for it but I would have to pay $30 for a subscription.  I have never heard of charging for a bios update.  Not cool!  I am not going to pay especially since I don't even know if it will fix the problem..

Any ideas?  Thanks, Ddeo

---

### Post by presence1960 on 2009-10-08
> **ddeo said:**
> Hi Raymond, my laptop has 2 internal hdds factory installed.  I have never opened the laptop and I would like to avoid that if possible.  I am not sure what you mean by sdc?

I have a phoenix trustedcore setup utility for my bios in my Vaio.  Sony does not have any updates to the bios.  i went to the pheonix website and downloaded a scanner and ran it.  It said that there is an update for it but I would have to pay $30 for a subscription.  I have never heard of charging for a bios update.  Not cool!  I am not going to pay especially since I don't even know if it will fix the problem..

Any ideas?  Thanks, Ddeo

sdc looks like a flash drive, possibly Ubuntu Live Cd on USB. It has syslinux on MBR. Is that correct that it is a flash drive?

---

### Post by ddeo on 2009-10-08
> **presence1960 said:**
> sdc looks like a flash drive, possibly Ubuntu Live Cd on USB. It has syslinux on MBR. Is that correct that it is a flash drive?

I installed ubuntu from a USB drive.  It was live CD iso on the usb drive created by unetbootin 3rd party software.

I was booted on the usb drive when I ran the script from Presence that supplied the boot info I pasted in the previous message.

I have been reading about phoenix trustedcore setup utility and it sounds like it is a very limited bios.  Another reason I hate this laptop.

Reasons:
1) Sony crap software
2) Vista (sorry excuse for an operating system)
3) Limited bios

---

### Post by raymondh on 2009-10-08
> **ddeo said:**
> I installed ubuntu from a USB drive.  It was live CD iso on the usb drive created by unetbootin 3rd party software.

I was booted on the usb drive when I ran the script from Presence that supplied the boot info I pasted in the previous message.

I have been reading about phoenix trustedcore setup utility and it sounds like it is a very limited bios.  Another reason I hate this laptop.

Reasons:
1) Sony crap software
2) Vista (sorry excuse for an operating system)
3) Limited bios

Have you tried safely ejecting the USB and then rebooting .... pausing the start-up (POST) and then checking if the 2nd HD is now recognized?

Sony ...... that brand is very "prohibited" (my opinion).  Ok, when you go through BIOS ..... enter CMOS and then see if "detection" is set to AUTO.  Then try reboot again.

Another option for you (as mentioned earlier) is to re-install GRUB in the MBR of the 1st HD ... in sda.  This means that GRUB will now be the master bootloader for both.  When you choose windows, it will then segue to the windows loader.  Personally, I prefer GRUB as my bootloader.  Your choice.

Regards,

---

### Post by ddeo on 2009-10-08
> **raymondhenson said:**
> Have you tried safely ejecting the USB and then rebooting .... pausing the start-up (POST) and then checking if the 2nd HD is now recognized?

Sony ...... that brand is very "prohibited" (my opinion).  Ok, when you go through BIOS ..... enter CMOS and then see if "detection" is set to AUTO.  Then try reboot again.

Another option for you (as mentioned earlier) is to re-install GRUB in the MBR of the 1st HD ... in sda.  This means that GRUB will now be the master bootloader for both.  When you choose windows, it will then segue to the windows loader.  Personally, I prefer GRUB as my bootloader.  Your choice.

Regards,

Hi raymond, I don't think this bios even give me the option to choose detection to auto.  But, I will check again.

I think your last point is my only option.  I wanted to keep Grub isolated to the second hhd to keep it inipendent.  When I upgrade to Windows 7 the installer will overwrite grub, correct?

Is there an easy way to move grub over to the 1st hdd?

Thanks, Ddeo

---

### Post by raymondh on 2009-10-08
> **ddeo said:**
> Hi raymond, I don't think this bios even give me the option to choose detection to auto.  But, I will check again.

I think your last point is my only option.  I wanted to keep Grub isolated to the second hhd to keep it inipendent.  When I upgrade to Windows 7 the installer will overwrite grub, correct?

Is there an easy way to move grub over to the 1st hdd?

Thanks, Ddeo

When you upgrade to win7, yes it will overwrite again.  However, the flexibility of linux allows you to re-install GRUB again hence overwriting windows once more ;)

Before you reinstall GRUB, do you have a Vista install disc (not the recovery disc supplied by sony)?  If not, download and burn this to a CD first.  It's a good tool to have:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

You could also download and burn hiren's CD (see my signature)

I suggest these (above) just in case something borks and we need a command prompt to fix the MBR of windows to give you at least a working OS.

[URL="http://ubuntuforums.org/showthread.php?t=224351"]
How to reinstall GRUB[/URL].  The reinstall process will put GRUB in the MBR of the first HD to boot.  This happens to be sda right now.

Back-up your files first.  Safe ubuntu-ing to you Ddeo.

Regards,

---

### Post by ddeo on 2009-10-08
> **raymondhenson said:**
> When you upgrade to win7, yes it will overwrite again.  However, the flexibility of linux allows you to re-install GRUB again hence overwriting windows once more ;)

Before you reinstall GRUB, do you have a Vista install disc (not the recovery disc supplied by sony)?  If not, download and burn this to a CD first.  It's a good tool to have:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

You could also download and burn hiren's CD (see my signature)

I suggest these (above) just in case something borks and we need a command prompt to fix the MBR of windows to give you at least a working OS.

[URL="http://ubuntuforums.org/showthread.php?t=224351"]
How to reinstall GRUB[/URL].  The reinstall process will put GRUB in the MBR of the first HD to boot.  This happens to be sda right now.

Back-up your files first.  Safe ubuntu-ing to you Ddeo.

Regards,

Hi Raymond, thanks for your help.  I do have the vista cds but Once I get Windows 7 I am wiping the 1st HDD clean anyway.  So I am already all backed up...

I will try the method from the other link.  What happens to my grub install that is on the 2nd hdd?  Will that cause any conflicts?  Should I try to remove it?

Thanks for your help.  Ddeo

---

### Post by raymondh on 2009-10-08
Re : GRUB previously installed:

I see no problems/conflicts.  

We are installing GRUB in the 1st HD as we are having issues with your system recognizing the 2nd HD. GRUB will now be the bootloader to access both OS'.  When we get to solve the "cannot detect" issue, you can change the boot order and still boot into Ubuntu without nee ding to go thru the 1st HD.  By then, we will have to edit the menu.lst to add windows and make windows think that it is first on drive as well as first to boot.

Wait a while for another poster to make a second opinion on this matter.  You can also ask/PM presence1960 (a friend I consider 'GURU' on these matters) about this plan and see what he thinks. 

While waiting (and if you can spare a CD), suggest you burn a copy of hiren's cd.  It's a great tool to have in your toolbox.

Safe ubuntu-ing Ddeo.

---

### Post by presence1960 on 2009-10-09
I think setting GRUB up on sda is good idea. My only concern is that when GRUB on sda takes over on boot it still must point to menu.lst on sdb. I am concerned that with BIOS not recognizing sdb that it will fail because the sdb disk is not recognized. But it can't hurt to try.

If all else fails I would try installing Ubuntu on sda with windows.

---

### Post by ddeo on 2009-10-10
> **presence1960 said:**
> I think setting GRUB up on sda is good idea. My only concern is that when GRUB on sda takes over on boot it still must point to menu.lst on sdb. I am concerned that with BIOS not recognizing sdb that it will fail because the sdb disk is not recognized. But it can't hurt to try.

If all else fails I would try installing Ubuntu on sda with windows.

Hi Presence, do you think I need to edit the menu.lst file after installing grub on sd0?  I have not tried it yet.

I am still perplexed about why my bios does not have the 2nd hard drive in the boot list.  It does not say hard drive 1 either, it simply says "Internal Hard Drive".  Could you explain how Master/Slave scenarios work with SATA hard drives because I have been reading other posts on these forums where users are referring to Master and Slave SATA drives.  The reason I am belaboring this point is because I don't think there are any hardware problems with my laptop. I think that it the 2nd hdd could be a slave (this may be completely wrong) or my bios is a barebones program that is not giving me all of the options including choosing a specific internal hdd in the boot order.

Do my theories make any sense?

---

### Post by ddeo on 2009-10-10
I am starting to think my bios is the problem.  I have been reading up and finding more info about how Phoenix TrustedCore has too much control over your pc.  Check out these:

[http://www.thefreelibrary.com/Phoenix+Technologies+Announces+BIOS+Replacement+Product+That+Supports+...-a0135433803](http://www.thefreelibrary.com/Phoenix+Technologies+Announces+BIOS+Replacement+Product+That+Supports+...-a0135433803)

[http://www.phoenix.com/en/OEM-ODM/products/browse+by+products/trustedcore/default.htm](http://www.phoenix.com/en/OEM-ODM/products/browse+by+products/trustedcore/default.htm)

---

### Post by presence1960 on 2009-10-10
> **ddeo said:**
> Hi Presence, do you think I need to edit the menu.lst file after installing grub on sd0?  I have not tried it yet.

I am still perplexed about why my bios does not have the 2nd hard drive in the boot list.  It does not say hard drive 1 either, it simply says "Internal Hard Drive".  Could you explain how Master/Slave scenarios work with SATA hard drives because I have been reading other posts on these forums where users are referring to Master and Slave SATA drives.  The reason I am belaboring this point is because I don't think there are any hardware problems with my laptop. I think that it the 2nd hdd could be a slave (this may be completely wrong) or my bios is a barebones program that is not giving me all of the options including choosing a specific internal hdd in the boot order.

Do my theories make any sense?

As far as I know there are no master/slave settings for SATA hard disks. The BIOS controls which disks boot in which order. There are no master/slave cables either for SATA. You plug each device into a SATA port on the mobo and then BIOS controls the order in which they boot. So if you have 3 SATA drives and the BIOS is set to boot sdc, sda then sdb that means sdc is the "master" and the other two are the "slaves".

---

### Post by raymondh on 2009-10-10
Just curious ....

boot into windows and thru 'device manager' ... see if the 2nd HD is listed.

I also do not think there is a master-slave for SATA.

---

### Post by ddeo on 2009-10-16
> **raymondhenson said:**
> When you upgrade to win7, yes it will overwrite again.  However, the flexibility of linux allows you to re-install GRUB again hence overwriting windows once more ;)

Before you reinstall GRUB, do you have a Vista install disc (not the recovery disc supplied by sony)?  If not, download and burn this to a CD first.  It's a good tool to have:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

You could also download and burn hiren's CD (see my signature)

I suggest these (above) just in case something borks and we need a command prompt to fix the MBR of windows to give you at least a working OS.

[URL="http://ubuntuforums.org/showthread.php?t=224351"]
How to reinstall GRUB[/URL].  The reinstall process will put GRUB in the MBR of the first HD to boot.  This happens to be sda right now.

Back-up your files first.  Safe ubuntu-ing to you Ddeo.

Regards,

Hi Raymond and Presence, I have been out of town and not able to focus on this until today.  I reinstalled grub on (sd0) by following the tutorial you sent me and it worked perfectly.  Thanks for all of you help.

The only weird thing is on boot (and this happens when I boot via the USB drive too) I see and error like this:

```
[.....1.349422] ACPI: Invalid _TSD Data
```

Is this anything I should be concerned about?  Thanks, Ddeo

---

### Post by raymondh on 2009-10-16
> **ddeo said:**
> Hi Raymond and Presence, I have been out of town and not able to focus on this until today.  I reinstalled grub on (sd0) by following the tutorial you sent me and it worked perfectly.  Thanks for all of you help.

The only weird thing is on boot (and this happens when I boot via the USB drive too) I see and error like this:

```
[.....1.349422] ACPI: Invalid _TSD Data
```

Is this anything I should be concerned about?  Thanks, Ddeo

Let me research ..... off-head, I think it'll involve acpi=off (maybe) in the grub/menu.lst.  Am not sure though, let me research and will post back findings.

Otherwise, are you booting ok into ubuntu and windows?

---

### Post by presence1960 on 2009-10-16
> **ddeo said:**
> Hi Raymond and Presence, I have been out of town and not able to focus on this until today.  I reinstalled grub on (sd0) by following the tutorial you sent me and it worked perfectly.  Thanks for all of you help.

The only weird thing is on boot (and this happens when I boot via the USB drive too) I see and error like this:

```
[.....1.349422] ACPI: Invalid _TSD Data
```

Is this anything I should be concerned about?  Thanks, Ddeo

I agree with Raymond. Glad you finally got it working. To be honest I don't like that BIOS you have very much.

---

### Post by Bucky Ball on 2009-10-16
. In error.

---

### Post by ddeo on 2009-10-17
> **presence1960 said:**
> I agree with Raymond. Glad you finally got it working. To be honest I don't like that BIOS you have very much.

Yes, I don't like this bios either.  I have never liked this overpriced viao either...  but now I finally feel "free" of vista at least....

---

### Post by ddeo on 2009-10-17
> **raymondhenson said:**
> Let me research ..... off-head, I think it'll involve acpi=off (maybe) in the grub/menu.lst.  Am not sure though, let me research and will post back findings.

Otherwise, are you booting ok into ubuntu and windows?

From my quick searching it seems to be related to power management.  I have not had any problems because of it as far as I can tell...  other then the nag...

BTW, my grub menu shows 2 versions of ubuntu for some reason.

---

### Post by raymondh on 2009-10-17
> **ddeo said:**
> From my quick searching it seems to be related to power management.  I have not had any problems because of it as far as I can tell...  other then the nag...

BTW, my grub menu shows 2 versions of ubuntu for some reason.

2 different kernels?  That's ok because should one bork, you can still access the other.

Are you referring to "generic" and "recovery"?  Keep that, as well as memtest, etc.

Or, are you referring to "2 PAIRS" of the same kernel? If so, post back so we can start editing your grub/boot/menu.lst.

If you access synaptic (system > administration), there's a nifty program called STARTUPMANGER. It is GUI-based.  With it, you can set GRUB defaults and parameters to your liking.  It also writes to the menu.lst.  I suggest you keep 2 kernels.

Regards,

---

### Post by Bucky Ball on 2009-10-17
> **ddeo said:**
> BTW, my grub menu shows 2 versions of ubuntu for some reason.

That is normal. You have the current kernel and a recovery kernel of it and also the previous working kernel and a recovery of that. If an update to the current kernel kills anything, you can boot into the previous and hopefully recover.

It is a safety thing but you can hide the previous kernel from the menu if you want.

---

### Post by ddeo on 2009-12-05
Hi All, I have not posted to this thread for a while but I hope it is ok to do so since my question is still pertaining to this same dual boot computer with 2 hard drives.

I currently have the following configuration:
sda1 has windows 7 installed and grub 1 installed.
sdb1 has ubuntu 9.8 installed

I would like to do a clean install of ubuntu 9.10 on sdb1 to replace 9.8 and I don't know how grub will be affected.  for one is it is on another hard drive so I assume it won't be configured to work with the new 9.10 install.  Is there a way I can tweak it?

second question is doesn't 9.10 use grub 2?  Will this need to be installed onto sda1?  Do I follow the same procedure as last time for this?

The 3rd question is that my grub lists windows vista not windows 7.  Can this be edited to read the proper os?

Thanks for your help.  Regards, Ddeo

---

### Post by oldfred on 2009-12-05
Did you ever figure out how to change drive order in BIOS? There should be two settings. One is what device to boot from HD, CD, FD, USB or anything else. The other setting is which harddrive to use. Thisis a little more important for Grub2 as it currently has a minor bug that makes for a 20-45 sec delay if grub2 is one one drive and Ubuntu is on another drive. You will want to switch drive order in BIOS so the Ubuntu drive boots first and then install Karmic Koala 9.10.

If still in old grub you can edit menu.lst to change the name. Grub2 will find your windows install and may have to correct name. It does not use menu.lst and is a little more difficult to customize but finds other systems better.

---

### Post by ddeo on 2009-12-05
> **oldfred said:**
> Did you ever figure out how to change drive order in BIOS? There should be two settings. One is what device to boot from HD, CD, FD, USB or anything else. The other setting is which harddrive to use. Thisis a little more important for Grub2 as it currently has a minor bug that makes for a 20-45 sec delay if grub2 is one one drive and Ubuntu is on another drive. You will want to switch drive order in BIOS so the Ubuntu drive boots first and then install Karmic Koala 9.10.

If still in old grub you can edit menu.lst to change the name. Grub2 will find your windows install and may have to correct name. It does not use menu.lst and is a little more difficult to customize but finds other systems better.

Hi Oldfred, My bios is very limited and I cannot change the boot order of the hard drives.  Based on your comment does it make sense to use grub 1 instead of grub 2?  Maybe i should just upgrade my 9.8 instead of doing a clean install.  This way it will preserve grub 1 correct?

---

### Post by oldfred on 2009-12-05
I have done updates for 3 years and had minor issues just about every time. Since I had accumulated lots of cruft I elected to do a clean install. The main differences are grub vs. grub2 and ext3 vs ext4. Both grub2 and ext4 will be the future but you do not have to be on the bleeding edge. Upgrade will work just fine and if later you want to do a clean install you can. Just in all cases back up any important data before any major system change.

---

### Post by ddeo on 2009-12-05
OK.  I will try the upgrade it is just going to take for ever to download....  I have already downloaded the iso...

Thanks, I will do some searching to find a tutorial about how to edit the menu.lst

Thanks, Ddeo

---

### Post by oldfred on 2009-12-05
Grub legacy info
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
Examples of menu.lst for alt oper sys
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Herman's page
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

After you have read some of the above:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

---

### Post by Bucky Ball on 2009-12-05
Upgrades generally do take ages. Clean install is my choice. The new grub should replace the old. You can set ext3 instead of 4 doing a manual partitioning during install if you want but 9.10 will still read your existing ext3 partitions so not really an issue.

---

### Post by hilmanzaky on 2009-12-06
Hi all,

Actually I have a problem with my boot loader.. I already installed 2 OS (Ubuntu and XP).. I had no problem when I choose to boot Ubuntu, but I had a problem with a blank DOS when I try to boot XP, just like the system doesn't found the XP hard drive or the XP partition.. (maybe). The only solution I have to access XP now is change the "hard drive boot priority" on my BIOS..

I installed Ubuntu on my SATA hard drive and XP on my ATA hard drive..

Now I want to experimenting to change the hd(?,?) --> ("actually I don't know what the name of this model").. but I didn't know what is the "hd(?,?)" number for my ATA drive and how to view it..

The questions is:

[LIST=1]
[*]Am I right if I assume that the "root" on "menu.lst" has a wrong address on my XP drive? if "yes" then how to find the "hd(?, ?)" on my ATA drive?
[*]Or if "false" then can anyone help me?
[/LIST]
The truth is :

[LIST=1]
[*]I'm a beginner
[*]Sorry for my bad at English speaking
[/LIST]

---

### Post by presence1960 on 2009-12-06
> **hilmanzaky said:**
> Hi all,

Actually I have a problem with my boot loader.. I already installed 2 OS (Ubuntu and XP).. I had no problem when I choose to boot Ubuntu, but I had a problem with a blank DOS when I try to boot XP, just like the system doesn't found the XP hard drive or the XP partition.. (maybe). The only solution I have to access XP now is change the "hard drive boot priority" on my BIOS..

I installed Ubuntu on my SATA hard drive and XP on my ATA hard drive..

Now I want to experimenting to change the hd(?,?) --> ("actually I don't know what the name of this model").. but I didn't know what is the "hd(?,?)" number for my ATA drive and how to view it..

The questions is:

[LIST=1]
[*]Am I right if I assume that the "root" on "menu.lst" has a wrong address on my XP drive? if "yes" then how to find the "hd(?, ?)" on my ATA drive?
[*]Or if "false" then can anyone help me?
[/LIST]
The truth is :

[LIST=1]
[*]I'm a beginner
[*]Sorry for my bad at English speaking
[/LIST]
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by hilmanzaky on 2009-12-06
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

ok.. after ```
sudo bash ~/Desktop/boot_info_script*.sh
``` I get this "/home/hilman/Desktop/boot_info_script*.sh: No such file or directory", is there anything wrong?

---

### Post by darkod on 2009-12-06
It's not on desktop. It's probably in Downloads. Either move the downloaded script to desktop and run the same command, or change Desktop in the command to Downloads. Then the results.txt file will be there too.

---

### Post by hilmanzaky on 2009-12-06
> **darkod said:**
> It's not on desktop. It's probably in Downloads. Either move the downloaded script to desktop and run the same command, or change Desktop in the command to Downloads. Then the results.txt file will be there too.

Oh sorry I forgot it..

here is the result :
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfbfcfbfc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,448,624    61,448,562   7 HPFS/NTFS
/dev/sda2          61,448,625    78,236,549    16,787,925   5 Extended
/dev/sda5          61,448,688    70,428,959     8,980,272  82 Linux swap / Solaris
/dev/sda6          70,429,023    78,236,549     7,807,527  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc14c6518

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   261,200,834   261,184,770   f W95 Ext d (LBA)
/dev/sdb5              16,128   261,200,834   261,184,707   b W95 FAT32
/dev/sdb2    *    261,200,835   312,576,704    51,375,870  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4600B62C00B6233B" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="3d7fb23d-bebb-492d-a82a-26992b0a0305" 
/dev/sda6: UUID="ae01f260-91a6-4bac-afa3-73f5ff896e37" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="ec543db8-283b-481e-830f-32e8e884c7b3" TYPE="ext3" 
/dev/sdb5: LABEL="BLACKSTAR" UUID="46F0-3F85" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb5 on /media/BLACKSTAR type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
gvfs-fuse-daemon on /home/hilman/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hilman)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=ec543db8-283b-481e-830f-32e8e884c7b3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ec543db8-283b-481e-830f-32e8e884c7b3

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
uuid        ec543db8-283b-481e-830f-32e8e884c7b3
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ec543db8-283b-481e-830f-32e8e884c7b3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ec543db8-283b-481e-830f-32e8e884c7b3
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ec543db8-283b-481e-830f-32e8e884c7b3 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ec543db8-283b-481e-830f-32e8e884c7b3
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=ec543db8-283b-481e-830f-32e8e884c7b3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3d7fb23d-bebb-492d-a82a-26992b0a0305 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 146.9GB: boot/grub/menu.lst
 146.9GB: boot/grub/stage2
 146.9GB: boot/initrd.img-2.6.28-11-generic
 146.9GB: boot/vmlinuz-2.6.28-11-generic
 146.9GB: initrd.img
 146.9GB: vmlinuz
```

---

### Post by darkod on 2009-12-06
Can't see much wrong with it, unless your hd0, hd1 reference is mixed up. But this setup is hell, how did you end up with this?
On drive1 you have XP, then the ubuntu swap after that.
On drive2 you start off with extended partition and then ubuntu root as primary partition.

---

### Post by hilmanzaky on 2009-12-06
> **darkod said:**
> Can't see much wrong with it, unless your hd0, hd1 reference is mixed up. But this setup is hell, how did you end up with this?
On drive1 you have XP, then the ubuntu swap after that.
On drive2 you start off with extended partition and then ubuntu root as primary partition.

Yup,
first time I already have XP system, then I want to install Ubuntu without changing or moving any data on my hard drives. So, I used a partition tool to make a space on both of my hard drives. After that I install Ubuntu, and I think there would be no problems if I set a swap space on the different drive (my mind just think that 2 hard drives looks the same as 2 partitions in one hard drive), then I got a problem with XP boot on the boot menu. So then what should I do?

---

### Post by darkod on 2009-12-06
In ubuntu try updating the device.map with:
sudo grub-install --recheck

---

### Post by presence1960 on 2009-12-06
> **hilmanzaky said:**
> Yup,
first time I already have XP system, then I want to install Ubuntu without changing or moving any data on my hard drives. So, I used a partition tool to make a space on both of my hard drives. After that I install Ubuntu, and I think there would be no problems if I set a swap space on the different drive (my mind just think that 2 hard drives looks the same as 2 partitions in one hard drive), then I got a problem with XP boot on the boot menu. So then what should I do?

You get the GRUB menu when you boot your machine? If not then go into BIOS and set the sdb disk as first hard disk to boot. Save changes to CMOS and continue booting into Ubuntu. Or if you already get GRUB boot into Ubuntu, When the desktop loads open a terminal (Applications > Accessories > Terminal). Type or copy this into terminal ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

scroll down to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1
```

Change it to look like this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

Click Save on top toolbar. Close file & reboot. Choose windpows from the GRUB menu and report back to us.

---

### Post by hilmanzaky on 2010-01-03
> **presence1960 said:**
> You get the GRUB menu when you boot your machine? If not then go into BIOS and set the sdb disk as first hard disk to boot. Save changes to CMOS and continue booting into Ubuntu. Or if you already get GRUB boot into Ubuntu, When the desktop loads open a terminal (Applications > Accessories > Terminal). Type or copy this into terminal ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

scroll down to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1
```Change it to look like this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```Click Save on top toolbar. Close file & reboot. Choose windpows from the GRUB menu and report back to us.

Sorry for my absence in past 3 weeks, 
I had just finished final exams at my college..

I already get GRUB boot into Ubuntu, and then I did what you told me and it WORKS !!!
BIG THANKS !!!

but can you explain to me why you told me to use
```
map       (hd0) (hd1)
map       (hd1) (hd0)
```

---

### Post by presence1960 on 2010-01-03
The map lines are needed when windows is not on the first disk to boot. Windows always has to be on the first disk to boot-that is just the way windows is. Some will tell you it must also be on the first partition but that is not true. I have had windows on primary partitions ranging from sda1, sda2, sda3 & sda4. All that windows requires is it be installed to any primary partition and the disk it is on be first in boot order. GRUB has a way around the boot order requirement.

Now back to your particular setup. Windows is on sda but you have sdb booting first in BIOS so you get the GRUB menu when you boot. This means windows is on the second disk to boot. The map lines "trick" or "entice" windows into "thinking" it is on the first disk to boot.

All of this is only applicable to GRUB 0.97. GRUB2 is actually easire and sets it up for you with little or no editing on your part. GRUB2 is the default bootloader for Ubuntu 9.10 & higher.

---

