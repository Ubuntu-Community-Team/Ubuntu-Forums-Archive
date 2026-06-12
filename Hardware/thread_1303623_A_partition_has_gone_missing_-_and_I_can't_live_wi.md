---
title: "A partition has gone missing - and I can't live without it"
date: 2009-10-28
forum: Hardware
---

### Post by Dr.Suave on 2009-10-28
Hiya - I've got myself in trouble. 

I have three storage partitions and a swap. Two are NTFS and one's ext3. I used to run with Vista on one of the NTFS, Ubuntu on the ext3 and my documents sitting on the other NTFS. 

Unfortunately, I've been messing about with Grub, and now I can't get into Vista at all, or for some reason access my document partition - and on that partition I had some unbacked-up copies of files that I would be very bitter about losing.

Here's the output of sudo fdisk -l 

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad49e9aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223        9863    37278832+   7  HPFS/NTFS
/dev/sda3            9864       10526     5325547+  82  Linux swap / Solaris
/dev/sda4           10527       19457    71738257+  83  Linux
```

It's sda2 that's gone missing.

Originally I couldn't see sda1 or sda2 in Nautilus, but after running Windows Recovery (which didn't do any recovering - apparently they have a newfound respect for Grub), sda1 mysteriously reappeared. But sda2 is the one I'm after.

I would be hugely grateful if someone could tell me how to get my files back, I had a draft of a novella and all sorts of precious stuff on there.

Thanks

Wilf

---

### Post by arrange on 2009-10-28
If you want to recover the files, try mounting the *sda2* partition manually```
cd /media
sudo mkdir win
sudo mount -v -t ntfs /dev/sda2 win
```Does it cough up any error messages? Can you browse the */media/win* folder now?

If you want help with booting the Win partition, provide more information via [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/"). (If you don't know how to run the script, [look here]("http://sourceforge.net/docman/display_doc.php?docid=137292&group_id=250055").)

---

### Post by Dr.Suave on 2009-10-28
Thanks for the speedy response!

Unfortunately, your commands gave me this:

```
wilf@wilf-laptop:~$ cd /media
wilf@wilf-laptop:/media$ sudo mkdir win
[sudo] password for wilf: 
wilf@wilf-laptop:/media$ sudo mount -v -t ntfs /dev/sda2 win
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
wilf@wilf-laptop:/media$ 
```

Where does that leave us? :)

---

### Post by arrange on 2009-10-28
Looks pretty bad :(

Probably the *sda2* boot sector (not sda MBR!) is corrupted. Your best bet now would probably be to try to repair the partition from Windows, and if that doesn't work, attempt to recover data from the damaged partition.

Some links:
[http://joeb454.ubuntuforums.org/showthread.php?t=855081&page=2](http://joeb454.ubuntuforums.org/showthread.php?t=855081&page=2)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Dr.Suave on 2009-10-28
Oh well, thanks for your help. Would you know how to get Grub to point to Vista again? I've downloaded the script you linked to, but the link to the instructions was broken.

Thanks

---

### Post by arrange on 2009-10-28
Just save the file onto your desktop and run it by typing```
sudo bash ~/Desktop/boot_info_script*.sh
```After a while you will see a RESULTS.txt file. Post the contents of the file here.

---

### Post by Dr.Suave on 2009-10-28
Thanks a lot - here's the output:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xad49e9aa

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 HPFS/NTFS
/dev/sda2          83,891,430   158,449,094    74,557,665   7 HPFS/NTFS
/dev/sda3         158,449,095   169,100,189    10,651,095  82 Linux swap / Solaris
/dev/sda4         169,100,190   312,576,704   143,476,515  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D46E92596E9233E8" LABEL="System Disk" TYPE="ntfs" 
/dev/sda3: UUID="d13ec82e-077c-4742-8e9e-233e988a5110" TYPE="swap" 
/dev/sda4: UUID="c046783c-db2d-4893-8fc2-735181a9c24f" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/wilf/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wilf)
/dev/sr0 on /media/2007.11.03_2329 type udf (ro,nosuid,nodev,uhelper=hal,uid=1000)


=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=c046783c-db2d-4893-8fc2-735181a9c24f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c046783c-db2d-4893-8fc2-735181a9c24f

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
uuid		c046783c-db2d-4893-8fc2-735181a9c24f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c046783c-db2d-4893-8fc2-735181a9c24f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c046783c-db2d-4893-8fc2-735181a9c24f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c046783c-db2d-4893-8fc2-735181a9c24f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c046783c-db2d-4893-8fc2-735181a9c24f
kernel		/boot/memtest86+.bin
quiet

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=c046783c-db2d-4893-8fc2-735181a9c24f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=d13ec82e-077c-4742-8e9e-233e988a5110 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


  89.6GB: boot/grub/menu.lst
  89.7GB: boot/grub/stage2
  89.7GB: boot/initrd.img-2.6.28-11-generic
  89.7GB: boot/vmlinuz-2.6.28-11-generic
  89.7GB: initrd.img
  89.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  4d 47 52 20 69 73 20 63  |.....,DcMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb
```

Thanks

---

### Post by arrange on 2009-10-28
Now - what exactly happens if you choose the option **Windows 95/98/NT/2000** from the Grub menu?

---

### Post by Dr.Suave on 2009-10-28
I'm afraid it never gives me the choice - and I pasted all of the windows entry in there from the example given in the menu.lst file - the drive is probably wrong - it was a clutching at straws type thing.

---

### Post by arrange on 2009-10-28
Right after you reboot your machine, can you see this Grub menu?```
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, memtest86+
Windows 95/98/NT/2000

```(for about 3 secs)

---

### Post by Dr.Suave on 2009-10-28
No :(

---

### Post by arrange on 2009-10-28
Oh, sorry, I overlooked the **hiddenmenu** option in your *menu.lst* file.

OK then - after reboot you should see a black screen with a 2-3 secs countdown. Press *Esc* key during the countdown and you should be able to see the Grub menu.

Use the *down arrow* key to navigate to the Win option and press Enter.

---

### Post by Dr.Suave on 2009-10-28
That worked! Thanks - I'll uncomment the hiddenmenu option then.

The drive is still broken in Windows, though, but I have managed to find some of the more important stuff in my sent mail folder.

I suppose in the morning I'll try your drive recovery links, save what I can, then reformat the thing.

Thanks a lot, it was a big help.

---

