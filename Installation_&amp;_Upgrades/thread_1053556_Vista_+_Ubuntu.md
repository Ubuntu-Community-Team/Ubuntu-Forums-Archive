---
title: "Vista + Ubuntu"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by AE7 on 2009-01-28
Hey guys, I have a little problem here, I installed Ubuntu and now my Vista drive will not boot. I have a 1TB drive for Vista and a 250GB drive for Ubuntu(physical drives not partitions). I installed Vista a week earlier(1TB drive) and I got busy with work. So I waited until tonight to install Ubuntu on the drive(250GB) that has been inactive since the Vista install.

Ubuntu has been great, I can load GRUB's menu up and the Ubuntu options are there but no Vista. I have disconnected the Ubuntu drive and Vista does not boot from the other drive(I am stuck at a simple screen after the POST). It's almost like the Ubuntu install killed the bootmgr but I get no error. I was stupid when I installed Ubuntu for I didn't backup anything from the Vista drive. Unfortunately, I have over 30GB of data on the Vista drive that I MUST have. Does anyone have a solution?

Much appreciated ;)

---

### Post by tmcarson1 on 2009-01-28
You may be able to boot into ubuntu then access the vista drive and copy your 30gb of info you need over to the ubuntu drive, just in case you need to reinstall vista.

I'm not saying you have to, honestly don't know how to fix that problem, although you could do some research on the fixmbr command for windows.

But you should be able to at least access the windows drive while in ubuntu and copy your files you need over to the ubuntu drive.

Good luck!

---

### Post by caljohnsmith on 2009-01-28
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Vista booting problem might be.

---

### Post by AE7 on 2009-01-28
> **tmcarson1 said:**
> You may be able to boot into ubuntu then access the vista drive and copy your 30gb of info you need over to the ubuntu drive, just in case you need to reinstall vista.

I'm not saying you have to, honestly don't know how to fix that problem, although you could do some research on the fixmbr command for windows.

But you should be able to at least access the windows drive while in ubuntu and copy your files you need over to the ubuntu drive.

Good luck!

It won't allow me to mount the drive because of an unclean shutdown, I happened to be in a hurry. I have tried to do this already... I'd like to get Vista to boot and function again... Any other ideas?

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
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
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 sdb1 ntfs-3g force 0 0

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9fbf9fbf

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  476,262,989  476,262,927  83 Linux
/dev/sda2        476,262,990  488,392,064   12,129,075   5 Extended
/dev/sda5        476,263,053  488,392,064   12,129,012  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x33961f2f

Partition  Boot        Start          End         Size  Id System

/dev/sdb1              2,0481,953,521,6631,953,519,616   7 HPFS/NTFS

/dev/sdb1 ends after the last cylinder of /dev/sdb

Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot        Start          End         Size  Id System

/dev/sdc1                 63  976,768,064  976,768,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2202f84a-8385-47c4-bacd-617f2bb5c011" TYPE="ext3" 
/dev/sda5: UUID="68275925-c82e-498f-a8ef-b3cca02e55bf" TYPE="swap" 
/dev/sdb1: UUID="5EFA80B8FA808E49" TYPE="ntfs" 
/dev/sdc1: LABEL="My Book" UUID="0367-83D9" TYPE="vfat" 

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
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ae/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ae)
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/scd1 on /media/cdrom1 type udf (ro,nosuid,nodev,utf8,user=ae)

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
# kopt=root=UUID=2202f84a-8385-47c4-bacd-617f2bb5c011 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2202f84a-8385-47c4-bacd-617f2bb5c011

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
uuid		2202f84a-8385-47c4-bacd-617f2bb5c011
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2202f84a-8385-47c4-bacd-617f2bb5c011 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2202f84a-8385-47c4-bacd-617f2bb5c011
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2202f84a-8385-47c4-bacd-617f2bb5c011 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2202f84a-8385-47c4-bacd-617f2bb5c011
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2202f84a-8385-47c4-bacd-617f2bb5c011 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=68275925-c82e-498f-a8ef-b3cca02e55bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location  of files loaded by Grub: ===================


  60.9GB: boot/grub/menu.lst
  61.0GB: boot/grub/stage2
  61.0GB: boot/initrd.img-2.6.27-7-generic
  60.9GB: boot/vmlinuz-2.6.27-7-generic
  61.0GB: initrd.img
  60.9GB: vmlinuz

=============================== StdErr Messages: ===============================

/home/ae/Desktop/boot_info_script22.sh: line 1052: cd: /media/My: No such file or directory
```

You'll notice that I have a 500GB drive listed in there, that's a USB external drive that is used as a storage/backup drive. It contains no operating systems.

Thanks guys

---

### Post by AE7 on 2009-01-28
UPDATE:

Alright, I have my files from the Vista install. I had to force mount the drive and I just saved the files to my backup drive. So now that is one less problem...

New question, how may I install Vista so that I can boot both Ubuntu and Vista without them interfering with each other?

Thanks

---

### Post by caljohnsmith on 2009-01-28
How about we first try booting Vista from Grub and see if that works? I think it's at least worth trying before you do an entire reinstall. If that sounds OK, then how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following entries at the end:
```
title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Reboot, and let me know exactly what happens when you try each Vista entry from the Grub menu. We can work from there if you want.

