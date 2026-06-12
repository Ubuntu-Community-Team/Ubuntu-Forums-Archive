---
title: "dual boot Laptop trouble booting Vista Business"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by IQRules on 2009-03-27
I installed Ubuntu first, then Vista 2nd.
So the Vista overwrote the boot sector.
I was able to recover with Ubuntu 8.10 DVD and booted up Ubuntu.

The problem is I can't boot Vista now.

# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
# savedefault
makeactive
chainloader	+1

root@linux64:/boot/grub# fdisk -l /dev/sda

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7062b4db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5219    41921586    7  HPFS/NTFS
/dev/sda2   *        5220        5255      289170   83  Linux
/dev/sda3            5463       30401   200322517+   5  Extended
/dev/sda4            5256        5291      289170   83  Linux

/dev/sda2 is the /boot partition.
Any idea to make Vista bootable?

Thanks

---

### Post by Mark Phelps on 2009-03-28
You said /sda2 is the boot partition, but Vista can't boot from a Linux partition; it has to boot from an NTFS partition.

I presume when you "fixed" the Linux boot, you wrote GRUB to the MBR, right?

I've got a similar arrangement (Vista + Ubuntu) on a laptop and your menu.lst entries match mine -- and mine work OK.

You didn't say what happens when you attempt to boot Vista, but the only way to repair a Vista boot problem is to boot from a Vista DVD, or from a recovery CD, and run startup repair.

If you don't have a Vista DVD, go to the Neosmart Forums.  They have a downloadable Vista recovery CD image you can download through torrents.

---

### Post by IQRules on 2009-03-29
I have this setup, sorry not /dev/sda2 here.

$ df -k .
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4               279999     42545    222996  17% /boot

I did "fixed" the Linux boot, with GRUB to the MBR.

When I choose to boot Vista, I got $5$5, then hangs.
I do have Vista DVD here, so I do not need neosmart, is it?

---

### Post by mhgsys on 2009-03-29
try:
```

title Windows Vista/Longhorn (loader)
root (hd0,1)
makeactive
chainloader +1

```

---

### Post by IQRules on 2009-03-29
Now I got this,

"Error 13: Invalid or unsupported executable format"

Should I use Vista DVD and run fixmbr?
I am thinking reinstall Vista Home again. If I do this way, do I need Ubuntu DVD and run grub-install later?

---

### Post by merquis on 2009-03-29
i am new to all this, but i also had many problems installing a dual ubuntu/vista system.

I sorted it by installing vista first and then ubuntu, i don't know if that helps but i thought id post anyway :)

---

### Post by Mark Phelps on 2009-03-30
Using (hd0,1) is going to force Vista to try to boot from the second partition -- which is Ubuntu and won't work -- as you found out.

The entry (hd0,0) is the correct one,  Don't know why that doesn't work.

If you're going to reinstall, would be best to do Vista first, Ubuntu second -- and have the first partition be Vista, not Ubuntu.

Ubuntu should detect Vista when you install it and automatically create a stanza in menu.lst for it.

---

### Post by IQRules on 2009-03-30
I wish I can totally avoid re-install Ubuntu 8.10 here.
Is it possible just reload Vista and fix grub with grub-install?

---

### Post by Mark Phelps on 2009-03-30
> **IQRules said:**
> I wish I can totally avoid re-install Ubuntu 8.10 here.
Is it possible just reload Vista and fix grub with grub-install?

Thought you said Vista won't boot.  I'm getting the impression that Vista never booted? Is that correct?  If so, it's unlikely that you can fix the Vista boot problem with GRUB because GRUB only invokes the Vista boot loader.  The info you had in your menu.lst stanza for Vista looked correct.

If Vista won't boot, you have to fix that by running Startup Repair booting from the Vista DVD.

We're going in circles here ... If the Vista repair doesn't work because it can't write the boot loader files to the Ext3 partition, we're back where we started.

---

### Post by IQRules on 2009-03-30
Here is what I did last month
1. install 32-bit 8.10 with /boot in /dev/sda2
2. install Vista OS; Vista works just fine
3. wipe out /dev/sda2, and recreate /dev/sda4 as /boot
4. install 8.10 64-bit
5. trouble begins

---

### Post by Mark Phelps on 2009-03-31
> **IQRules said:**
> Here is what I did last month
1. install 32-bit 8.10 with /boot in /dev/sda2
2. install Vista OS; Vista works just fine
3. wipe out /dev/sda2, and recreate /dev/sda4 as /boot
4. install 8.10 64-bit
5. trouble begins

Ok, so Vista booted OK after the install, and so did Ubuntu.

