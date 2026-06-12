---
title: "Wanna punch GRUB in the face...HELP!"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by theProdiKalson on 2009-06-06
I REALLLLLLY need help i have been reading everything but cant find a way to boot into my WinXP Pro install..  
I successfully added it to the GRUB menu but it just says starting up then control alt del to restart... what a tease why wont windows open her legs and let me in damn it??

so i dont know what this means but i typed sudo blkid into the terminal and got this...

```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0917" TYPE="vfat" 
/dev/sda2: UUID="49c04831-a9f6-411f-9707-f62cb054a99d" TYPE="ext2" 
/dev/sda5: UUID="6C2420A82420776C" LABEL="Media" TYPE="ntfs" 
/dev/sda6: UUID="8E88D93188D91893" TYPE="ntfs" 
/dev/sda7: TYPE="swap" UUID="47ec59ee-34d1-418f-abab-6839a1e7a04a" 
```
and this is my fdisk...

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          17      136521   de  Dell Utility
/dev/sda2   *          18         990     7815622+  83  Linux
/dev/sda3             991        9729    70196017+   f  W95 Ext'd (LBA)
/dev/sda5            1293        3842    20482843+   7  HPFS/NTFS
/dev/sda6            3843        9729    47287296    7  HPFS/NTFS
/dev/sda7             991        1292     2425752   82  Linux swap / Solaris

Partition table entries are not in disk order

```and finally my GRUB...
```

