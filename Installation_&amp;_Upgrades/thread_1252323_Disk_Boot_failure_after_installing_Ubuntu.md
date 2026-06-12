---
title: "Disk Boot failure after installing Ubuntu"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by EizoSiege on 2009-08-28
Hi, I am converting from Windows to Ubuntu. Well, after installing Ubuntu(Jaunte Jacklon) I restarted the pc and when it boots a message appears: "Disk Boot failure, Insert system disk and press enter" 
I have tried both Ubuntu and xUbuntu. Both with same result. I am running 2 SATA HDD's one is 1TB and one is 500GB. The 500GB is partioned into a 150GB local partition, and the rest of the 500GB is for storing. 

So I installed the ubuntu on the 150GB partition. Have you guys got any idea what is going wrong with my installation?

Thanks in advance for reply.

---

### Post by inobe on 2009-08-28
is onboard raid disabled and are the drives set to sata/ide ?

are you dualbooting ?

i would leave one of the two hard drives disconnected until things are up and going, in fact remove one of them now and test the ubuntu install.

---

### Post by EizoSiege on 2009-08-28
> **inobe said:**
> is onboard raid disabled and are the drives set to sata/ide ?

are you dualbooting ?

i would leave one of the two hard drives disconnected until things are up and going, in fact remove one of them now and test the ubuntu install.
Shall I unplugg the 1TB HDD? I am not duelbooting. The thing is that the 1TB HDD is full and is NTFS format and I don't want to format it. So I have made 2 Partitions out of the 500GB HDD and one of the partitions is NTFS and one of them I have made to EXT3. 
So what you are saying is that I should plug out the 1TB HDD and then just use the 500GB with 2 partitions?

btw, thanks for the reply.

---

### Post by inobe on 2009-08-28
the tb drive removed will help us rule out the problem, of course after plugging it in later' ubuntu will detect it.

at least if it's unplugged' you won't need worry of it getting formatted.

---

### Post by fela on 2009-08-28
1) Make sure your default boot device is the 500GB drive, and was when you installed Ubuntu.

2) Make sure grub is installed to the 500GB drive. If it was the deafult boot drive when you installed ubuntu, this would have happened automatically.

3) Make sure the ubuntu partition is at the beginning of the drive. In particular, make sure the /boot partition (by default the same one as the main one) is at the beginning of the drive, before instead of after the NTFS partition. This is because some computers can only boot if the bootloader files are installed very near the beginning of the drive, I forget the maximum size but it's quite small. This doesn't apply so much (I don't think) in newer machines, at least from my experience.

4) It should work now, unless I've missed something.

---

### Post by EizoSiege on 2009-08-28
> **fela said:**
> 1) Make sure your default boot device is the 500GB drive, and was when you installed Ubuntu.

2) Make sure grub is installed to the 500GB drive. If it was the deafult boot drive when you installed ubuntu, this would have happened automatically.

3) Make sure the ubuntu partition is at the beginning of the drive. In particular, make sure the /boot partition (by default the same one as the main one) is at the beginning of the drive, before instead of after the NTFS partition. This is because some computers can only boot if the bootloader files are installed very near the beginning of the drive, I forget the maximum size but it's quite small. This doesn't apply so much (I don't think) in newer machines, at least from my experience.

4) It should work now, unless I've missed something.
Sounds promising. I am trying as we speak. I just noticed something. My computer has the same specs as you do. I have the same RAM, CPU, the only difference is that I have a 6600GT Geforce, and i have a AM2 Asus mainboard.

Will report back in a while if it has worked.

---

### Post by EizoSiege on 2009-08-28
I can't seem to get it to work. I took the 500GB HDD, which has a 350GB NTFS from before hand which I have been using with windows. So I have about 150GB to use for the Linux OS. 

1. I choose to: "Specify partitions manually (advanced)"
2. I delete the 150GB partition, so now there is 150GB free space.
3. I select :"new partition" and make a 10GB Swap partition.
4. I thene choose to make a 10GB Boot partition. Wich I mount as /boot.
5. I Select: "new partition" again, and make a 130GB = Primary,EXT3. Which I mount as "/"
6. I then select the EXT3 130GB "/" partition, and press forward. 
I then type in my name and all that stuff. Then it comes to the part where it whants me to take out the disk and restart the computer. When I then restart the computer the error message comes up: "Disk boot failure, insert system disk and press enter"

