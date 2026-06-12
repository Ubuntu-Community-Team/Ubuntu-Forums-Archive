---
title: "Windows won't boot after Ubuntu install"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by tformed on 2009-05-21
This is in continuation to thread: 

[http://ubuntuforums.org/showthread.php?p=7321662#post7321662](http://ubuntuforums.org/showthread.php?p=7321662#post7321662)

Hopefully someone out there has a solution for me. I have really been getting use to Ubuntu, I would hate to uninstall it (again) and just stick with Windows completely. Somehow I end up installing Ubuntu again, and always with some problem.

I have taken several steps to try and rectify the issue. When my laptop (Asus W3J) boots up and gets past the Asus logo, I am presented with the Grub menu.

I am able to boot up Ubuntu just fine, but when I go ahead and select Windows 7, the computer just restarts and brings me back to the Grub menu screen.

This is what I get when I type the following:                               sudo bash ~/Desktop/boot_info_script*.sh                      
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5335872d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   153,513,983   153,307,136   7 HPFS/NTFS
/dev/sda3         153,517,140   195,366,464    41,849,325   5 Extended
/dev/sda5         153,517,203   193,535,054    40,017,852  83 Linux
/dev/sda6         193,535,118   195,366,464     1,831,347  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3A1011231010E821" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="FC4822D748229086" TYPE="ntfs" 
/dev/sda5: UUID="7ef07a2a-9ad0-464b-9244-6568278fd13d" TYPE="ext3" 
/dev/sda6: UUID="70ea9fef-f247-405e-8550-66db0a8fb5a2" TYPE="swap" 

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
gvfs-fuse-daemon on /home/robert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robert)


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
# kopt=root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7ef07a2a-9ad0-464b-9244-6568278fd13d

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
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows 7 (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1


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
UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=70ea9fef-f247-405e-8550-66db0a8fb5a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  86.4GB: boot/grub/menu.lst
  86.4GB: boot/grub/stage2
  86.2GB: boot/initrd.img-2.6.28-11-generic
  86.3GB: boot/vmlinuz-2.6.28-11-generic
  86.2GB: initrd.img
  86.3GB: vmlinuz

```note: I am new to ubuntu and the terminal commands or how the file system works. 

Please help.

---

### Post by Bucky Ball on 2009-05-21
> /dev/sda1: UUID="3A1011231010E821" LABEL=**"System Reserved"** TYPE="ntfs"That seems odd, but maybe not. Windows install was running fine before installing Ubuntu? It was closed down properly, etc?

Apart from that, this:

```
title Windows 7 (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```Looks correct.

---

### Post by tformed on 2009-05-21
Yes, I created a fresh install of Windows 7, and when I was partitioning the drive for it, the system informed me that it needed to create a system reserve partition which is about 10mb I believe.

---

### Post by Bucky Ball on 2009-05-21
Well, maybe, just maybe, if that is at the first part of the disk before everything else, grub is hitting that instead of Windows or MBR and bouncing back. Better look into that. Just a guess. But you have your grub/menu.lst entry right.

hd 0,0 = sda1

Everything seems to be fine on the Linux side. That is really odd.

---

### Post by tformed on 2009-05-21
Currently it's like this:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows 7 (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1


what is weird, is that originally I had a vista install and it would do the same thing. The only time I manage to get it working correctly was when I let Window MBR take control of things, and setup EasyBCD. Ubuntu and Windows would load, but after I let Ubuntu update, it would never load again. So I took it off and installed Vista as the only OS.

---

### Post by Bucky Ball on 2009-05-21
> **tformed said:**
> Currently it's like this:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
**root**


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows 7 (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1




Ah! Get rid of the bit I have bolded out, **root**, just remove it.

It should look like this:

```


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows 7 (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1



```Give that a try and see what gives.

---

### Post by tformed on 2009-05-21
Ok, I gave it a try: 

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
# kopt=root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7ef07a2a-9ad0-464b-9244-6568278fd13d

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
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows 7 (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

```

You got my hopes up, lol.

I rebooted, and this time, Windows was listed right below the Ubuntu options and not separated like before. When I selected Windows, the laptop restarted and came back to the Grub Menu.

---

### Post by tformed on 2009-05-21
Is it possible to install a different bootloader? :S

I would install it on a VM, but that defeats the purpose of having Ubuntu for it's quick boot.

---

### Post by lindsay7 on 2009-05-21
I do know if this would do any good, but at this point you may want to just try it.

Type in the terminal "sudo apt-get install lilo" then "sudo lilo -M /dev/sda mbr"

This is another bootloader.

sda should be the same as hd0.

If you try this and it does not work. You may want to go back and set up your mbr with windows bootrec /fixboot.

---

### Post by V8pedals on 2009-05-21
Try to use this  program it's called super grub disk reasonably easy to use
hope it helps to solve your problem):P

[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by tformed on 2009-05-21
ok, I did and ran the following in the terminal
"Type in the terminal "sudo apt-get install lilo" then "sudo lilo -M /dev/sda mbr"". 
 
When I restarted Windows 7 boot up automatically, but there's no visible  bootloader, since it doesn't let me choose OS.

---

### Post by lindsay7 on 2009-05-21
Well we may be coming back to square one again, but the only thing I can think of is to try to load grub again.  Maybe using this bootloader will change something for the positive. Let me know how it turns out.

in the terminal type.

"sudo grub"

at the grub prompt, type

"find /boot/grub/stage2

this will return something like (hd0,4)

still at the grub prompt type the results of what you get above
as such

"root (hdx,y)" where x and y are what you got in the above
"setup (hd0)"
"quit"

reboot

---

### Post by tformed on 2009-05-21
ok I reinstalled grub and the same thing happens as before, the grub menu appears. If I choose Windows the system restarts, if I choose Ubuntu, the system boots Ubuntu just fine. 

:( 

I don't think it was meant to be.

---

### Post by lindsay7 on 2009-05-21
There has to be some small mistake in the grub file that is causing this.  Well you are now an expert at the grub file and mbr.  What I would do is format the Ubuntu partition and reinstall it. Hopefully that will set up a new grub file. If your mbr gets overwritten, at least you know how to get it back.

---

### Post by tformed on 2009-05-21
it pains me to say this, but I think I will just stick to Windows and run Ubuntu on a VM. :(

I've already done several Ubuntu installs, and have tried several distros (thinking it would matteR) in order to solve this issue but to no avail.

If I didn't need special windows app (like outlook for exchange, adobe software etc) I wouldn't mind sticking to Ubuntu as the main OS. 

I still have alot to learn about how the file system work in Ubuntu and etc. I thank you for your time Lindsay.

I'm sure I'll have the urge of installing Ubuntu once again in the near future, like always. haha ;)

---