And, sda4 is NOW the boot partition for Linux. Run Partition Editor in Ubuntu and see what flags are set for sda2 and sda4.  From Fdisk, it looks like sda2 has the boot flag set.

If you can mount your Vista OS partition (Use Places and double-click the Vista icon), look for a directory "boot" in sda1, and in that directory, look for a "BCD" program. Just look, don't change anything. If those are  there (which I suspect), it means that Vista DID write the boot loader files to its own partition (which it probably did because it couldn't write them to sda1).

---

### Post by meierfra. on 2009-04-01
> When I choose to boot Vista, I got $5$5, then hangs

Very strange.  Does it looks like Vista is starting to boot?  Or does it hang immediately?

In order to get a clearer picture of your setup, I suggest to boot into  
Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by IQRules on 2009-04-06
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7062b4db

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    83,843,234    83,843,172   7 HPFS/NTFS
/dev/sda2    *     83,843,235    84,421,574       578,340  83 Linux
/dev/sda3          87,747,030   488,392,064   400,645,035   5 Extended
/dev/sda5          87,747,093   107,282,069    19,534,977  83 Linux
/dev/sda6         107,282,133   165,871,124    58,588,992  83 Linux
/dev/sda7         165,871,188   177,582,509    11,711,322  82 Linux swap / Solaris
/dev/sda8         177,582,573   236,171,564    58,588,992  83 Linux
/dev/sda9         236,171,628   255,706,604    19,534,977  83 Linux
/dev/sda10        255,706,668   276,687,494    20,980,827  83 Linux
/dev/sda11        276,687,558   488,392,064   211,704,507  83 Linux
/dev/sda4          84,421,575    84,999,914       578,340  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="829844BB9844B009" LABEL="Local Disk" TYPE="ntfs" 
/dev/sda2: UUID="180901e7-3d94-48c8-823c-4dc70398d95b" TYPE="ext3" 
/dev/sda4: UUID="cf5b554e-e9c5-49cd-8660-a467c787ba00" TYPE="ext3" 
/dev/sda5: UUID="80020093-9ef3-4c28-9bb1-e4e7edeb7afb" TYPE="ext3" 
/dev/sda6: UUID="d44849e2-85b4-4116-8812-62d6a1560c5e" TYPE="ext3" 
/dev/sda7: UUID="b535c6f3-7b74-487a-bde1-42e3168b132a" TYPE="swap" 
/dev/sda8: UUID="cb413b57-fb11-445d-a3ed-d5da4099c646" TYPE="ext3" 
/dev/sda9: UUID="23b45f7a-7b36-40e3-88b7-288fe2f06ef0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="b1a9d02c-235e-4f27-9726-dc7d246e799b" TYPE="ext3" 
/dev/sda11: UUID="bb50d685-ac24-4ba9-aaa8-5edd45ae9921" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda10 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda4 on /boot type ext3 (rw,relatime)
/dev/sda6 on /home type ext3 (rw,relatime)
/dev/sda8 on /opt type ext3 (rw,relatime)
/dev/sda11 on /data type ext3 (rw,relatime)
/dev/sda5 on /32bitroot type ext3 (rw,relatime)
/dev/sda2 on /srv type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dba/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dba)


=================== sda2: Location of files loaded by Grub: ===================


  43.1GB: grub/stage2
  42.9GB: initrd.img-2.6.27-11-generic
  42.9GB: initrd.img-2.6.27-7-generic
  42.9GB: vmlinuz-2.6.27-11-generic
  42.9GB: vmlinuz-2.6.27-7-generic

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=80020093-9ef3-4c28-9bb1-e4e7edeb7afb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=96ec90ee-65bc-4c7d-ad28-8df2a6c8f2d7 /boot           ext3    relatime        0       2
# /dev/sda10
UUID=f163762d-faec-491f-a1ef-e9b7174ff68a /data           ext3    relatime        0       2
# /dev/sda6
UUID=d44849e2-85b4-4116-8812-62d6a1560c5e /home           ext3    relatime        0       2
# /dev/sda8
UUID=cb413b57-fb11-445d-a3ed-d5da4099c646 /opt            ext3    relatime        0       2
# /dev/sda9
UUID=23b45f7a-7b36-40e3-88b7-288fe2f06ef0 /usr/local      ext3    relatime        0       2
# /dev/sda7
UUID=b535c6f3-7b74-487a-bde1-42e3168b132a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 117.2GB: boot/grub/stage2
 117.2GB: boot/initrd.img-2.6.27-11-generic
 117.2GB: boot/initrd.img-2.6.27-7-generic
 117.2GB: boot/vmlinuz-2.6.27-11-generic
 117.2GB: boot/vmlinuz-2.6.27-7-generic

