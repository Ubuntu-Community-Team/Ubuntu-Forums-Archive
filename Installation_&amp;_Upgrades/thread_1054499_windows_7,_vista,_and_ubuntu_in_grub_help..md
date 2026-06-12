---
title: "windows 7, vista, and ubuntu in grub help."
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by killergp123 on 2009-01-29
Here is the setup I have:
sda1:recovery---sda2:vista
sdb1:extra storage---sdb2:windows 7---sdb3/5/6:ubuntu

On bootup I have the 3 choices for ubuntu, then under other I have 2 options for vista, the first goes to recovery, second to windows boot menu where I can choose vista or windows 7.

I want to know if it is possible to eliminate windows boot menu and get windows 7 and vista directly on the grub menu instead.  Here is my boot info:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x381ff000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    23,406,704    23,406,642   7 HPFS/NTFS
/dev/sda2    *     23,406,705   488,392,064   464,985,360   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd1040c6a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   568,588,544   568,586,497   7 HPFS/NTFS
/dev/sdb2         771,971,072   976,771,071   204,800,000   7 HPFS/NTFS
/dev/sdb3         568,588,545   771,955,379   203,366,835   5 Extended
/dev/sdb5         568,588,608   763,617,644   195,029,037  83 Linux
/dev/sdb6         763,617,708   771,955,379     8,337,672  82 Linux swap / Solaris

/dev/sdb2 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C6FEAF4EFEAF3619" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda2: UUID="0296D25596D248B5" TYPE="ntfs" 
/dev/sdb1: UUID="D420F00A20EFF182" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb2: UUID="8A86999E86998AF9" LABEL="Windows 7" TYPE="ntfs" 
/dev/sdb5: UUID="93d86cf0-7162-4b59-b77c-f652e665df6b" TYPE="ext3" 
/dev/sdb6: UUID="d31bb621-b274-4ab0-b581-b3aff9d3e1ea" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
/dev/sdb2 on /media/Windows 7 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=93d86cf0-7162-4b59-b77c-f652e665df6b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=93d86cf0-7162-4b59-b77c-f652e665df6b

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
uuid		93d86cf0-7162-4b59-b77c-f652e665df6b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=93d86cf0-7162-4b59-b77c-f652e665df6b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		93d86cf0-7162-4b59-b77c-f652e665df6b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=93d86cf0-7162-4b59-b77c-f652e665df6b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		93d86cf0-7162-4b59-b77c-f652e665df6b
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=93d86cf0-7162-4b59-b77c-f652e665df6b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=d31bb621-b274-4ab0-b581-b3aff9d3e1ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location  of files loaded by Grub: ===================


 335.4GB: boot/grub/menu.lst
 335.5GB: boot/grub/stage2
 335.5GB: boot/initrd.img-2.6.27-7-generic
 335.5GB: boot/vmlinuz-2.6.27-7-generic
 335.5GB: initrd.img
 335.5GB: vmlinuz

=======Devices which don't seem to have a corresponding hard drive==============

 sdc .