title    MS Windows XP
map (hd0,0) (hd0,5)
map (hd0,5) (hd0,0)
root (hd0,5)
chainloader    +1
```
so i got all this going on and this is my first few hours using the OS and i NEED to boot back to windows and dont wanna format... where do i go from here???

---

### Post by merlinus on 2009-06-06
Try the supergrub disk.  It may allow you to boot into windows and even restore it to the mbr, if that is what you are wanting.

I do believe that windows cannot reside on a logical partition, only a primary.

So perhaps it is gates that you would like to punch in the face.... :p

---

### Post by theProdiKalson on 2009-06-06
aww man this cant be... partitioned the hdd a while ago with the intention of installing ubuntu and just now got around to it.... when i installed windows my os was on my "G: DRIVE" ahhh beloved windows lingo... so much easier than sda6.. but i guess i see how sda6 is more descriptive and explains that it is on a logical partition...

anyway point is windows was working fine and ubuntu was installed on the "C Drive"
when i installed ubuntu i split up the c drive to have a swap area... i dunno what that is but they said i needed it in a thread i read b4 installing...

so i basically if i leave never never land i can never come back?

ps if i punch gates his glasses will cut my hand...
GRUB sounds like a he has a red rubber nose... more fist friendly..

---

### Post by lindsay7 on 2009-06-06
Ok, here is the instructions to get your mbr back so that you can boot xp.

Basically boot the xp install disk and go to the repair option and get to the command line, then type "fixmbr" without the quotation marks. After this is fixed we can work on the grub menu to boot Ubuntu.


[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

---

### Post by theProdiKalson on 2009-06-06
> **lindsay7 said:**
> Ok, here is the instructions to get your mbr back so that you can boot xp.

Basically boot the xp install disk and go to the repair option and get to the command line, then type "fixmbr" without the quotation marks. After this is fixed we can work on the grub menu to boot Ubuntu.


[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)
THANKS FOR THE HELP!!!!! 
im gonna try now!

---

### Post by lindsay7 on 2009-06-06
When you get windows back. Boot us Ubuntu with the live cd and do the following. If you do not get windows back after the mbr fix attempt, go ahead and do the following anyway. This will help towards getting this fixed.

Can you do this, it will give us all the info about you machine,

Please download this and place it on your Desktop in Ubuntu:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

You will have you run it, so that we can gather more information about your hard drive setup and boot process to troubleshoot the problem more clearly.

After you download it to the Desktop, right-click it and click Properties, then click the Permissions tab and check the box at the bottom of the window that 'allows executing'.

Then click the Applications menu at the top right of your screen, followed by the Accessories menu and then click Terminal. A black window will come up, in it type the following commands, ending each line with a press of the Enter key:

Code:

cd ~/Desktop
sudo ./boot*.sh

Please remember that in Linux, everything is case sensitive. Therefore, a lowercase 'd' is different than an uppercase 'D'. Also, you will be prompted for the password you gave when you installed Ubuntu whenever you use the 'sudo' command. The 'sudo' command escalates privileges and in this case is needed to properly view the hard drives and boot process.

After you have done this, it should place a Results.txt file on your desktop. Double-click that file and select Edit->Copy. Then return here and start a new reply message. In this message, click the # sign at the top of the message editor box and this will give you CODE tags; click between these tags ({code]here[/code}) and paste the contents that you copied from the Result

---

### Post by theProdiKalson on 2009-06-06
thanks for such explicit instrustions if i really wasnt such an ubuntu idiot i would be offended lmao
but really appriciate it man!
here is the results...
decided to do this b4 the mbr just in case
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       273,104       273,042  de Dell Utility
/dev/sda2    *        273,105    15,904,349    15,631,245  83 Linux
/dev/sda3          15,904,350   156,296,384   140,392,035   f W95 Ext d (LBA)
/dev/sda5          20,756,043    61,721,729    40,965,687   7 HPFS/NTFS
/dev/sda6          61,721,793   156,296,384    94,574,592   7 HPFS/NTFS
/dev/sda7          15,904,476    20,755,979     4,851,504  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0917" TYPE="vfat" 
/dev/sda2: UUID="49c04831-a9f6-411f-9707-f62cb054a99d" TYPE="ext2" 
/dev/sda5: UUID="6C2420A82420776C" LABEL="Media" TYPE="ntfs" 
/dev/sda6: UUID="8E88D93188D91893" TYPE="ntfs" 
/dev/sda7: UUID="47ec59ee-34d1-418f-abab-6839a1e7a04a" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext2 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/adellimore/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=adellimore)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=adellimore)


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
# kopt=root=UUID=49c04831-a9f6-411f-9707-f62cb054a99d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=49c04831-a9f6-411f-9707-f62cb054a99d

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

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        49c04831-a9f6-411f-9707-f62cb054a99d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=49c04831-a9f6-411f-9707-f62cb054a99d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        49c04831-a9f6-411f-9707-f62cb054a99d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=49c04831-a9f6-411f-9707-f62cb054a99d ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        49c04831-a9f6-411f-9707-f62cb054a99d
kernel        /boot/memtest86+.bin
quiet

title MS Windows XP
root (hd0,5)
makeactive
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST
###map (hd0,0) (hd0,3)
###map (hd0,3) (hd0,0)
###rootnoverify (hd0,3)
###chainloader +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=49c04831-a9f6-411f-9707-f62cb054a99d /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=47ec59ee-34d1-418f-abab-6839a1e7a04a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


   4.1GB: boot/grub/menu.lst
   4.2GB: boot/grub/stage2
   4.2GB: boot/initrd.img-2.6.27-14-generic
   4.1GB: boot/initrd.img-2.6.27-7-generic
   4.2GB: boot/vmlinuz-2.6.27-14-generic
   4.2GB: boot/vmlinuz-2.6.27-7-generic
   4.2GB: initrd.img
   4.1GB: initrd.img.old
   4.2GB: vmlinuz
   4.2GB: vmlinuz.old
```

ok now off to mbr thing

---

### Post by theProdiKalson on 2009-06-06
> **lindsay7 said:**
> Ok, here is the instructions to get your mbr back so that you can boot xp.

Basically boot the xp install disk and go to the repair option and get to the command line, then type "fixmbr" without the quotation marks. After this is fixed we can work on the grub menu to boot Ubuntu.


[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)
i did the fixmbr....
i have no computer now... 
it doesnt boot into anything...
im useing a live cd..

how do i get grub back...

---

### Post by lindsay7 on 2009-06-06
Ok, One of the things going on here that is not correct is that the windows boot instructions are in the wrong place. This is what you have now

Now,