---

### Post by AE7 on 2009-01-28
> **caljohnsmith said:**
> How about we first try booting Vista from Grub and see if that works? I think it's at least worth trying before you do an entire reinstall. If that sounds OK, then how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following entries at the end:
```
title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Reboot, and let me know exactly what happens when you try each Vista entry from the Grub menu. We can work from there if you want.

Alright...I tried both, the first option gave me the dreaded error about the boot manager missing. The second one will not work because the drive is hd1.

And, I have ran the Vista disc as a repair disc, trying to fix the boot. It doesn't work...

---

### Post by Javich on 2009-01-29
Dude, the way I made this work:

Disk1 - is going to be Vista 
Disk2 - is going to be Ubuntu


To have both running:
1.- Unplug (physically) or bios-disable your Disk2
2.-Install Vista
3.- Plug Disk2 and unplug disk1
4.- Install Ubuntu
5.- Plug both disks
6.- Set your BIOS to look for a OS in disk2 before disk1
7.- Get in linux and edit your Grub settings to add the vista drive to the boot menu.

---

### Post by caljohnsmith on 2009-01-29
If replacing the Vista boot files is all that Vista needs to boot again, we can do that, but how about first posting the following so we can check if there's maybe some other issues:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /mnt && ls -l /mnt
```

---

### Post by AE7 on 2009-01-29
> **caljohnsmith said:**
> If replacing the Vista boot files is all that Vista needs to boot again, we can do that, but how about first posting the following so we can check if there's maybe some other issues:


```
ae@ae-ubmachine:~$ sudo ntfsfix /dev/sdb1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdb1 was processed successfully.
ae@ae-ubmachine:~$ sudo mount -t ntfs-3g /dev/sdb1 /mnt && ls -l /mnt
total 4497872
drwxrwxrwx 1 root root          0 2006-11-02 10:42 Documents and Settings
-rwxrwxrwx 1 root root 2145902592 2009-01-28 07:31 hiberfil.sys
drwxrwxrwx 1 root root          0 2009-01-18 01:15 NVIDIA
-rwxrwxrwx 1 root root 2459828224 2009-01-28 07:31 pagefile.sys
drwxrwxrwx 1 root root       4096 2009-01-25 20:06 ProgramData
drwxrwxrwx 1 root root       8192 2009-01-27 20:58 Program Files
drwxrwxrwx 1 root root      12288 2009-01-28 18:22 Program Files (x86)
drwxrwxrwx 1 root root          0 2009-01-17 12:51 $Recycle.Bin
drwxrwxrwx 1 root root      12288 2009-01-27 20:58 System Volume Information
drwxrwxrwx 1 root root      32768 2009-01-28 18:23 TCASH4
drwxrwxrwx 1 root root       4096 2009-01-17 12:51 Users
drwxrwxrwx 1 root root      16384 2009-01-28 07:33 Windows
ae@ae-ubmachine:~$ 
```

Alright there's that...

Thanks

---

### Post by caljohnsmith on 2009-01-29
Great, it looks like missing boot files may be the only thing wrong with Vista. How about following step 2 of [this tutorial]("http://ubuntuforums.org/showpost.php?p=5726832"), and note that you don't need to do the last "bootsect" command in step 2. You also don't need to do step 1 or step 3. Once you've done that, try booting Vista again from Grub and let me know how it goes.

---

### Post by amadeus266 on 2009-01-29
I just went through this. I installed Ubuntu inside windows (Wubi) and then my laptop would start up at all. I just put in my Vista install disk and booted to it. Then I chose the option to repair my computer. When it finished, all was well. I can now boot into either one at startup.

---

### Post by AE7 on 2009-01-29
Okay, I went through that how-to successfully... It boots but at the logon screen it greets me with a BSOD and restarts before I can even catch the error. It stays at the logon screen for about 6 seconds with or without user action before throwing blue at me. Any idea what's going wrong? I have never this much trouble out of an OS in my life!

Thanks guys

---

### Post by caljohnsmith on 2009-01-29
OK, how about booting your Vista CD again, and this time do:
```
bootrec /rebuildbcd
chkdsk /r
```
And run the chkdsk command as many times as it takes until it reports no errors. Then reboot and see if you get any further booting Vista. If that doesn't make any difference, do you have your own Vista Install CD, or did you have to download the Vista Recovery CD linked to in the tutorial? If you have a Vista Install CD, how about trying what amadeus266 suggested and do a "Vista Repair". Let me know how that goes.

---

