---
title: "Windows XP frozen splash screen (Dual boot ubuntu and XP)"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by skyfuzz on 2009-09-11
I am currently dual booting Ubuntu 9.04 and Windows XP. When I select the Windows XP option from my GRUB, it loads windows but as soon as the blue screen with the small centered Windows XP logo appears, the computer won't move past that point and I have to hard restart the computer. 

Ubuntu 9.04 was installed first and I ran it for awhile by itself. Then, I installed Windows XP using the guide from google: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

After successfully using Windows XP by itself, I went and used the Ubuntu Live CD to restore the GRUB and access my Ubuntu partition again. Only after that step has the Windows XP partition been acting strangely.

Any help is appreciated!


Here is the related menu.lst portion and fdisk -l output:

## ## End Default Options ##

title Windows XP
root (hd0,2)
makeactive
chainloader +1 

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		486430b2-32a2-4fdd-b855-77c2e457f30a
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=486430b2-32a2-4fdd-b855-77c2e457f30a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		486430b2-32a2-4fdd-b855-77c2e457f30a
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=486430b2-32a2-4fdd-b855-77c2e457f30a ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		486430b2-32a2-4fdd-b855-77c2e457f30a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

------------------------------------------------------------------------

fdisk-l output:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1581    12699351   83  Linux
/dev/sda2            1582       19187   141420195   83  Linux
/dev/sda3   *       19188       24320    41230822+   7  HPFS/NTFS
/dev/sda4           24321       24321        8032+  82  Linux swap / Solaris



ALSO--> Here is the boot info from a boot_info_script032.sh file:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 11239487 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /menu.lst

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38d70090

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,398,764    25,398,702  83 Linux
/dev/sda2          25,398,765   308,239,154   282,840,390  83 Linux
/dev/sda3    *    308,239,155   390,700,799    82,461,645   7 HPFS/NTFS
/dev/sda4         390,700,800   390,716,864        16,065  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="486430b2-32a2-4fdd-b855-77c2e457f30a" TYPE="ext3" 
/dev/sda2: UUID="11a88db4-68e9-479d-afab-725d1f03f5ee" TYPE="ext3" 
/dev/sda3: UUID="28E05760E0573374" TYPE="ntfs" 
/dev/sda4: UUID="c5111599-c799-4401-bfcb-0d7d55e62a08" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /home type ext3 (rw,relatime)
none on /proc/bus/usb type usbfs (rw,devgid=1001,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sky/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sky)


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
timeout		3

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
# kopt=root=UUID=486430b2-32a2-4fdd-b855-77c2e457f30a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=486430b2-32a2-4fdd-b855-77c2e457f30a

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

title Windows XP
root (hd0,2)
makeactive
chainloader +1 

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		486430b2-32a2-4fdd-b855-77c2e457f30a
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=486430b2-32a2-4fdd-b855-77c2e457f30a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		486430b2-32a2-4fdd-b855-77c2e457f30a
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=486430b2-32a2-4fdd-b855-77c2e457f30a ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		486430b2-32a2-4fdd-b855-77c2e457f30a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=486430b2-32a2-4fdd-b855-77c2e457f30a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=11a88db4-68e9-479d-afab-725d1f03f5ee /home           ext3    relatime        0       2
# /dev/sda5
UUID=ae7182a3-89da-4cf4-adf1-dd5a1b92101a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
none /proc/bus/usb usbfs devgid=126,devmode=664 0 0

=================== sda1: Location of files loaded by Grub: ===================


   5.6GB: boot/grub/menu.lst
   5.7GB: boot/grub/stage2
   5.7GB: boot/initrd.img-2.6.28-11-generic
   5.7GB: boot/initrd.img-2.6.28-13-generic
   5.8GB: boot/initrd.img-2.6.28-14-generic
   5.8GB: boot/initrd.img-2.6.28-15-generic
   5.6GB: boot/vmlinuz-2.6.28-11-generic
   5.7GB: boot/vmlinuz-2.6.28-13-generic
   5.7GB: boot/vmlinuz-2.6.28-14-generic
   2.3GB: boot/vmlinuz-2.6.28-15-generic
   5.8GB: initrd.img
   5.8GB: initrd.img.old
   2.3GB: vmlinuz
   5.7GB: vmlinuz.old

