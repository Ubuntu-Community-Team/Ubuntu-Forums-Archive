---
title: "GRUB killed Vista"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by looter211 on 2009-02-08
First let me say I know there is a great deal of  discussionn related to similar issues, alot of which I have read.  But there has been nothing that  relates directly to my problem so forgive me if any answers to my problem are redundant.  

Now my problem,  I have had a dual boot configuration consisting of Vista and XP for some time now.  XP   was installed first on the first  IDE channel.  I then purchased an additional hard drive for the dual boot to load vista onto.  I used the Vista Boot loader to switch between OS and I manually edited the BCD so that it would reflect the XP install.  Having pretty much abandoned using XP I decided that I was going to put Ubuntu on that first channel's hard drive, thus replacing XP.  I backed up all my stuff and proceeded to install Ubuntu from the live CD.  Everything seemed to go pretty smoothly as I installed GRUB to the hd0 partition and have been messing with it for most of the evening.  Upon a restart I tried loading Vista and of course this is where my problem begins. 

GRUB loads Ubuntu just fine and I can even mount the Vista hd and see all my files.  The problem is when I select the Vista option from GRUB it takes me  to the Vista Boot loader screen where I see two options, one for the Vista install and one for the old XP install.  If I click on the XP option I get nothing, it just goes to a black screen and then does nothing.  If I click on the Vista option I get a "Windows failed to start"  something related to winload.exe missing.   

What I have tried so far:  I ran the Vista Recovery DVD twice and no luck.  I was hesitant to do any BCD editing from the command prompt as I don't want to screw up the GRUB configuration.  I also tried switching the boot order of the hard drives.  None of this has changed anything.  I really need to be able to boot back into that Vista install.  It would be a huge hassole to have to reinstall.  I really would like to use GRUB as my bootloader as well but I'm desperate at this point.  



Here is my GRUB config

```
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
# kopt=root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8c83f501-9af2-4930-bdd5-da97c5fe3cdd

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
uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista Business (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```


Please some point me in the right direction as to what my options are.  I am really hurtin here.  Thanks in advance.

---

### Post by caljohnsmith on 2009-02-08
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Vista booting problem might be.

---

### Post by looter211 on 2009-02-08
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14e2f572

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   308,030,309   308,030,247  83 Linux
/dev/sda2         308,030,310   320,159,384    12,129,075   5 Extended
/dev/sda5         308,030,373   320,159,384    12,129,012  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xec3b14ae

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8c83f501-9af2-4930-bdd5-da97c5fe3cdd" TYPE="ext3" 
/dev/sda5: UUID="cc4cdfe7-9cf1-42a0-b694-a9282387ffee" TYPE="swap" 
/dev/sdb1: UUID="EC3CA2C93CA28E60" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/looter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=looter)

=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8c83f501-9af2-4930-bdd5-da97c5fe3cdd

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
uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista Business (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=cc4cdfe7-9cf1-42a0-b694-a9282387ffee none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  87.8GB: boot/grub/menu.lst
  87.8GB: boot/grub/stage2
  87.8GB: boot/initrd.img-2.6.27-11-generic
  87.8GB: boot/initrd.img-2.6.27-7-generic
  87.8GB: boot/vmlinuz-2.6.27-11-generic
  87.8GB: boot/vmlinuz-2.6.27-7-generic
  87.8GB: initrd.img
  87.8GB: initrd.img.old
  87.8GB: vmlinuz
  87.8GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


```

---

### Post by caljohnsmith on 2009-02-08
OK, how about booting your Vista Recovery DVD, go to the command line, and do:
```
chkdsk /r
bootrec /rebuildbcd
```
And run the chkdsk command as many times as it takes until it reports no errors. Also, let me know if you get any errors when running the "bootrec /rebuildbcd" command, but if not, try booting Vista again from Grub and let me know how far you get. We can work from there if you want.

---

### Post by looter211 on 2009-02-08
Ok,   wow that took awhile.  I ran check disk and it completed without an apparent errors.  I am not sure where the log file is so if you need to see it please point me to its location and I'll post that.  

When I ran bootrec /rebuildbcd it said it successfully scanned the windows installations and showed one option, [1] C:\Windows, asking if I wanted to add  to the boot list. I hit Yes and it said the "Volume does not contain a recognized file system"

I rebooted and tried to load Vista and nothing had change. Still loads the Vista boot manager showing Vista and XP and then exhibits the same behavior when I try to load vista from there.  Also, when I booted back into Ubuntu I noticed an icon on the desktop labeled UDF Volume.  It contains  some boot related  files.  Was not there before.

I'll  sit tight and wait for further instruction

---

### Post by caljohnsmith on 2009-02-08
OK, how about booting your Vista DVD again, go to the command line, and try:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
Find which is your Vista partition drive letter, and then do:
```
bcdedit /store C:\boot\bcd /set {default} osdevice boot
bcdedit /store C:\boot\bcd /set {default} device boot
bcdedit /store C:\boot\bcd /set {bootmgr} device boot
bcdedit /store C:\boot\bcd /set {memdiag} device boot
```
But replace "C" with whichever is your Vista partition. Then reboot, and please let me know how far you get when booting Vista.

---

### Post by dougalkerr on 2009-02-08
I have been following this thread with interest. I do not want to advize you to do anything that will put you off in another direction but, when I had lost grub and my Vista dual system because of losing Grub I got some advice about how Supergrub should get things working again and it did.
There are a number of options to choose from in Supergrub and some only available if you go through the help pages and then return to the options from the help pages.
Now I am not saying it WILL help you but it might.

Also, I believe you may have a major problem doing much with your recovery dusc for Vista because the recovery discs I have for Vista never get the system going again. Only a real OEM version of Vista for a fresh install has done anything for me. If I have problems with Vista booting after installing Ubuntu then the first thing I do is to load the Vista disc and reboot, opting to repair Vista when I get the chance and this fixes the Vista bootloader which grub overwrites (atleast that it what I have been told) and then when you choose Vista from the menu it boots properly. The XP option on the menu can be scrubbed by going into 'Control Panel/System/Startup and Recovery' then 'Settings' then just (edit out) the XP entry.
Hope this helps...

---

### Post by dougalkerr on 2009-02-08
Sorry forgot to mention you need to download Supergrub and burn it to a small CD. An 8 cm size will do then if you need to use it boot the PC with the disc in the drive...

---

### Post by looter211 on 2009-02-08
Yep it worked.  Booted to the Vista boot manager where its still showing XP but I chose Vista and it then warned me like it had been improperly shut down and prompted me with some advanced startup items like safe mode, last known working config, etc.  I chose normal and it booted right in.

TO: dougalkker

Thank you for your insight as it is much appreicated.  In regards to your posts though, my trouble seems to have been with the Vista Boot manager not grub.  Although I'm not saying supergrub wouldn't or couldn't have helped I just want to be sure we are on the same track.  Also, I do have the OEM copy of Vista, its not just the recovery disc, just to clarify.  As of now I am booting back into vista after johns BCD editing commands.  Where to go from here? I'd love to be able to boot both from grub and ditch the Vista bootlaoder.  Eitehr way the most important thing is being able to boot into Vista, for now.

---