I also have a :"push F8 to choose boot" i then manually choose my 500GB harddrive and still the error message. 

What am i doing wrong? Is it so hard for Linux to realize that i don't whant to use my entre 500GB disk to operate Linux?

Any more suggestions would be very nice.
And thanks for the previus replyes.

---

### Post by presence1960 on 2009-08-28
well instead of going round & round until the cows come home (just my tired attempt at humor) we need to see exactly what the installer has done to your 500 GB disk, do this please:

Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by EizoSiege on 2009-08-29
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

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

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x113707ab

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          1,008 1,953,522,143 1,953,521,136   f W95 Ext d (LBA)
/dev/sda5               1,071 1,953,521,135 1,953,520,065   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000ae60

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         235,689,615   976,751,999   741,062,385   f W95 Ext d (LBA)
/dev/sdb5         245,762,433   976,751,999   730,989,567   7 HPFS/NTFS
/dev/sdb6         235,689,741   245,762,369    10,072,629  82 Linux swap / Solaris
/dev/sdb2                  63   235,689,614   235,689,552  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda5: UUID="42E45ABFE45AB4BF" LABEL="Slave" TYPE="ntfs" 
/dev/sdb2: UUID="5bf3ef9f-2bb2-43e6-87a6-50579c70375d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="6E4C0A614C0A2505" LABEL="Slave2" TYPE="ntfs" 
/dev/sdb6: TYPE="swap" UUID="58dd1e99-638c-48eb-88fa-063362d03e03" 

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


=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5bf3ef9f-2bb2-43e6-87a6-50579c70375d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5bf3ef9f-2bb2-43e6-87a6-50579c70375d

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		5bf3ef9f-2bb2-43e6-87a6-50579c70375d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5bf3ef9f-2bb2-43e6-87a6-50579c70375d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		5bf3ef9f-2bb2-43e6-87a6-50579c70375d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5bf3ef9f-2bb2-43e6-87a6-50579c70375d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		5bf3ef9f-2bb2-43e6-87a6-50579c70375d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=5bf3ef9f-2bb2-43e6-87a6-50579c70375d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=58dd1e99-638c-48eb-88fa-063362d03e03 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  65.6GB: boot/grub/menu.lst
  65.7GB: boot/grub/stage2
  65.7GB: boot/initrd.img-2.6.28-11-generic
  65.6GB: boot/vmlinuz-2.6.28-11-generic
  65.7GB: initrd.img
  65.6GB: vmlinuz

```

---

### Post by presence1960 on 2009-08-29
Do this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

In # 6 use setup (hd1)

Reboot and go into BIOS. Set the 500 Gb disk to boot first in hard disk boot order. save the change and continue booting

---

### Post by EizoSiege on 2009-08-29
Oh my god! It actually worked. Pity though that it took this long for Linux just to install. 
Well, guess that's just part of Linx that we'll have to live with. 

Anyways, thank you guys very much for your help and especially you presence1960.

Btw, what was it that was wrong in the first place?

---

### Post by presence1960 on 2009-08-29
> **EizoSiege said:**
> Oh my god! It actually worked. Pity though that it took this long for Linux just to install. 
Well, guess that's just part of Linx that we'll have to live with. 

Anyways, thank you guys very much for your help and especially you presence1960.

Btw, what was it that was wrong in the first place?

I personally put GRUB on MBR of the disk that contains Linux which ideally should be the first disk that boots (this is just my preference, it doesn't have to be that way!). You had it on the other disk which as I recall you said was almost filled with data. So I went with my instincts on this one and had you install GRUB to the 500 GB disk and then make that first in boot order in BIOS.

Enjoy Ubuntu!

---

### Post by fela on 2009-08-30
It's not a problem with Linux, it's a problem with all operating systems. It's just that with Linux it doesn't decide to willy-nilly overwrite the MBR of another OS that you might have, not like windows for instance, which overwrites the MBR of grub if you install it (making you have to restore grub).

Now if the BIOS had a better disk management mechanism it might be a little easier. I don't know what EFI is like.

---

