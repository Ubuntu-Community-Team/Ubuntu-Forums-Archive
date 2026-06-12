---
title: "XP Dual Boot Install Gone Bad"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by MonkeyChewTobacco on 2009-08-17
First time noob here
 
First off, sorry if this has been done before - I can see a lot of stuff about dual boot, dedicated disks, etc but nothing to answer this specific question.
 
I have (or had to be exact) a Win XP PC with twin 200GB hard disks. I want to keep XP on the first disk (disk 0), put Ubuntu 9 on the other (disk 1) and have a grub bootloader.
 
I ran the install off the CD but found myself totally guessing when it came to the bit about the partitioning. Here's a screenshot of what I went for:
 
[IMG]http://www.chesteratlarge.com/large/resources/forumpics/screenshot500.jpg[/IMG]
 
I'm not sure what happened - I guess disk1 was reformatted as ext3 and had Ubuntu plus apps installed on it.
 
Problem is, whatever I do I can't see grub and I always boot straight into XP, even if I go into the BIOS on startup and ask it boot from the second (disk 1) drive. Once I'm in XP, I can't see the second disk, except in Device Manager.
 
What would be my best bet to get from where I am now to where I want to be? I'd prefer not to have start messing with master/slave jumper settings if at all poss.
 
TIA

---

### Post by dstew on 2009-08-17
It looks like the grub boot loader was not installed during your Ubuntu installation. This may be easy to fix, or it may be hard. If the Ubuntu installation configured grub for booting (created a menu.lst file, which is grub's configuration file) but just did not put the boot loader in, that is easy to fix. Follow the instructions [here.]("http://ubuntuforums.org/showthread.php?t=224351")

However, if no menu.lst file was created (you will find out if you try the reinstallation method above) you will need to create one. That is more difficult. But, just try the grub reinstallation and see if that works.

---

### Post by presence1960 on 2009-08-17
let's see exactly what your setup & boot process looks like. Boot off the Ubuntu live CD, choose "try ubuntu without any changes", when the desktop loads open Firefox and come back here. Download the Boot Info Script 0.32 from my signature line. Once that is on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. Paste the contents of that file back here. Once pasted here highlight all text and click # on the toolbar to place code tags around the text.

---

### Post by MonkeyChewTobacco on 2009-09-02
Sorry for the delay in replying (too many jobs, too many kids) but I did what you said presence1960, and here's my results.txt:
 
```
 
============================= Boot Info Summary: ==============================
 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
sdb1: _________________________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe12b2d15
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63   390,716,864   390,716,802   7 HPFS/NTFS

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e127e12
Partition  Boot         Start           End          Size  Id System
/dev/sdb1                  63   388,114,334   388,114,272  83 Linux
/dev/sdb2         388,114,335   390,716,864     2,602,530   5 Extended
/dev/sdb5         388,114,398   390,716,864     2,602,467  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="8C7467B174679CA8" TYPE="ntfs" 
/dev/sdb1: UUID="2c6e2126-b9a8-4d0a-b83c-5923e3c62cdc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="b6371023-d687-468a-b10f-c03028a4f88e" 
/dev/ramzswap0: TYPE="swap" 
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda1/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=============================== sdb1/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=2c6e2126-b9a8-4d0a-b83c-5923e3c62cdc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b6371023-d687-468a-b10f-c03028a4f88e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=================== sdb1: Location of files loaded by Grub: ===================

 104.8GB: boot/vmlinuz-2.6.28-11-generic
 104.8GB: vmlinuz

```
 
Can you tell me what this means? (just to recap, my intention was to be able to boot from disk 0 (Win XP) with grub coming up first to give me the choice of booting into XP or Ubuntu.)
 
Thanks in advance.

---

### Post by presence1960 on 2009-09-02
Your ubuntu is installed to sdb1. but GRUB is not installed. Also you are missing menu.lst & GRUB stage 2.

You can try reinstalling GRUB. Boot off the Ubuntu Live CD, choose try Ubuntu without any changes. When the desktop loads open a terminal and run ```
sudo grub-install /dev/sda
```

Then rerun the script again & post the output. Hopefully it will take care of those issues. Then we can see about getting your GRUB menu on boot.

---

### Post by presence1960 on 2009-09-02
Bear in mind that your install may be bad because GRUB installs to (hd0) by default unless you change the location or choose install no bootloader during the install. if the above fix does not work I would reinstall Ubuntu again to the same partitions on sdb. But let's see the results of the boot info script after you run that command to install GRUB.

---

### Post by MonkeyChewTobacco on 2009-09-02
I got this:
 
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
```

---

### Post by presence1960 on 2009-09-02
> **MonkeyChewTobacco said:**
> I got this:
 
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
```

at this point I would say reinstall. BTW sorry for the delay I was out with my daughter.

---

### Post by MonkeyChewTobacco on 2009-09-02
Thanks, presence1960, I'll try reinstalling.

Can you suggest where I might change the options I went for in the screenshot in my first post?

---

### Post by presence1960 on 2009-09-02
> **MonkeyChewTobacco said:**
> Thanks, presence1960, I'll try reinstalling.

Can you suggest where I might change the options I went for in the screenshot in my first post?

I would do a manual install option since the partitions are set up already. The next window you will highlight sdb1 and click edit. Then set the parameters that come up in the window. Use as : choose filesystem ext 3, tick the format box and set mount point as /. Click add or ok to apply.

Then highlight the swap partition sdb5 and click edit. Set parameter use as : linux-swap. Click add or Ok. Proceed with the install. if you want GRUB to boot don't make any adjustments for GRUB. proceed and you should be good to go. let us know what happens.

---

### Post by MonkeyChewTobacco on 2009-09-02
Followed your advice and it went OK until I got an 'Installation Failed [Errno 5] Input/Output error'.
 
Tried again and had to run through a couple more passes at it but eventually it got there OK.
 
A quick check looks very promising (grub works correctly) but it's time for bed.
 
Muchas gracias for your help presence1960.

---

### Post by presence1960 on 2009-09-02
Glad you got it working. if you need anything else post back. Enjoy Ubuntu.

---