```
title        Ubuntu 8.10, memtest86+
uuid        49c04831-a9f6-411f-9707-f62cb054a99d
kernel        /boot/memtest86+.bin
quiet

title MS Windows XP
root (hd0,5)
makeactive
chainloader +1



### END DEBIAN AUTOMAGIC KERNELS LIST
###map (hd0,0) (hd0,3)
###map (hd0,3) (hd0,0)
###rootnoverify (hd0,3)
###chainloader +1

```


The widows boot instructions need to be below the line ###Edn DEBIAN AUTOMATIC KERRELS LIST.

Should be like this

```
title        Ubuntu 8.10, memtest86+
uuid        49c04831-a9f6-411f-9707-f62cb054a99d
kernel        /boot/memtest86+.bin
quiet




### END DEBIAN AUTOMAGIC KERNELS LIST
###map (hd0,0) (hd0,3)
###map (hd0,3) (hd0,0)
###rootnoverify (hd0,3)
###chainloader +1


title MS Windows XP
root (hd0,5)
savedefault
makeactive
chainloader +1




```


To edit the grub type the following in the Ubuntu terminal,

sudo gedit /boot/grub/menu.lst   that is the letter l not the number 1.

cut and paste the above and save the file. Be sure to delete the incorrect windows boot instructions that are above the line.

Please note that we are going with the idea that windows is on hd5 which is sda6, in fact it could be on hd4 which is sda5. So you may need to try this if you can not get windows to boot when we get the grub menu fixed.

---

### Post by theProdiKalson on 2009-06-06
i have no grub to edit..
i tried the above lines many times before ... and different partitions

im gonna put the hdd in the vitamix blender with some bsn synta6 protein and kiss buntu goodbye
wat a waste

---

### Post by lindsay7 on 2009-06-06
Sorry, I had a typo and had to fix it, this gets a little confusing sometimes. Anyway it is right now.

To get Grub back, use the Ubuntu live cd and type the following in the terminal.

sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hdx)
quit

Then reboot and see if this fixed it.

This process is give and take. When you get the mbr fixed it wipes out the  grub menu, and if the grub menu is incorrect you either can not boot to anything or can not boot to windows.  So, things get messed up until it is all correct.

---

### Post by confused57 on 2009-06-06
You can reinstall grub to the mbr, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Edit:  Ignore, Lindsay7 beat me to it.

---

### Post by lindsay7 on 2009-06-06
You do have a grub menu, here it is, this is from the script that you ran and posted.

```
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
# kopt=root=UUID=49c04831-a9f6-411f-9707-f62cb054a99d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=49c04831-a9f6-411f-9707-f62cb054a99d

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

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        49c04831-a9f6-411f-9707-f62cb054a99d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=49c04831-a9f6-411f-9707-f62cb054a99d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        49c04831-a9f6-411f-9707-f62cb054a99d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=49c04831-a9f6-411f-9707-f62cb054a99d ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        49c04831-a9f6-411f-9707-f62cb054a99d
kernel        /boot/memtest86+.bin
quiet

title MS Windows XP
root (hd0,5)
makeactive
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST
###map (hd0,0) (hd0,3)
###map (hd0,3) (hd0,0)
###rootnoverify (hd0,3)
###chainloader +1


```

The gedit /boot/grub/menu.lst will find it and you can edit it.

---

### Post by theProdiKalson on 2009-06-06
IM BACK IN BUSINESS!!!
i have been trying for 6 hours to get back into my winxp install but that FIXMBR thing was a real flacid maker... i was ready to quit and just format and lose everything...

but i went from the winXP boot loader to the grub bootloader...
at least i think i did...
thanks for the help on how to get grub back!!

i didnt think i would be so happy to hear the ubuntu start up noise... man this OS is demanding...well im back to square one.. at least i dont need to use the liveCD that was so slow...

---

### Post by theProdiKalson on 2009-06-06
ok linsay even if i put the winXP below the ### line it wouldnt matter....
i think the "###" denotes comments in the menu.lst file that arent seen when running, so above or below wouldnt really make  a difference...

i tried it anyway and gave me the same thing... invaid device thing Error12

i was better off when i tried to trick windows into thinking that it was a primary partition... i read it somewhere in another thread... 
but anyway with the other format it has no error but gets stuck at starting up...back to square 1 at the start of the thread....

