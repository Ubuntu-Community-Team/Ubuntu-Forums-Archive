---
title: "No GRUB at startup"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by tanusgreystar on 2009-03-18
Hi. I installed the Ubuntu OS along with Win XP as dual boot (XP was installed first). When I boot the computer it automatically goes to Windows. I don't get the GRUB bootloader screen. The only way I am able to boot in Linux is if I have the CD in the drive and boot off the CD. Then I choose to boot from the HDD, and Ubuntu loads. How do I get it so it goes to GRUB when I turn on the computer??

---

### Post by Rolle_Pollie on 2009-03-18
> **tanusgreystar said:**
> Hi. I installed the Ubuntu OS along with Win XP as dual boot (XP was installed first). When I boot the computer it automatically goes to Windows. I don't get the GRUB bootloader screen. The only way I am able to boot in Linux is if I have the CD in the drive and boot off the CD. Then I choose to boot from the HDD, and Ubuntu loads. How do I get it so it goes to GRUB when I turn on the computer??


I think you'll need to edit the boot.ini

A google search should be able to walk ya through it.

---

### Post by meierfra. on 2009-03-18
If you have more than one hard drive, Grub might be installed to the MBR of your second hard drive. So see what happens if you set your bios to boot   from you second (or third or ...) hard drive.

[B]
If this did not solve your problem:[/B]

In order to get a clearer picture of your setup, I suggest to boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by tanusgreystar on 2009-03-20
Yeah, it's on my second (data) HDD. How do I move it to the C drive?? I want to be able to take my data drive out and put it in a file server, so I will only have the maine drive in this pc.I changed the boot.ini and  I installed WinGrub in windows. Should I uninstall that?

---

### Post by meierfra. on 2009-03-20
> Yeah, it's on my second (data) HDD. 

So what happens when you  set your bios boot from the second HDD?   Do you get the Grub menu? Any error messages?


> I changed the boot.ini and I installed WinGrub in windows. Should I uninstall that? 

No. WinGrub shouldn't cause any problems.

---

### Post by tanusgreystar on 2009-03-20
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /GRLDR /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

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

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x078bcbb0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   398,283,479   398,283,417   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ba01ba0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   731,102,084   731,102,022   7 HPFS/NTFS
/dev/sdb2         731,102,085 1,465,144,064   734,041,980   5 Extended
/dev/sdb5         731,102,148 1,445,400,179   714,298,032  83 Linux
/dev/sdb6       1,445,400,243 1,465,144,064    19,743,822  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6E1CC2B61CC2789B" LABEL="Music Files" TYPE="ntfs" 
/dev/sdb1: UUID="AADC870BDC86D0CD" TYPE="ntfs" 
/dev/sdb5: UUID="97fcdc42-4b09-40f6-b4b1-905118e5657a" TYPE="ext3" 
/dev/sdb6: UUID="f7ecab01-843b-48be-be35-2370a9b0eb3f" TYPE="swap" 

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
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /media/Musicfiles type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/Music Files type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tanusgreystar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tanusgreystar)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=tanusgreystar)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\GRLDR="Start Grub"


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
# kopt=root=UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=97fcdc42-4b09-40f6-b4b1-905118e5657a

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
uuid		97fcdc42-4b09-40f6-b4b1-905118e5657a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		97fcdc42-4b09-40f6-b4b1-905118e5657a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		97fcdc42-4b09-40f6-b4b1-905118e5657a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		97fcdc42-4b09-40f6-b4b1-905118e5657a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		97fcdc42-4b09-40f6-b4b1-905118e5657a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb5 :
UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb6 :
UUID=f7ecab01-843b-48be-be35-2370a9b0eb3f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/Musicfiles ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Music\040Files ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdb5: Location of files loaded by Grub: ===================


 450.3GB: boot/grub/menu.lst
 450.3GB: boot/grub/stage2
 450.3GB: boot/initrd.img-2.6.27-11-generic
 450.4GB: boot/initrd.img-2.6.27-7-generic
 450.3GB: boot/vmlinuz-2.6.27-11-generic
 450.3GB: boot/vmlinuz-2.6.27-7-generic
 450.3GB: initrd.img
 450.4GB: initrd.img.old
 450.3GB: vmlinuz
 450.3GB: vmlinuz.old

---

### Post by meierfra. on 2009-03-20
> I want to be able to take my data drive out 

OK.   You need to install Grub  the internal drive and edit menu.lst

Open a terminal in Ubuntu (I assume you are able to boot into Ubuntu, if not just boot from the Ubuntu LiveCD)

Reinstall grub via:

```
sudo grub
```
and at the "grub>"prompt:

```
device (hd0) /dev/sdb
root (hd0,4)
setup (hd0)
quit
```


Open  menu.lst via


```
gksudo gedit /boot/grub/menu.lst
```


Change

title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

to 

title Microsoft Windows XP Home Edition
root (hd0,0)
chainloader +1


Save the file. Reboot and you should be able to boot of your internal drive and get the Grub menu.

---

### Post by tanusgreystar on 2009-03-20
In menu.lst was I supposed to delete 

map (hd0) (hd1)
map (hd1) (hd0)?

---

### Post by meierfra. on 2009-03-20
Yes. Just use the three lines I posted.

---

### Post by sahabcse on 2009-03-20
Hi

Try to fix the grub. Follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)

---

### Post by tanusgreystar on 2009-03-20
> **meierfra. said:**
> Yes. Just use the three lines I posted.

Yeah it works now tha:guitar:nks!!

---

### Post by meierfra. on 2009-03-20
> Yeah it works now thanks!!

Great. Have fun with XP and Ubuntu.

---

### Post by tanusgreystar on 2009-03-22
How do I uninstall WinGrub? I don't need it. When I select Win XP to boot, I still get another screen to select OS (WinGrub), so I have to choose XP again. I googled uninstalling WinGrub but it only shows INSTALLING wingrub...:(

---

### Post by upchucky on 2009-03-22
Tanus you may want to create your own thread for this, it is likely to get more direct attention.

indicate if you are dual booting, wanting or not wanting a dual boot, or a bios boot.

if u have a bootable Ubuntu install or the live cd then do this,

download this

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh
```


post the results on your new thread.

---

### Post by koporoko on 2009-03-22
I have grub but i cannot use the arrows on my key board to go down to ubuntu to activate----
what could be a reason for my normal key board not working in this situation?

Your kind help would be appreciated-------thank you

---

### Post by upchucky on 2009-03-22
kopo, you also should start your own thread for better results.

need more information, but I am guessing that you have arrived at a grub prompt instead of a booted system, if this is the case you need to read about editing or commands to enter at the grub prompt as it only accepts certain keys when in edit or command mode.

---

### Post by meierfra. on 2009-03-22
**tanusgreystar:**  You need to edit  boot.ini.  This shows you how to open boot.ini for editing:
[http://support.microsoft.com/kb/289022]("http://support.microsoft.com/kb/289022")

Just delete the WinGrub line.

> Tanus you may want to create your own thread for this, it is likely to get more direct attention
????? This is tanusgreystar's thread and the question is directly related to the previous questions. So I think this is a good place to post.

> kopo, you also should start your own thread for better results.
+1

---

### Post by tanusgreystar on 2009-04-02
I went into boot.ini but there's no wingrub line, just the regular grub.

---

### Post by meierfra. on 2009-04-02
> I went into boot.ini but there's no wingrub line, just the regular grub.
Sorry, it doesn't say Win Grub, but that is still the line you need to delete.  So delete:

C:\GRLDR="Start Grub"

---

