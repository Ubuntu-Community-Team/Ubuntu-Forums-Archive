---
title: "Add Windows 7 to Grub Menu"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by natetheskate on 2009-01-10
ok, so installed windows 7 beta today and i want to add it to my grub menu

here is how i have it set up...

boot off my 200gb pata drive, that has two partitions
165gb for storage 
25gb for ubuntu studio

then my 500gb sata drive has three partitions
75gb for windows 7
200gb for windows vista
125gb for more storage
(the rest unallocated for future use)

before i installed windows 7, i unplugged my pata drive so windows wouldn't screw it up... that said i want to add windows 7 to grub with out the risk of losing any or all of my patitions... i haven't done anything except for using the 'fdisk -lu' command which displayed: 

```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
240 heads, 63 sectors/track, 26342 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       347094720   398291039    25598160   83  Linux
/dev/sda2   *       15120   347094719   173539800    5  Extended
/dev/sda5           15183   347091038   173537928    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfbb68a7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   409602047   204800000    7  HPFS/NTFS
/dev/sdb2       409602048   665602047   128000000    7  HPFS/NTFS
/dev/sdb3       665602048   819202039    76799996    7  HPFS/NTFS
```

where do i go from here? :confused:

---

### Post by logos34 on 2009-01-11
like this:

gksudo gedit /boot/grub/menu.lst