---

### Post by confused57 on 2009-06-06
> **theProdiKalson said:**
> ok linsay even if i put the winXP below the ### line it wouldnt matter....
i think the "###" denotes comments in the menu.lst file that arent seen when running, so above or below wouldnt really make  a difference...

i tried it anyway and gave me the same thing... invaid device thing Error12

i was better off when i tried to trick windows into thinking that it was a primary partition... i read it somewhere in another thread... 
but anyway with the other format it has no error but gets stuck at starting up...back to square 1 at the start of the thread....

Sorry to intrude again, lindsay7's advice has been excellent, but this may explain the problems booting Windows from a logical partition using grub:
[http://members.iinet.net.au/~herman546/p15.html#12_](http://members.iinet.net.au/~herman546/p15.html#12_)

---

### Post by lindsay7 on 2009-06-06
Those windows lines do need to be below the line.

Go back and edit the Grub menu again and try changing the windows number to the following,

> Please note that we are going with the idea that windows is on hd5 which is sda6, in fact it could be on hd4 which is sda5. So you may need to try this if you can not get windows to boot when we get the grub menu fixed.

so make it read as such,

title MS Windows XP
root (hd0,4)
savedefault
makeactive
chainloader +1


type gedit /boot/grub/menu.lst and change the root and save and reboot and see if that works.

---

### Post by lindsay7 on 2009-06-06
Thanks for the help here, confused57, I am about out of ideas after my last post on changing the root designation. So any aid on getting this resolved would sure help.

Thanks again.

---

### Post by theProdiKalson on 2009-06-06
im positive it is not sda5... initially i had windows installed alone on this laptop.  I made an additional extended partition for all my media and shared the folder in a home workgroup (or logical partition im not sure the difference yet but i know it was not a primary)  the only primary partition was the "C: drive" and i used that to install ubuntu.  The drive was empty or so i thought it was until after reading the line confused posted...thanks buddy!... there might have been files needed to boot windows on the primary partion that i installed ubuntu on... i really made a mess of things =(...

also the site said i needed to use the live cd to make sda6 a bootable partition and remove the make active line to avoid ther error 12...
am i on the right track? or still retarted?

---

### Post by lindsay7 on 2009-06-06
You have two partitions that are windows, this from the boot script

```
sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   


```

It will not hurt anything to try changing the root number in the grub menu and see it will work. I would try it just to rule the possibility out.

---

### Post by theProdiKalson on 2009-06-06
i tried
im a possibility ruler...

so i booted into recovery console again... to scared to do the fixmbr... even typing it scares lol...
that was like an acid trip not being about to boot up into any operating system when i have two!

when in the rocovery concole i did boocfg/scan to search for windows installs on any disk and found nothing... i then typed G: to go to the drive where i know it is installed and it cound not enumerate the volue.... i guess this means the partition is bad? and if no windows instalations were found then i guess i need to reinsall windows on another primary partition.... when in ubuntu i can see all the windows files still thou... they seem ok... i dunno why i cant get to those suckers...

---

### Post by confused57 on 2009-06-06
> also the site said i needed to use the live cd to make sda6 a bootable partition and remove the make active line to avoid ther error 12...
am i on the right track? or still retarted?
Have you tried this yet to see if it works.

A search found this link, which suggests making a very small primary FAT32 partition:
[http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition](http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition)

You may be able to resize the end of your Linux partition to free some space(maybe no more than 20 Mb?) for a FAT boot partition for Windows.  Worth a shot to avoid reinstalling Windows.

I can't really offer any additional advice, since I've never actually done this myself; but it should give you some things to try...Good Luck.

---

### Post by lindsay7 on 2009-06-06
I read the grub info that was pointed out and this sounds like it may work. You can find Gparted on the the live cd or you can install it on your Ubuntu system. I like to work with it from the Gparted Live cd which you can download form their web site. The drive that you want to work on must be unmounted to do anything to it so the bootable Gparted cd makes this easy since all the computer drive will be unmounted when you use the Gparted live cd.

Anyway this looks like a good option for you.

---