================================ sda2/menu.lst: ================================

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
timeout		3

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
# kopt=root=UUID=486430b2-32a2-4fdd-b855-77c2e457f30a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=486430b2-32a2-4fdd-b855-77c2e457f30a

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		486430b2-32a2-4fdd-b855-77c2e457f30a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=486430b2-32a2-4fdd-b855-77c2e457f30a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		486430b2-32a2-4fdd-b855-77c2e457f30a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=486430b2-32a2-4fdd-b855-77c2e457f30a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		486430b2-32a2-4fdd-b855-77c2e457f30a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=486430b2-32a2-4fdd-b855-77c2e457f30a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		486430b2-32a2-4fdd-b855-77c2e457f30a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=486430b2-32a2-4fdd-b855-77c2e457f30a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		486430b2-32a2-4fdd-b855-77c2e457f30a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda2: Location of files loaded by Grub: ===================


  13.0GB: menu.lst

================================ sda3/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

---

### Post by briantoumbs on 2009-09-11
Mine has been doing the same, think its just windows being windows seems to work when I restart again.

---

### Post by skyfuzz on 2009-09-11
> Mine has been doing the same, think its just windows being windows seems to work when I restart again.

How long did you wait before restarting the computer when it froze on the splash screen?

---

### Post by briantoumbs on 2009-09-11
Not to long I can normally tell when it isn't going to work. I get a tad impatient with it. 

If your having a similar problem I wonder if it does have something to do with 9.04 an Xp dual boot, never happened till recently.

---

### Post by Finalfantasykid on 2009-09-11
Ok I think I had the same problem as you.

I'm guessing when you partitioned your harddrive, you added the linux partition(s) onto the left side of your windows ntfs one.  If that is the case, I think you can fix this problem by going to the Boot.INI file on your windows partition(just mount that drive and edit the file).  The file should be located at  C:\BOOT.INI (or in Ubuntu it is probably at something like this /media/disk/BOOT.INI)

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022) There is a tutorial on how to edit the boot.ini file, and the part you are probably interested in is this... 

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Windows XP Professional" /fastdetect

I think you want the partition() to have 3, since that is where yours is located.  If that does not work, you might need to change the number to something else.

EDIT:  Ok I totally missed the bit at the end where you posted your boot.ini.  It seems you already have it set to partition(3).  I'm pretty sure thats the partition you want, so that must not be the problem.

Have you tried booting into Windows XP (Safe Mode)?

---

### Post by presence1960 on 2009-09-11
I would take your windows entry out from the Ubuntu entries and place it below this line:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

title         Windows XP
rootnoverify  (hd0,2)
chainloader   +1


```

I seriously doubt this is why windows will not boot. But try it anyway because that is where the windows entry traditionally goes in menu.lst
make changes also, you don't need makeactive or savedefault on the 3rd line. Change root to rootnoverify.

If that does not work I would try to fixboot & fixmbr from the windows install cd recovery console then see if windows boots. Then restore GRUB to MBR. It is a two step process.

1. Boot off the windows install CD and do [this]("http://ubuntuforums.org/showthread.php?t=1014708") (follow instructions for XP). When complete reboot without Cd and see if you boot right into windows. If you do go to #2 below. if not you have a problem with your windows installation.

2. Boot from the ubuntu Live Cd and do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.

```

reboot and try windows from GRUB.

---

### Post by Sin@Sin-Sacrifice on 2009-09-11
It's XP 64 but is set up like presence1960 says to have it and never fails. In fact I use to triple boot Ubuntu, XP, and Backtrack and was flawless every time.

---

### Post by skyfuzz on 2009-09-11
> **presence1960 said:**
> I would take your windows entry out from the Ubuntu entries and place it below this line:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

title         Windows XP
rootnoverify  (hd0,2)
chainloader   +1


```

I seriously doubt this is why windows will not boot. But try it anyway because that is where the windows entry traditionally goes in menu.lst
make changes also, you don't need makeactive or savedefault on the 3rd line. Change root to rootnoverify.

If that does not work I would try to fixboot & fixmbr from the windows install cd recovery console then see if windows boots. Then restore GRUB to MBR. It is a two step process.

1. Boot off the windows install CD and do [this]("http://ubuntuforums.org/showthread.php?t=1014708") (follow instructions for XP). When complete reboot without Cd and see if you boot right into windows. If you do go to #2 below. if not you have a problem with your windows installation.

2. Boot from the ubuntu Live Cd and do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.

```

reboot and try windows from GRUB.

Ok I'll try this right now...

---