[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows 7
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

edit /etc/fstab so windows partitions are accesible in linux:

sudo apt-get install ntfs-config

sudo ntfs-config

add mount points in /media for windows partitions

---

### Post by maxmartin on 2009-01-11
Thanks for your post, logos. Unfortunately, when I edited my menu.lst in the way you posted and I choose "Windows 7" from the GRUB menu, it just gives me a message that BOOTMGR is missing and tells me to restart with Ctrl+Alt+Del. My setup (in case it's affecting things) involves one 150 GB drive with an Ubuntu partition and then a partition for Windows (which registers as hd1) and a 750 GB drive with one NTFS partition (which registers as hd0).

---

### Post by kranny on 2009-01-12
When U installed Windows7 ,installer might have put bootmgr and c:\Boot on your Vista partition.Try to copy/paste the bootmgr and the Boot folder from the root of your vista partition to the root of Windows 7 partition

---

### Post by logos34 on 2009-01-12
> **maxmartin said:**
> BOOTMGR is missing and tells me to restart with Ctrl+Alt+Del. My setup (in case it's affecting things) involves one 150 GB drive with an Ubuntu partition and then a partition for Windows (which registers as hd1) and a 750 GB drive with one NTFS partition (which registers as hd0).

so is it set up like kranny says--vista on the other drive, or is the 750 just a huge data partition?  

Post your 

sudo fdisk -l

---

### Post by maxmartin on 2009-01-12
Sorry, I wasn't clear - I just set up this computer, so Windows 7 is the first Windows I've installed on it. The partition on my system drive is for it. The other drive is just for file storage.

```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006d2fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c326c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9123    73280466   83  Linux
/dev/sdb2            9124        9305     1461915    5  Extended
/dev/sdb3   *        9306       18242    71779328    7  HPFS/NTFS
/dev/sdb5            9124        9305     1461883+  82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24b1b889

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976762552+   7  HPFS/NTFS

```

---

### Post by logos34 on 2009-01-12
> **maxmartin said:**
> BOOTMGR is missing and tells me to restart with Ctrl+Alt+Del. My setup (in case it's affecting things) involves one 150 GB drive with an Ubuntu partition and then a partition for Windows (which registers as hd1) and a 750 GB drive with one NTFS partition (which registers as hd0).

Ok, if your boot drive/hd0  (i.e. just to be crystal clear, the hdd set first in the bios boot priority) is the 750 GB, then this grub entry should work:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title Windows 7
**root (hd1,2)**
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

If instead, you're really booting from the 150 GB, then you don't need the mapping:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title Windows 7
root (hd0,2)
savedefault
makeactive
chainloader +1

You might want to remove the usb stick just to avoid any confusion

---

### Post by maxmartin on 2009-01-12
I am booting from the 150 GB drive...not sure how the boot order got screwed up. But anyways, that change did the trick - thanks!

---

### Post by maxmartin on 2009-01-12
EDIT: Disregard what I posted earlier - I was just having trouble mounting disks because Windows 7 won't shut down cleanly.

---

### Post by lolcats on 2009-01-12
this is how i boot every OS that isnt Linux and has its own bootloader installed:
```

rootnoverify(hdN)
chainloader
boot
```
replace N with the Nth disk on which the OS is installed. :p
**for example**

if i have disk A (0) and B (1), linux will map those to /dev/hda and /dev/hda (or sd* but that doesn't matter at the moment)
As long as you know WHERE they're mapped to, thats the important thing you have

So, if you have 3 disks (0,1,2) you'll have the following:
(hd0) (hd1) and (hd2)
lets assume hd2 doesnt matter. Lets assume that hd0 has your linux install on it and hd1 has Win7 installed.
Simply add this to your menu:
```

#windows 7
title Windows se7en beta
root(hd1)
chainloader

```

at this point i want to know how to fake out the INSTALLER to let me install to an emulated disk >.>

---

### Post by iraiscoming223 on 2009-05-08
Hello everyone!
I've been playin' around with Windows 7 and grub, but didn't succeed!
I've read all this conversation, but can't get rid of the "BOOTMGR is missing Restar with Ctrl+Alt+Del bla bla bla".
First of all, I do want to have grub instead of Windows bootloader. (this is just for personal stuff)
Here it is how my disk is organized (see attachment for gparted screenshot):
```
marco@marco-jaunty:~$ sudo fdisk -l
[sudo] password for marco: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc1b7b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3984    32001448+   7  HPFS/NTFS
/dev/sda2            3985        5229    10000462+  83  Linux
/dev/sda3            5230       14904    77714437+   5  Extended
/dev/sda4   *       14905       19458    36572160    7  HPFS/NTFS
/dev/sda5            5230       10209    40001818+   7  HPFS/NTFS
/dev/sda6           10210       14904    37712556   83  Linux

```
Windows 7 is on /dev/sda4. The other partitions are:
/dev/sda1 Windows XP
/dev/sda2 Ubuntu Jaunty
/dev/sda5 DATA partition (documents, music, and stuff like that)
/dev/sda6 /home partition
/dev/sda4 Windows 7, as said above.

The trick is - I guess - with the extended partition. How do grub read that? Should I put in my menu.lst file (hd0,5)? or (hd0,4)? Is the BOOTMGR problem related to grub's options or Windows? (note that Win XP boot flawlessly)...

Thank you for your help in the meanwhile! :)

And greetings from Italy!

---

### Post by caljohnsmith on 2009-05-08
Iraiscoming223, I think it would help to first get a clearer picture of your setup related to your Windows booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by iraiscoming223 on 2009-05-10
Hi John!
I got rid of this problem and I'm posting the solution just in case someone falls into it.
Installing Windows will replace the MBR sector with a "link" (I know this is not the right term) to the Windows Bootloader, which is actually installed on the first Windows partition (on my computer was on Windows XP partition - aka /dev/sda1).

So what you need to do is restore GRUB (i.e. with an Ubuntu live cd) and point all Windows installation to the first Windoze partition. That's all.

Thank you for your help, hope this will help someone else, too. :)

---

### Post by Reiwolf on 2009-05-22
I have the same problem with the whole bootmrg missing. Results.txt shows

>  => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7a4d7a4

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   312,576,704   312,576,642  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdd90dd90

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   234,438,655   234,436,608   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5f06eb7f-3048-4d14-a5b8-896e72f6dc54" TYPE="ext3" 
/dev/sdb1: UUID="602829AD28298360" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/rei/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rei)

and this is what i have going on for grub

title	Windows se7en RC(Loader)
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


any ideas?

---

### Post by jorge78041 on 2009-06-04
Hi,

i hope you can help me, i am very new to linux so please, be kind with your intructions and put a step by step guide,  please, i would really apreciate it.

i have windows vista and ubutnu, i just installled windows 7 and it eliminated grub, i installed grub and it only shows ubuntu and wndows vista but no more windows 7

how can i put windows 7 on the grub menu?

here are the details and thanks again


---------

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

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
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x19814382

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   299,022,326   299,022,264   7 HPFS/NTFS
/dev/sda2         299,022,336   382,906,367    83,884,032   7 HPFS/NTFS
/dev/sda3         382,909,275   464,824,709    81,915,435   5 Extended
/dev/sda5         382,909,338   461,370,734    78,461,397  83 Linux
/dev/sda6         461,370,798   464,824,709     3,453,912  82 Linux swap / Solaris
/dev/sda4         464,828,416   488,390,655    23,562,240   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="336EFB3A316973FC" TYPE="ntfs" 
/dev/sda2: UUID="3C345B09345AC614" LABEL="windows 7" TYPE="ntfs" 
/dev/sda4: UUID="84342DD8342DCE4C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="aa4b23fb-1ac1-4855-97db-2956b16373c8" TYPE="ext3" 
/dev/sda6: UUID="8d42a7b7-b2f9-415c-9c0b-829d6d4d051f" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/jorge/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jorge)


=========================== sda5/boot/grub/menu.lst: ===========================

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
default        4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        2

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
# kopt=root=UUID=aa4b23fb-1ac1-4855-97db-2956b16373c8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=aa4b23fb-1ac1-4855-97db-2956b16373c8

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        aa4b23fb-1ac1-4855-97db-2956b16373c8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aa4b23fb-1ac1-4855-97db-2956b16373c8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        aa4b23fb-1ac1-4855-97db-2956b16373c8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aa4b23fb-1ac1-4855-97db-2956b16373c8 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

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


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=aa4b23fb-1ac1-4855-97db-2956b16373c8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8d42a7b7-b2f9-415c-9c0b-829d6d4d051f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 200.4GB: boot/grub/menu.lst
 200.3GB: boot/grub/stage2
 200.4GB: boot/initrd.img-2.6.28-11-generic
 200.3GB: boot/vmlinuz-2.6.28-11-generic
 200.4GB: initrd.img
 200.3GB: vmlinuz

---

### Post by bobsta101 on 2009-08-30
Is this still a problem?

..It appears that vista has two grub entries, is this correct?

---

### Post by Intrepid Ibex on 2009-10-18
> **bobsta101 said:**
> Is this still a problem?

..It appears that vista has two grub entries, is this correct?
No.

---

### Post by bobsta101 on 2009-10-18
> **Intrepid Ibex said:**
> No.

To the two entries or still a problem?

---

### Post by Intrepid Ibex on 2010-01-01
> **bobsta101 said:**
> To the two entries or still a problem?
To both.

---

### Post by Mark Phelps on 2010-01-02
Looks like you installed Win7 from scratch because it created two partitions, the first of which is the boot partition. Unlike with Vista, Win7 installs its bootloader files into the first partition, the remainder of the OS into the second partition. 

Grub2 is probably detecting the winload file in the second partition and thinking it's a second version of the OS -- which it is not.

You should be OK if you simply select the first entry, not the second.

---

### Post by sephi.X on 2010-05-25
I have this problem, too.
Thanks, Belboz99.

---

### Post by infine0n on 2010-05-29
use super grub.

---

### Post by vladt@hotmail.com on 2011-03-09
I am having similar problem after installing Ubuntu on the same drive as Windows 7.
grub does not list Windows 7 as one of the options
manual entry in menu.lst does not change the displayed in grub options 
I am ABLE to boot windows from grub command line by entering:
root (hd0,1)
chainloader +1
boot

please advise how to get option for Windows to be displayed in grub OS selection.

---

### Post by vladt@hotmail.com on 2011-03-09
I ran boot info script and here are the results:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   841,669,285   841,669,223   7 HPFS/NTFS
/dev/sda2         841,670,654   976,771,071   135,100,418   5 Extended
/dev/sda5         841,670,656   971,173,887   129,503,232  83 Linux
/dev/sda6         971,175,936   976,771,071     5,595,136  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders, total 975400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1               2,048   975,400,959   975,398,912   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3E605D5F605D1EC9                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        39e9e57f-ef97-4421-ab01-778acb249177   ext4                                     
/dev/sda6        18527eb0-cba1-4767-9a56-3fb6c6f549c5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        3C42935F42931CA8                       ntfs       My Book                       
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr1         /media/WD SmartWare      udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdf1        /media/My Book           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
# kopt=root=UUID=39e9e57f-ef97-4421-ab01-778acb249177 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=39e9e57f-ef97-4421-ab01-778acb249177

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

title        Ubuntu 10.10, kernel 2.6.35-27-generic-pae
uuid        39e9e57f-ef97-4421-ab01-778acb249177
kernel        /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=39e9e57f-ef97-4421-ab01-778acb249177 ro quiet splash
initrd        /boot/initrd.img-2.6.35-27-generic-pae

title        Ubuntu 10.10, kernel 2.6.35-27-generic-pae (recovery mode)
uuid        39e9e57f-ef97-4421-ab01-778acb249177
kernel        /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=39e9e57f-ef97-4421-ab01-778acb249177 ro single
initrd        /boot/initrd.img-2.6.35-27-generic-pae

title        Ubuntu 10.10, memtest86+
uuid        39e9e57f-ef97-4421-ab01-778acb249177
kernel        /boot/memtest86+.bin

title        Windows
root        (hd0,1)
chainloader    +1
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 39e9e57f-ef97-4421-ab01-778acb249177
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 39e9e57f-ef97-4421-ab01-778acb249177
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 39e9e57f-ef97-4421-ab01-778acb249177
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=39e9e57f-ef97-4421-ab01-778acb249177 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 39e9e57f-ef97-4421-ab01-778acb249177
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=39e9e57f-ef97-4421-ab01-778acb249177 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 39e9e57f-ef97-4421-ab01-778acb249177
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 39e9e57f-ef97-4421-ab01-778acb249177
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=39e9e57f-ef97-4421-ab01-778acb249177 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=18527eb0-cba1-4767-9a56-3fb6c6f549c5 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 484.7GB: boot/grub/core.img
 469.8GB: boot/grub/grub.cfg
 484.7GB: boot/grub/menu.lst
 431.5GB: boot/initrd.img-2.6.35-27-generic-pae
 484.7GB: boot/vmlinuz-2.6.35-27-generic-pae
 431.5GB: initrd.img
 484.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdg

---