```
Let me know if you need any more info.
Any help would be greatly appreciated, as I am new to grub, and linux in general.

---

### Post by dstew on 2009-01-29
For starters, you should be able to get Windows 7 to boot by adding this to the grub menu.lst:```
title		Windows 7
root		(hd1,1)
savedefault
makeactive
chainloader	+1
```You then have to get Windows Vista to boot without showing you a menu. I don't know how to do that.

---

### Post by killergp123 on 2009-01-29
ok thanks, now I hope someone else knows how to get rid of that menu :)

---

### Post by caljohnsmith on 2009-01-29
It looks like that main issue preventing you from booting Windows 7 separate from Vista right now is that Win 7 put its boot files in your Vista partition. If you want to boot Win 7 and Vista separately, I would first recommend following [this tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") for how to restore and configure Win 7's boot files (just do step 2 of that tutorial). Also, the Grub entry for Win 7 you should try in your menu.lst would be:
```
title       Windows 7
rootnoverify     (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Let me know how it goes, or if you run into problems with the tutorial. Once you have Windows booting on its own, it should be easy to reconfigure Vista so it doesn't offer the option to boot Win 7; but try getting Win 7 booting by itself first, and then I can help you with Vista if you want.

---

### Post by killergp123 on 2009-01-30
It half works, when I choose the windows 7 from the grub menu, it has the loading of windows, the little bar on the bottom(when I tried a second time it gave the options for normal or safemode for booting, so it is almost there), then goes to a blue screen for a split second and restarts.  If I choose vista and then windows 7, it loads fine still.

I tried step three of that page, as it said it doesn't always work with step 2, and when I go to rebuild BS, it just gives me options for dump, list, or quit.

Thanks for the help so far, and look forward to your answer.

---

### Post by caljohnsmith on 2009-01-30
According to the output of the script, there is fortunately nothing wrong with your Windows 7 boot sector, so that's why testdisk does not give you the option to do the "Rebuild BS"--your Windows 7 boot sector does not need fixing. When you ran all the bcdedit commands, did they all complete successfully, or did any return an error? How about posting:
```
sudo mount /dev/sdb2 /mnt && { ls -l /mnt; ls -l /mnt/[Bb][Oo][Oo][Tt]; }
```
And we can work from there.

---

### Post by killergp123 on 2009-01-30
all of the bcd commands said they completed successfully, the only one that didn't go through successful was that last command with nt60 in it, and the tutorial said that one might not.

Here are the results:

```
total 5809057
-rwxrwxrwx 1 root root         24 2008-10-15 11:11 autoexec.bat
drwxrwxrwx 1 root root       4096 2009-01-30 00:56 BOOT
-rwxrwxrwx 1 root root     377151 2008-12-13 12:45 bootmgr
-rwxrwxrwx 1 root root         10 2008-10-15 11:11 config.sys
drwxrwxrwx 1 root root          0 2009-01-27 01:21 Diskeeper
drwxrwxrwx 1 root root          0 2008-12-12 17:58 Documents and Settings
-rwxrwxrwx 1 root root 2414682112 2009-01-29 23:17 hiberfil.sys
-rwxrwxrwx 1 root root 3533369344 2009-01-29 23:17 pagefile.sys
drwxrwxrwx 1 root root          0 2008-12-13 01:57 PerfLogs
drwxrwxrwx 1 root root       4096 2009-01-28 10:28 ProgramData
drwxrwxrwx 1 root root       8192 2009-01-28 11:14 Program Files
drwxrwxrwx 1 root root          0 2009-01-27 23:27 Recovery
drwxrwxrwx 1 root root          0 2009-01-27 23:28 $Recycle.Bin
drwxrwxrwx 1 root root       4096 2009-01-29 15:52 System Volume Information
drwxrwxrwx 1 root root       4096 2009-01-27 23:27 Users
drwxrwxrwx 1 root root      16384 2009-01-28 09:06 Windows
total 3940
-rwxrwxrwx 1 root root  262144 2009-01-30 00:57 bcd
-rwxrwxrwx 1 root root   17408 2009-01-30 00:57 bcd.LOG
-rwxrwxrwx 1 root root    1024 2008-12-13 12:45 bootfix.bin
-rwxrwxrwx 1 root root 3170304 2008-12-13 12:45 boot.sdi
-rwxrwxrwx 1 root root   97280 2008-12-13 12:45 bootsect.exe
-rwxrwxrwx 1 root root    4096 2008-12-13 12:45 etfsboot.com
-rwxrwxrwx 1 root root  473864 2008-12-13 12:45 memtest.exe

```

---

### Post by meierfra. on 2009-01-30
Try this:  Boot into Windows 7. Click on "Start" and type "cmd". Press "Ctrl Shift Enter".  This should open a console with administrator rights.

Determine the drive letter of your Windows 7 partition (either via "diskpart"  "list volume" or by going to "Start->Computer")

Type

```
bcdedit /store C:\boot\bcd /set {default} osdevice  partition=C:

bcdedit /store C:\boot\bcd /set {default} device partition=C:

bcdedit /store C:\boot\bcd /set {bootmgr} device partition=C:
```

Here in place of "C:" you need to use you the drive letter of your Windows 7 partition.


If this did not solve your problem, boot into Window 7 again. Open a console as above. Type
```
bcdedit /store C:\boot\bcd >>C:\info.txt

bcdedit /store D:\boot\bcd >>C:\info.txt

bcdedit /store E:\boot\bcd >>C:\info.txt


```

Here replace "C:" by the drive letter of you Windows 7 partition, "D:"  by the drive letter of your Vista partition and "E:" by the drive letter of your Recovery partition. Then post the content  of the file "info.txt" in the root folder of your Windows 7 partition.

---

### Post by killergp123 on 2009-01-30
The first set of bcdedits did not help, so here is the contents of the info.txt:
```


Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {default}
displayorder            {default}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {default}
device                  partition=C:
path                    \windows\system32\boot\winload.exe
description             Windows Setup
locale                  en-US
inherit                 {bootloadersettings}
osdevice                partition=C:
systemroot              \windows
detecthal               Yes
winpe                   Yes
ems                     Yes

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=I:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {default}
resumeobject            {f35d9244-ed0a-11dd-9df4-a8df01cb1458}
displayorder            {default}
                        {6dfc5cb0-f9ab-11da-ae34-df1fe3e76dcf}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {default}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {f35d9246-ed0a-11dd-9df4-a8df01cb1458}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {f35d9244-ed0a-11dd-9df4-a8df01cb1458}
nx                      OptIn

Windows Boot Loader
-------------------
identifier              {6dfc5cb0-f9ab-11da-ae34-df1fe3e76dcf}
device                  partition=I:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {572bcd55-ffa7-11d9-aae2-0007e994107d}
recoveryenabled         Yes
osdevice                partition=I:
systemroot              \Windows
resumeobject            {6dfc5cb1-f9ab-11da-ae34-df1fe3e76dcf}
nx                      OptIn

Windows Boot Manager
--------------------
identifier              {bootmgr}
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {default}
displayorder            {default}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {default}
device                  boot
path                    \windows\system32\boot\winload.exe
description             Windows Setup
locale                  en-US
inherit                 {bootloadersettings}
osdevice                boot
systemroot              \windows
detecthal               Yes
winpe                   Yes
ems                     Yes

```

---

### Post by meierfra. on 2009-01-30
Open a console  in Windows 7 as before and type:


```
bcdedit /store C:\boot\bcd /set {default} path \Windows\system32\winload.exe 
```

Reboot and hope for the best.

---

### Post by killergp123 on 2009-01-31
I still get the bar starting scrolling, then blue screen of death for a split second, followed by the reboot.

---

### Post by caljohnsmith on 2009-01-31
Meierfra and I talked it over some, and we think maybe the most promising solution to get Windows 7 booting independent of Vista would be if you can temporarily disconnect the Vista drive and make the Ubuntu/Windows 7 drive the master drive. Then boot your Windows 7 CD and do:
```
bootrec /rebuildbcd
```
And hopefully that will be all it takes to get Windows 7 booting independent of Vista from your Grub menu. But to make that work, before you disconnect sda and change the drives, please do:
```
sudo grub
grub> root (hd1,1)
grub> makeactive
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
Then change your drives, do the "bootrec /rebuildbcd", and try booting the Ubuntu/Windows 7 drive before hooking the Vista drive back up. If you get the Grub menu OK, choose the second Vista entry in your Grub menu, i.e. this one:
```
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```
In other words, since you will be booting the Ubuntu/Win7 sdb drive at that point, (hd0,1) will actually be Win7 and not Vista, so you can use that entry to boot Win7. Of course once you get Win7 booting successfully from Grub without the Vista drive connected, it will be safe to reconnect the Vista drive again and go back to your original configuration. Let us know how it goes or if you run into problems.

---

### Post by killergp123 on 2009-01-31
I don't want to take the laptop apart again to get to the hard drive spots, so I will just deal with the second menu, thanks for all the help though.

---

### Post by meierfra. on 2009-02-01
I did some testing and was able to recreate  your symptoms:  Short blue screen of death followed by rebooting.  So I believe that  your problem is  caused by 

> detecthal        Yes
winpe                   Yes
ems                     Yes

So lets see what happens if you remove those entries from the bcd.
Open a console in Windows 7 and type:



```
bcdedit /store C:\boot\bcd /deletevalue  {default} detecthal 

bcdedit /store C:\boot\bcd /deletevalue  {default} winpe

bcdedit /store C:\boot\bcd /deletevalue  {default} ems

```

---

### Post by killergp123 on 2009-02-01
Yay windows 7 boots from grub menu now.  Any idea how to get rid of the boot menu when you select vista?  I am going to search google for that, and will post back here if I fixed it myself, but if you know how please post and let me know.  Thanks again for all the help so far. :)

EDIT: I found out what I had to do, just went into startup/recovery options in vista and made vista primary operating system and unticked show OS menu at startup.  Now I am just going to make the grub screen look cleaner and more organized.  Thanks again for all your help caljohnsmith and meierfra., couldn't have done it without you both.

---

### Post by meierfra. on 2009-02-01
> windows 7 boots from grub menu now

Good news.  It seems  that the  BCD included in the Window 7 CD is different from the one on the Vista CD and requires a little more editing. I will update my HowTo accordingly.

---

