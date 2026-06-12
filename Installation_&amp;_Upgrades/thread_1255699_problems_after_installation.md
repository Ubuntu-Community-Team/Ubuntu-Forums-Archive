---
title: "problems after installation"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by zaydius1729 on 2009-09-01
I need some help with my ubuntu... i just downloaded Ubuntu 9.04 yesterday and installed it side by side with windows vista. everything worked out fine and i restarted the computer and ran ubuntu for a couple of hours. then i decided to switch to windows vista. so i restarded and it asked me which OS i wanted to load and i selected vista. it gave me a screen sized window that said ERROR... so i decided to restart and load ubuntu but instead it said 

(something) grub

error 22. 

this is what it says everytime i start up the computer and i dont even get to where i can pick ubuntu or vista 

right now i am running ubuntu straight from the CD. 

i would really appreatiate any help right now..... having a really bad experience here... also note that im kind of a newbie with all this and i was recommended ubuntu because i needed a 64 bit OS instead of the 32 bit vista.

---

### Post by oboedad55 on 2009-09-01
> **zaydius1729 said:**
> I need some help with my ubuntu... i just downloaded Ubuntu 9.04 yesterday and installed it side by side with windows vista. everything worked out fine and i restarted the computer and ran ubuntu for a couple of hours. then i decided to switch to windows vista. so i restarded and it asked me which OS i wanted to load and i selected vista. it gave me a screen sized window that said ERROR... so i decided to restart and load ubuntu but instead it said 

(something) grub

error 22. 

this is what it says everytime i start up the computer and i dont even get to where i can pick ubuntu or vista 

right now i am running ubuntu straight from the CD. 

i would really appreatiate any help right now..... having a really bad experience here... also note that im kind of a newbie with all this and i was recommended ubuntu because i needed a 64 bit OS instead of the 32 bit vista.

Do you have a Vista recovery partition? Can you post your menu.lst?

---

### Post by zaydius1729 on 2009-09-01
i dont know how to do those things... im sorry!! especially on ubuntu... this is the first time im using it... i dont even know how to access my word documents an stuff...

---

### Post by zaydius1729 on 2009-09-01
how do i find the menu.lst??

---

### Post by oboedad55 on 2009-09-01
> **zaydius1729 said:**
> how do i find the menu.lst??

It's in the /boot/grub directory. You should be able to open it with a text editor then copy-paste it into your response.

---

### Post by zaydius1729 on 2009-09-01
so there is no grub in there... i used text editor and opened to file system / boot... and then it just had 
abi-2.6.28- generic
config (same) generic
memtest86+.bin
system.map... generic
vmcoreinfo...generic

so no grub there... im guessing that might be the problem!?!?

---

### Post by oboedad55 on 2009-09-01
> **zaydius1729 said:**
> so there is no grub in there... i used text editor and opened to file system / boot... and then it just had 
abi-2.6.28- generic
config (same) generic
memtest86+.bin
system.map... generic
vmcoreinfo...generic

so no grub there... im guessing that might be the problem!?!?

How did you install Ubuntu? Did you install from Vista, wubi, or did you install it side-by-side?

---

### Post by zaydius1729 on 2009-09-01
i did it side by side....

---

### Post by zaydius1729 on 2009-09-01
i already had the vista pre-installed and then yesterday i installed ubuntu side by side... where when i turned on the laptop it asked me which OS i wanted to run... except that only lasted like two times an then that started happening...

---

### Post by oboedad55 on 2009-09-01
> **zaydius1729 said:**
> i already had the vista pre-installed and then yesterday i installed ubuntu side by side... where when i turned on the laptop it asked me which OS i wanted to run... except that only lasted like two times an then that started happening...

Do a forum search for grub, and look for how to reinstall it from the LiveCD.

---

### Post by zaydius1729 on 2009-09-01
i tried to find something for that. but damn i cannot find anything... everything tells me to go to terminal an then 
sudo grub
find/boot/grub/stage1

and that doesnt work. it says error 27 unrecognized command.

---

### Post by oboedad55 on 2009-09-01
> **zaydius1729 said:**
> i tried to find something for that. but damn i cannot find anything... everything tells me to go to terminal an then 
sudo grub
find/boot/grub/stage1