========================== sda10/boot/grub/menu.lst: ==========================

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
# kopt=root=UUID=b1a9d02c-235e-4f27-9726-dc7d246e799b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=b1a9d02c-235e-4f27-9726-dc7d246e799b ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=b1a9d02c-235e-4f27-9726-dc7d246e799b ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,3)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=b1a9d02c-235e-4f27-9726-dc7d246e799b ro quiet splash 
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=b1a9d02c-235e-4f27-9726-dc7d246e799b ro  single
initrd		/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
# savedefault
makeactive
chainloader	+1


=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=b1a9d02c-235e-4f27-9726-dc7d246e799b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=cf5b554e-e9c5-49cd-8660-a467c787ba00 /boot           ext3    relatime        0       2
# /dev/sda6
UUID=d44849e2-85b4-4116-8812-62d6a1560c5e /home           ext3    relatime        0       2
/dev/sda8 /opt           ext3    relatime        0       2
/dev/sda11  /data           ext3    relatime        0       2
/dev/sda5  /32bitroot           ext3    relatime        0       2
# /dev/sda2
UUID=180901e7-3d94-48c8-823c-4dc70398d95b /srv            ext3    relatime        0       2
# /dev/sda7
UUID=b535c6f3-7b74-487a-bde1-42e3168b132a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
### 
/dev/sda1 sda1 ntfs-3g force 0 0

=================== sda10: Location of files loaded by Grub: ===================


 131.1GB: boot/grub/menu.lst
 131.2GB: boot/grub/stage2
 130.9GB: boot/initrd.img-2.6.24-23-generic
 130.9GB: boot/initrd.img-2.6.24-23-generic.bak
 130.9GB: boot/initrd.img-2.6.27-11-generic
 130.9GB: boot/vmlinuz-2.6.24-23-generic
 130.9GB: boot/vmlinuz-2.6.27-11-generic
 130.9GB: initrd.img
 130.9GB: initrd.img.old
 130.9GB: vmlinuz
 130.9GB: vmlinuz.old

============================= sda4/grub/menu.lst: =============================

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
# kopt=root=UUID=b1a9d02c-235e-4f27-9726-dc7d246e799b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=b1a9d02c-235e-4f27-9726-dc7d246e799b ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=b1a9d02c-235e-4f27-9726-dc7d246e799b ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,3)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=b1a9d02c-235e-4f27-9726-dc7d246e799b ro quiet splash 
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=b1a9d02c-235e-4f27-9726-dc7d246e799b ro  single
initrd		/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
# savedefault
makeactive
chainloader	+1


=================== sda4: Location of files loaded by Grub: ===================


  43.5GB: grub/menu.lst
  43.5GB: grub/stage2
  43.2GB: initrd.img-2.6.24-23-generic
  43.2GB: initrd.img-2.6.24-23-generic.bak
  43.2GB: initrd.img-2.6.27-11-generic
  43.2GB: vmlinuz-2.6.24-23-generic
  43.2GB: vmlinuz-2.6.27-11-generic
=============================== StdErr Messages: ===============================

sed: can't read sda9/etc/issue: No such file or directory
```

And no files under Vista c:/boot/ subdir.

/32bitroot# find . -name BCD\* -print
root@:/32bitroot#

---

### Post by meierfra. on 2009-04-06
> 
sda1: 
    Boot sector type:  Windows XP


This is your problem.  You also have the XP boot files on the vista partition.  Did you try to fix your booting problem with an XP CD?
 
Try this
[B]
Step 1[/B]  Fix menu.lst

Use 

title Windows Vista/Longhorn (loader)
rootnoverify		(hd0,0)
chainloader	+1

for your Vista item in  menu.lst

**Step 2**  Put the boot flag on the Vista partition.

```
sudo sfdisk -A1 /dev/sda
```
(the "1" after -A is the number one)

[B]
Step 3[/B]  Fix the boot sector  of your Vista partition:

Boot from the Vista DVD, select "Repair Computer" and then "command line".

Type 

```
bootrec /fixboot
```

Reboot and see whether you can boot into Vista

[B]If  this did not work:

[/B]
**Step 4**  Run Vista Start Up Repair.

Boot from the Vista DVD, select "Repair Computer"  and then "Start Up Repair.


If this still did not work, report any error messages you got.

---

### Post by IQRules on 2009-04-13
Thanks to meierfra, I fixed it finally. Good part is no need to run grub install at all.
Good job.

---

### Post by meierfra. on 2009-04-13
> I fixed it finally.
Great, have fun with Vista and Ubuntu.

---

