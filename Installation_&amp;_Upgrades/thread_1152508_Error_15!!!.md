---
title: "Error 15!!!"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by roachman5000 on 2009-05-07
I'm somewhat of a partial n00b when it comes to Ubuntu, so please bear with me...

I updated to Jaunty 9.04 the other week, and then a couple of days ago my wi-fi stopped working.  Even worse, when I rebooted my computer today all I got is 

ERROR 15:  File not found (it's on GRUB).

I can boot from a USB drive, but when I go in and try to back up my information on an external hard drive to do a re-install, it won't let me.  

If I had a Ubuntu-logo-style-Bat-symbol to call for help, I would fire it up right about...now.  PLEASE HELP!!!

Much appreciated, in advance.

---

### Post by pastalavista on 2009-05-07
Haha Ubuntu-Man to the rescue! Boot from the CD and open a terminal. Type ```
sudo grub
```
At the grub prompt enter these commands:


find /boot/grub/stage1

root (hd?,?)

setup (hd0)

quit

Then reboot from the HD. Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell where grub's files are. So you find the files and then you tell grub where to locate the files it will need for setup.

So root (hd?,?) tells grub it's files are on that partition. Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition, grub will use the mbr. hd0 is the grub label for the first drive's mbr.

---

### Post by roachman5000 on 2009-05-07
Thank you for the quick response.

I followed your instructions, but when I rebooted from the HD I still got the ERROR 15 message.

If it doesn't work out, is there a way to recover my data off of the HD when booting from the CD

---

### Post by pastalavista on 2009-05-07
Yes there is. Just hit alt-f2 and type gksu nautilus. This will give you a root file browser and permission to copy and paste any files just like you were in your own home directory.

About restoring grub, if you can, you might try downloading and burning a [Super Grub Disk]("http://www.supergrubdisk.org"). It's saved my butt a couple of times.

---

### Post by caljohnsmith on 2009-05-08
If you haven't all ready reinstalled Ubuntu and would still like help resolving your Grub problem, roachman5000, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by raymondh on 2009-05-08
roachman ... run the boot info script as cal suggests ... it is so valuable and can show what you have going.

Hi cal (sorry for this hijack) ... can you make that script and subsequent instructions a stickie?

Best.

---

### Post by caljohnsmith on 2009-05-08
> **raymondhenson said:**
> 
Hi cal (sorry for this hijack) ... can you make that script and subsequent instructions a stickie?

I'll have to check with the admins and other moderators for their opinions, but I think that might be a good idea. :)

---

### Post by roachman5000 on 2009-05-08
I haven't done a re-install yet.  Here is what came up in RESULTS.TXT
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 266551359 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   299,805,029   299,804,967  83 Linux
/dev/sda2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sda5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="805fe6b8-2479-46fe-959e-235e3f9a4054" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="054663d4-b091-49a8-8d06-ff8de1d4f972" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


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
default		2

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=805fe6b8-2479-46fe-959e-235e3f9a4054

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=054663d4-b091-49a8-8d06-ff8de1d4f972 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 136.4GB: boot/grub/menu.lst
 136.4GB: boot/grub/stage2
 136.3GB: boot/initrd.img-2.6.28-10-generic
 136.3GB: boot/initrd.img-2.6.28-11-generic
  21.6GB: boot/initrd.img-2.6.28-11-server
  21.6GB: boot/initrd.img-2.6.28-12-generic
  21.7GB: boot/initrd.img-2.6.28-3-rt
 136.3GB: boot/initrd.img-2.6.28-9-generic
 136.3GB: boot/vmlinuz-2.6.28-10-generic
 136.2GB: boot/vmlinuz-2.6.28-11-generic
  21.6GB: boot/vmlinuz-2.6.28-11-server
  21.7GB: boot/vmlinuz-2.6.28-12-generic
  21.6GB: boot/vmlinuz-2.6.28-3-rt
 136.3GB: boot/vmlinuz-2.6.28-9-generic
  21.7GB: initrd.img
  21.6GB: initrd.img.old
  21.6GB: vmlinuz
  21.6GB: vmlinuz.old
```

This is way over my head, so it goes without saying that I really appreciate the help.

---

### Post by caljohnsmith on 2009-05-08
OK, I believe I found your problem; for some reason your Grub's menu.lst did not get updated with the newly installed kernels that came with Jaunty, because your current menu.lst refers to older kernels that are no longer installed. To correct the problem, how about doing:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
update-grub
exit
gksudo gedit /mnt/boot/grub/menu.lst
```
When that last command pulls up your menu.lst, make sure the "hiddenmenu" line near the top of the file has a pound/hash # in front of it to comment it out, so it should be:
```
#hiddenmenu
```
Also, please post the new contents of the menu.lst. After that reboot and let me know how far you get. We can work from there.

John

---

### Post by roachman5000 on 2009-05-08
Drat!  I'm still getting the Error 15.  Here's the output:
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
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=805fe6b8-2479-46fe-959e-235e3f9a4054

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by roachman5000 on 2009-05-08
Also, I'm using a 7.10 Boot Disc.  Would that cause any issues?

---

### Post by caljohnsmith on 2009-05-08
Did the update-grub command that you ran complete without errors? I forgot to ask you to post the output of those commands. For some reason your menu.lst still doesn't have the new kernels. How about instead modifying your menu.lst manually, so instead try:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
Change the first Ubuntu entry as shown in red:
```
title		Ubuntu 8.10, kernel 2.6.[COLOR="Red"]28-12[/COLOR]-generic
uuid		805fe6b8-2479-46fe-959e-235e3f9a4054
kernel		/boot/vmlinuz-2.6.[COLOR="Red"]28-12[/COLOR]-generic root=UUID=805fe6b8-2479-46fe-959e-235e3f9a4054 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.[COLOR="Red"]28-12[/COLOR]-generic
quiet
```
Then reboot and try the new 2.6.28-12 kernel from your Grub menu, and let me know how far you get. We can work from there.

John

---

### Post by roachman5000 on 2009-05-08
[SIZE="6"]SUCCESS!!![/SIZE]

Thanks so much to all of you.  You are lifesavers.

Long live Ubuntu Forums!!!

Joe

---

