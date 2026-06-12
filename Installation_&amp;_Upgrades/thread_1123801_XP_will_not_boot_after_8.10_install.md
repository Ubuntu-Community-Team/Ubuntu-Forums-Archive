---
title: "XP will not boot after 8.10 install"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by ephonk on 2009-04-12
Trying to set up a dual XP/Ubuntu 8.10 boot.  I used the guided partition tool to give the ntfs/ext3 partitions 50% of the HD apiece.
The Ubuntu install goes well and runs perfectly.  However, XP will not boot up anymore.  It starts to, but a few seconds in the machine reboots and I'm back to the GRUB menu.  
What went wrong?

---

### Post by inobe on 2009-04-12
> What went wrong? 

gparted will resize the windows partition.

[>>>tutorial<<<]("http://www.youtube.com/watch?v=JBfl3oViny8&feature=related")

---

### Post by ephonk on 2009-04-12
Are you saying that I should let the guided partition tool pick it's own sizes for things and then resize them after the fact with gparted?  How will that fix the problem with GRUB booting the Windows partition?

I'm already using gparted to restore my system after a failed install...

---

### Post by meierfra. on 2009-04-12
In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by robinbj on 2009-04-12
maybe check you boot disk to see if XP is still there. If not, i would suggest wiping your entire HD and starting from anew and loading XP on and then using Wubi to install ubuntu. that worked best for me.

hope this helps
brad

---

### Post by ephonk on 2009-04-13
XP is still there...  If I wipe out the ubuntu install, and fixmbr from the XP recovery console it comes back fine.

I'm going to try the boot info script on a fresh install.  That looks pretty promising.

---

### Post by robinbj on 2009-04-13
Sounds good. Hope it works out for ya. Let us know how it goes.

Best of luck

brad

---

### Post by ephonk on 2009-04-13
Got back into it...  this time with a Kubuntu install.  Same problem:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8e9b8e9b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS
/dev/sda2         156,296,385   312,576,704   156,280,320   5 Extended
/dev/sda5         156,296,448   309,604,679   153,308,232  83 Linux
/dev/sda6         309,604,743   312,576,704     2,971,962  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D0BC882CBC880F62" TYPE="ntfs" 
/dev/sda5: UUID="25a7fb9f-f53b-4679-a132-0914f9991272" TYPE="ext3" 
/dev/sda6: UUID="4acfb6e7-5a27-4e0d-a126-3e3cedb20acf" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
tmpfs on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=0755)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


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
# kopt=root=UUID=25a7fb9f-f53b-4679-a132-0914f9991272 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=25a7fb9f-f53b-4679-a132-0914f9991272

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
uuid		25a7fb9f-f53b-4679-a132-0914f9991272
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=25a7fb9f-f53b-4679-a132-0914f9991272 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		25a7fb9f-f53b-4679-a132-0914f9991272
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=25a7fb9f-f53b-4679-a132-0914f9991272 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		25a7fb9f-f53b-4679-a132-0914f9991272
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=25a7fb9f-f53b-4679-a132-0914f9991272 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		25a7fb9f-f53b-4679-a132-0914f9991272
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=25a7fb9f-f53b-4679-a132-0914f9991272 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		25a7fb9f-f53b-4679-a132-0914f9991272
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=25a7fb9f-f53b-4679-a132-0914f9991272 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=4acfb6e7-5a27-4e0d-a126-3e3cedb20acf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  98.7GB: boot/grub/menu.lst
  98.7GB: boot/grub/stage2
  98.2GB: boot/initrd.img-2.6.27-11-generic
  98.2GB: boot/initrd.img-2.6.27-7-generic
  98.2GB: boot/vmlinuz-2.6.27-11-generic
  98.2GB: boot/vmlinuz-2.6.27-7-generic
  98.2GB: initrd.img
  98.2GB: initrd.img.old
  98.2GB: vmlinuz
  98.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by meierfra. on 2009-04-13
Everything seems to be configured correctly.  So this seems to be one of the rare cases where Grub is not able to chain load the Windows Boot loader. I recommend to add Ubuntu to the Windows boot loader:


**Step 1** Install Grub to the boot sector of the Ubuntu Partition:

Open a terminal in Ubuntu and type:

```
sudo grub

```
and at the grub prompt:



```
root (hd0,4)
setup (hd0,4)
quit
```

**Step 2 **Copy the Ubuntu boot sector to a file on your Windows partition:

```
sudo mount /dev/sda1 /mnt
sudo dd if=/dev/sda5 of=/mnt/ubuntu.bin  count=1
```

(be very careful with the "dd" command. If it runs for more than a couple of seconds press "Ctrl+C" to stop the process)

**Step 3 **Edit boot.ini:

```
sudo nano /mnt/boot.ini
```

(Do not use "gedit" in place of "nano": gedit does not handle "dos" files very well)

Add this to the end of the file (start a new line, but do not leave a blank line):

C:\ubuntu.bin="Ubuntu"

Follow the instructions on the bottom of the screen to save the file.

**Step 4 **Install a Windows style MBR

```
sudo apt-get install lilo
sudo lilo -M /dev/sda ext

```

Reboot and see whether you can boot into both OS's.


**Step 5** Edit menu.lst so that you don't have to go through two boot menus

In an Ubuntu terminal:


```
gksudo gedit /boot/grub/menu.lst

```
Change

timeout 10

to

timeout 3

and

#hiddenmenu

to

hiddenmenu.

Save the file and you should be all set.

---

### Post by ephonk on 2009-04-13
I followed these instructions and did indeed see the Windows boot manager with Ubuntu as a pick.  However, no joy.  When I pick Windows I get the same behaviour - it starts to boot, even getting so far as to ask me if I want safe mode or the last good configuration, but then shortly after that - reboot!

Once again, no problem at all getting into ubuntu.  If it weren't my wife's machine I'd ditch XP entirely here.

This was really an excellent approach, tho.  Don't see why it isn't working...  I wonder if there's some BIOS setting or anti-virus stuff that's intended to prevent meddling with the boot config.  Seems unlikely.

Thanx!

---

### Post by meierfra. on 2009-04-13
What exactly did you do the last time to fix Windows?  You said you run "fixmbr" and deleted Ubuntu. Anything else? Did you resize the Windows partition?

Anyway I suggest to boot from your Windows CD and run

```
fixmbr
fixboot
```

If this did not help,try

```
chkdsk /r
```
(also from the Window CD)

---