and that doesnt work. it says error 27 unrecognized command.

It sounds like grub never got installed. Why don't you try a reinstall to the same partition you used last time. It only takes a few minutes and it doesn't sound like you have anything else installed yet. The grub reinstall should work. You can try this link:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by zaydius1729 on 2009-09-01
so ur saying reinstall all of ubuntu??! cuz the link that you gave me... i tried that... and it didnt work cuz when i put in find/boot/grub/stage1 it give an error an says unrecognized command...... so should i just go for a full reinstall of ubuntu??

---

### Post by presence1960 on 2009-09-01
before you go fiddling around (since you admittedly are a complete newbie) do this:

Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal (Go Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by zaydius1729 on 2009-09-01
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #10 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,482,874    20,482,812  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     20,482,875   264,670,874   244,188,000   7 HPFS/NTFS
/dev/sda3         264,670,875   488,392,064   223,721,190   f W95 Ext d (LBA)
/dev/sda5         264,670,938   472,680,494   208,009,557   7 HPFS/NTFS
/dev/sda6         472,680,558   477,564,254     4,883,697  83 Linux
/dev/sda7         477,564,318   477,917,684       353,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="RECOVERY" UUID="3C98-AC5D" TYPE="vfat" 
/dev/sda2: UUID="DE3EAC813EAC53F5" LABEL="VistaOS" TYPE="ntfs" 
/dev/sda5: UUID="A70801C933D2A843" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: UUID="a163fc42-0ccf-4e94-867f-1a747e4e5018" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="961de28d-764d-4f0c-8bd4-b4e1f369c4c1" TYPE="swap" 

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


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a163fc42-0ccf-4e94-867f-1a747e4e5018

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
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
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


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=961de28d-764d-4f0c-8bd4-b4e1f369c4c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 244.3GB: boot/grub/menu.lst
 244.3GB: boot/grub/stage2
 244.0GB: boot/initrd.img-2.6.28-11-generic
 243.9GB: boot/vmlinuz-2.6.28-11-generic
 244.0GB: initrd.img
 243.9GB: vmlinuz




there are the results.

---

### Post by presence1960 on 2009-09-01
should be a simple fix. Your GRUB is pointing to a non-existant partition sda10. It needs to point to sda6, boot from the ubuntu Live Cd and do this:
```

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,5)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,5)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

In #6 use setup (hd0)
```

---

### Post by presence1960 on 2009-09-01
> **zaydius1729 said:**
> i tried to find something for that. but damn i cannot find anything... everything tells me to go to terminal an then 
sudo grub
find/boot/grub/stage1

and that doesnt work. it says error 27 unrecognized command.

you are missing a space in that command it is find /boot/grub/menu.lst

there is a space between find and /
[B]
P.S. I just noticed your fstab file from the boot info script. You originally installed to sda10. You changed your partitions setup and neglected to tell us you did so. That did not happen on it's own. Hopefully this will still work since fstab uses UUID for partition ID

This is exactly why I insist on using the boot info script because whether inadvertently or purposefully a lot of times we don't get accurate info or the whole story from people asking for help. Without the boot info script we never would have known the OP changed his/her partition scheme.[/B]

---

### Post by zaydius1729 on 2009-09-01
thanks a lot ... it is working right now... i dont know how i changed the partition... no idea really... but i now also have another question... i just logged into ubuntu from the hardrive and the update manager showed up... and i tried to install the updates but it said there was not enough space... which is not true because when i look at my harddrives it has about 40 gigs free in one partition ( C drive) and about 100 gigs in the other one (D drive)

---

### Post by presence1960 on 2009-09-01
> **zaydius1729 said:**
> thanks a lot ... it is working right now... i dont know how i changed the partition... no idea really... but i now also have another question... i just logged into ubuntu from the hardrive and the update manager showed up... and i tried to install the updates but it said there was not enough space... which is not true because when i look at my harddrives it has about 40 gigs free in one partition ( C drive) and about 100 gigs in the other one (D drive)

In Linux there are no C; D: or any other letters. partitions are labeled sda1, sda2, sda3 etc. here is your partition table from the boot info script:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

Partition Boot Start End Size Id System

/dev/sda1 63 20,482,874 20,482,812 1c Hidden W95 FAT32 (LBA)
/dev/sda2 * 20,482,875 264,670,874 244,188,000 7 HPFS/NTFS
/dev/sda3 264,670,875 488,392,064 223,721,190 f W95 Ext d (LBA)
/dev/sda5 264,670,938 472,680,494 208,009,557 7 HPFS/NTFS
[COLOR="Red"]/dev/sda6 472,680,558 477,564,254 4,883,697 83 Linux[/COLOR]
/dev/sda7 477,564,318 477,917,684 353,367 82 Linux swap / Solaris

```
sda6 is your linux partition. Notice the size is 4,883,697. Approximately 1,304,934 equal a GB. So basically your Ubuntu partition is under 4 GB. You are going to have to shrink (resize) some free space from the windows partition (sda2) adjacent to your extended partition to create more space for Ubuntu. Then resize your extended partition (sda3) to include that space. Then you will resize sda6 Ubuntu partition to claim that space once inside the extended partition.

Or an easier way is to shrink sda5 and then resize sda6 to use that space. i would add about 8 -10 more GB to make sure you have room for updates and software you may install.

P.S. Do the resizing from the Live CD. Boot the Cd and choose "try ubuntu without any changes", when the desktop loads go System > Administration > Partition Editor

---

### Post by raymondh on 2009-09-01
> **zaydius1729 said:**
> thanks a lot ... it is working right now... i dont know how i changed the partition... no idea really... but i now also have another question... i just logged into ubuntu from the hardrive and the update manager showed up... and i tried to install the updates but it said there was not enough space... which is not true because when i look at my harddrives it has about 40 gigs free in one partition ( C drive) and about 100 gigs in the other one (D drive)

When you installed side-by-side, did you use a slider to allocate partition sizies between Vista and Ubuntu?

Kindly access a terminal (once again) and type and paste back the output of

```
df -h
```

Presence1960 has a picture of that slider I am talking about.  Hopefully he can post it here as I had saved it in another machine ;)

EDIT :  Presence is correct about which partitions to resize. :)

---

### Post by presence1960 on 2009-09-01
here it is raymond

---

### Post by zaydius1729 on 2009-09-01
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.3G     0 100% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  104K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  168K  2.0G   1% /dev
tmpfs                 2.0G  540K  2.0G   1% /dev/shm
lrm                   2.0G  2.7M  1.9G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp

---

### Post by zaydius1729 on 2009-09-01
i dont know how to look at the slider... and i definitely did not do anything with it when i initialled installed ubuntu... u guys are a lot of help and i really appretiate it!

---

### Post by zaydius1729 on 2009-09-01
actually yes i do remember that picture... but i didnt do anything with it since i didnt wanna screw anything up...i did have them side by side though..

---

### Post by presence1960 on 2009-09-01
> **zaydius1729 said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.3G     0 100% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  104K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  168K  2.0G   1% /dev
tmpfs                 2.0G  540K  2.0G   1% /dev/shm
lrm                   2.0G  2.7M  1.9G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp

who don't know that!This a very common mistake on the side by side install. Don't fret it is easily fixed like I posted previously. I would use my last option as it is the easiest for a newbie. Shrink the sda5 partition and then add the space to sda6. I would use 8-10 GB so you have enough to update and install a bunch of software. Shrinking sda5 would be the easiest because it is in the extended partition sda3 and adjacent to the Ubuntu / partition sda6.

Please be patient while the resize operations are happening. They can take a little time.

---

### Post by presence1960 on 2009-09-01
> **zaydius1729 said:**
> actually yes i do remember that picture... but i didnt do anything with it since i didnt wanna screw anything up...i did have them side by side though..
well it is too late for that now. you won't use that again unless you do another install. Chalk it up as a lesson learned. In my opinion if you aren't messing anything up in Linux then you are not really learning much.

---

### Post by zaydius1729 on 2009-09-01
how do i get to the slider where i can resize them??

---

### Post by zaydius1729 on 2009-09-01
hahah,... wellllll i kinda realized that... so should i uninstall and reinstall it again?!!?

---

### Post by presence1960 on 2009-09-01
> **zaydius1729 said:**
> how do i get to the slider where i can resize them??

you can't now , that is for the install. You are past that point. boot off the Ubuntu CD. choose "try ubuntu without any changes", when the desktop loads go System > Administration > Partition Editor

when gparted loads right click sda5 and choose resize. Grab the right border of sda5 with your pointer and drag it to the left until you have created 8-10 GB for Ubuntu. You will see the numbers changing as you move on the last readout (should say space after)

click Apply (green check mark at top toolbar) Be patient allow it to complete. It may take some time. When done you should have some grey unallocated space between sda5 and sda6. Right click sda6 and choose resize. Grab the left border of sda6 and drag it all the way to left as the graphic will allow. This will use all that freed up space for Ubuntu. Click apply and be patient again. it is important that you allow these to complete uninterrupted. If you abort or interrupt the process you may have a corrupted partition or two and may not be able to boot Ubuntu!

---

### Post by zaydius1729 on 2009-09-02
so i posted on here yesterday about some troubles i was having with the installation and you guys helped me out a lot but unfortunately it fixed half of the problem... ubuntu is running fine now... but i cannot load us windows vista now... when i try to do that it shows a bar on the bottom that says loading files... an then it goes to a greay screen followed by a full screen window that says error in big red letters.... stuck there and would really appretiate some help... something that might be of importance is that now when i turn on the computer and it gives me the choice for ubuntu or vista... there are a total of four ubuntu choices( two of them are recovery ) and two windows vista choices( 1 recovery)... i would really appretiate the help... i like ubuntu but i still need vista since i have a lot of stuff saved on there that i cant access though ubuntu yet... im sure there is a way to do it but just havent figured it out.

---

### Post by zaydius1729 on 2009-09-02
so i posted on here yesterday about some troubles i was having with the installation and you guys helped me out a lot but unfortunately it fixed half of the problem... ubuntu is running fine now... but i cannot load us windows vista now... when i try to do that it shows a bar on the bottom that says loading files... an then it goes to a greay screen followed by a full screen window that says error in big red letters.... stuck there and would really appretiate some help... something that might be of importance is that now when i turn on the computer and it gives me the choice for ubuntu or vista... there are a total of four ubuntu choices( two of them are recovery ) and two windows vista choices( 1 recovery)... i would really appretiate the help... i like ubuntu but i still need vista since i have a lot of stuff saved on there that i cant access though ubuntu yet... im sure there is a way to do it but just havent figured it out.

---

### Post by zaydius1729 on 2009-09-02
somebody please help... i need to have vista running soon... i would really really appretiate it.

---

### Post by presence1960 on 2009-09-02
Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by zaydius1729 on 2009-09-02
=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,482,874    20,482,812  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     20,482,875   264,670,874   244,188,000   7 HPFS/NTFS
/dev/sda3         264,670,875   488,392,064   223,721,190   f W95 Ext d (LBA)
/dev/sda5         264,670,938   451,876,319   187,205,382   7 HPFS/NTFS
/dev/sda6         451,876,383   477,564,254    25,687,872  83 Linux
/dev/sda7         477,564,318   477,917,684       353,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="RECOVERY" UUID="3C98-AC5D" TYPE="vfat" 
/dev/sda2: UUID="DE3EAC813EAC53F5" LABEL="VistaOS" TYPE="ntfs" 
/dev/sda5: UUID="A70801C933D2A843" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: UUID="a163fc42-0ccf-4e94-867f-1a747e4e5018" TYPE="ext3" 
/dev/sda7: UUID="961de28d-764d-4f0c-8bd4-b4e1f369c4c1" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zayd/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zayd)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a163fc42-0ccf-4e94-867f-1a747e4e5018

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
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


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=961de28d-764d-4f0c-8bd4-b4e1f369c4c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 233.6GB: boot/grub/menu.lst
 233.7GB: boot/grub/stage2
 233.4GB: boot/initrd.img-2.6.28-11-generic
 233.6GB: boot/initrd.img-2.6.28-15-generic
 233.2GB: boot/vmlinuz-2.6.28-11-generic
 233.5GB: boot/vmlinuz-2.6.28-15-generic
 233.6GB: initrd.img
 233.4GB: initrd.img.old
 233.5GB: vmlinuz
 233.2GB: vmlinuz.old


thanks a lot

---

### Post by presence1960 on 2009-09-02
OK, everything looks good including your Vista partition and the Vista entry for sda2 in GRUB. I had to go back in this thread to see that you you resized Vista with the Live CD. That is probably why your Vista will not boot. if you shrunk Vista with the Live CD you need to do this:

1. Go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") to download a Vista recovery console CD since you have a recovery partition and can't access recovery console from the recovery partition. download the iso for your version of Vista and burn the iso as an image to CD.

2. Boot of that CD and do [this]("http://ubuntuforums.org/showthread.php?t=1014708") (scroll down to the instructions for Vista). When complete reboot and you should boot right into Vista. if successful proceed to #3.

3. Now you must restore GRUB to MBR like this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,5)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,5)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

You should be good to go. There is a documented bug (see [here]("http://bugzilla.gnome.org/show_bug.cgi?id=379482")) when resizing Vista with gparted or any outside partitioner. Sometimes it works but other times it renders vista unbootable. Next time you ever have to shrink Vista'a partition do so with Vista's disk management utility.

---

### Post by zaydius1729 on 2009-09-02
so i did what you told me... i burnt the CD and loaded it up and it worked and everything was fine... i took out the CD and it loaded up the vista properly... then i did what you told me with the Ubuntu liveCD... and did the grub stuff... that worked ... an then i rebooted the laptop without the CD and tried to go into vista... same problem!!!  it ends up with a window that say says cannot open C:\recovery.dat  and then a big red ERROR... im gonna look at the results file again and post it for you...

---

### Post by zaydius1729 on 2009-09-02
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,482,874    20,482,812  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     20,482,875   264,670,874   244,188,000   7 HPFS/NTFS
/dev/sda3         264,670,875   488,392,064   223,721,190   f W95 Ext d (LBA)
/dev/sda5         264,670,938   451,876,319   187,205,382   7 HPFS/NTFS
/dev/sda6         451,876,383   477,564,254    25,687,872  83 Linux
/dev/sda7         477,564,318   477,917,684       353,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="RECOVERY" UUID="3C98-AC5D" TYPE="vfat" 
/dev/sda2: UUID="DE3EAC813EAC53F5" LABEL="VistaOS" TYPE="ntfs" 
/dev/sda5: UUID="A70801C933D2A843" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: UUID="a163fc42-0ccf-4e94-867f-1a747e4e5018" TYPE="ext3" 
/dev/sda7: UUID="961de28d-764d-4f0c-8bd4-b4e1f369c4c1" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zayd/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zayd)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a163fc42-0ccf-4e94-867f-1a747e4e5018

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a163fc42-0ccf-4e94-867f-1a747e4e5018
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


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=a163fc42-0ccf-4e94-867f-1a747e4e5018 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=961de28d-764d-4f0c-8bd4-b4e1f369c4c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 233.6GB: boot/grub/menu.lst
 233.7GB: boot/grub/stage2
 233.4GB: boot/initrd.img-2.6.28-11-generic
 233.6GB: boot/initrd.img-2.6.28-15-generic
 233.2GB: boot/vmlinuz-2.6.28-11-generic
 233.5GB: boot/vmlinuz-2.6.28-15-generic
 233.6GB: initrd.img
 233.4GB: initrd.img.old
 233.5GB: vmlinuz
 233.2GB: vmlinuz.old





so this is the new results file dont know if there is any change that u can see... and thanks again for helping me with this.

---

### Post by presence1960 on 2009-09-03
you should choose the second vista entry. the first is your recovery partition. I would comment out the recovery partition by doing this: Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```

scroll to the bottom and make the changes in red:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
[COLOR="Red"]#[/COLOR] on /dev/sda1
[COLOR="Red"]#[/COLOR]title Windows Vista (loader)
[COLOR="Red"]#[/COLOR]rootnoverify (hd0,0)
[COLOR="Red"]#[/COLOR]savedefault
[COLOR="Red"]#[/COLOR]makeactive
[COLOR="Red"]#[/COLOR]chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista (loader)
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1
```

adding # to each line will hide the recovery partition during GRUB

To use the recovery partition you should refer to your computer documentation. That usually involves pressing a certain key at boot to invoke the recovery option.

---

