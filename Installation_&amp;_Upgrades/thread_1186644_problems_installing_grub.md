---
title: "problems installing grub"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by ipburbank on 2009-06-13
I can't seem to install grub on my new setup. I have windows on my drive, and I want to install ubuntu. I am familiar with ubuntu, have been using it for years but it was time to re-install. However now I get the error:

executing 'grub-install /dev/sda' failed. this is a fatal error'

also I when I try to run:

find /grub/stage1

or

find /boot/grub/stage1

they both return:
Error 15: File not found
WHY!!??? ](*,)

~thanks for any help, Istvan.

---

### Post by merlinus on 2009-06-13
From where are you running the grub commands?

If from a terminal running from the live cd, then you have to get to a grub prompt to run them.

But perhaps you already knew this...

---

### Post by ipburbank on 2009-06-13
update: when I boot the system with no live cd grub give me 'error 17'

I go into the terminal, type 'grub' and then the commands. still same error.

---

### Post by merlinus on 2009-06-13
You are using

sudo grub

to get to the grub>

prompt, yes?

Just wanting to be sure....

---

### Post by ipburbank on 2009-06-13
yes. but I can't find the stage1 file with the grub commands. why?

---

### Post by merlinus on 2009-06-13
Probably because it never got installed, as detailed in your original post.

You might try reinstalling it.  For example, from the grub prompt, instead of trying to find /boot/grub/stage1:

root (hd0,1)  #if ubuntu is the second partition on your first -- or only -- hdd
setup (hd0)
quit

Substitute for your actual hdds and partitions.

---

### Post by Melhisedek on 2009-07-02
Have the exact same problem, tried your idea merlinus but sadly no go. I made root every damn number up to 6 (hd0,1-6), and than grub started complaining that BIOS can't take so many.

I'm sure my grub isn't installed at all, is there some other way of installing it? Or forcing it?

Here is some boot info if it can help perhaps:


```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
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
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01940193

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620 2,930,272,064 2,725,475,445   f W95 Ext d (LBA)
/dev/sda5         204,796,683 1,433,592,404 1,228,795,722   7 HPFS/NTFS
/dev/sda6       1,433,592,468 2,704,975,995 1,271,383,528   7 HPFS/NTFS
/dev/sda7       2,704,976,568 2,707,016,759     2,040,192  82 Linux swap / Solaris
/dev/sda8       2,707,016,823 2,930,272,064   223,255,242  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1999 MB, 1999568384 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3905407 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000330b0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,905,406     3,905,344   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="8808F12108F10F46" TYPE="ntfs" 
/dev/sda5: UUID="74442E20442DE618" TYPE="ntfs" 
/dev/sda6: UUID="42285551285544D7" TYPE="ntfs" 
/dev/sda7: UUID="259fc2cb-ae67-4b88-91a9-706152e6cf62" TYPE="swap" 
/dev/sda8: UUID="0137c039-7903-42ab-8353-59d911d1ce98" TYPE="ext3" 
/dev/sdb1: LABEL="IPREP_V008" UUID="FA78-3824" TYPE="vfat" 

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
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda8 on /target type ext3 (rw,relatime,errors=remount-ro)
/proc on /target/proc type none (rw,bind)
/dev on /target/dev type none (rw,bind)


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=0137c039-7903-42ab-8353-59d911d1ce98 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=259fc2cb-ae67-4b88-91a9-706152e6cf62 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


1430.0GB: boot/grub/stage2
1430.0GB: boot/initrd.img-2.6.28-11-generic
1430.1GB: boot/vmlinuz-2.6.28-11-generic
1430.0GB: initrd.img
1430.1GB: vmlinuz
```

And here is a screen of my Gparted...

[[IMG]http://img41.imageshack.us/img41/1327/screenshotggf.th.png[/IMG]](http://img41.imageshack.us/i/screenshotggf.png/)

Anything else you guys need?

---

### Post by merlinus on 2009-07-02
Post results of:

```
sudo fdisk -l

```

---

### Post by Melhisedek on 2009-07-02
Here it goes:



```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01940193

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749      182401  1362737722+   f  W95 Ext'd (LBA)
/dev/sda5           12749       89237   614397861    7  HPFS/NTFS
/dev/sda6           89238      168377   635691764    7  HPFS/NTFS
/dev/sda7          168378      168504     1020096   82  Linux swap / Solaris
/dev/sda8          168505      182401   111627621   83  Linux

Disk /dev/sdb: 1999 MB, 1999568384 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000330b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         244     1952672    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(242, 254, 63) logical=(243, 25, 37)
```


There is no grub folder inside /boot

i've tried copying grub folder there but find /boot/grub/stage1 still can't be found :( Even if it really is there...

---

### Post by merlinus on 2009-07-02
You can try this in a terminal whilst booting from the live cd:

```
sudo grub
root (hd0,7)
setup (hd0)
quit

```

---

### Post by Melhisedek on 2009-07-02
In that case I get this message:

```
grub> root (hd0,7)

Error 18: Selected cylinder exceeds maximum supported by BIOS
```

---

### Post by merlinus on 2009-07-02
Should have done so before, but our posts crossed so I only now looked at your gparted screenshot.  The mountpoint for sda8 should be /, not /target.  It appears, therefore, that no root partition exists.

I wonder how you were able to install without that?

---

### Post by Melhisedek on 2009-07-02
I'm not sure everything is installed. My install fails at 94% with "Executing 'grub-install /dev/sda' failed. This is a fatal error"

So I never get through the install :( I'm just booting off a LiveCD

---

### Post by merlinus on 2009-07-02
OK, that explains it.  You will certainly have to start over.  Good info on dual booting here:

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm]("http://apcmag.com/the_definitive_")

You may wish to get rid of those other ntfs partitions first (NOT sda1), and defrag windows a few times as well, before installing.

---

### Post by Melhisedek on 2009-07-02
I see, so I can keep C: but have to nuke the other two? Should I put Linux partitions after C: (sda1) or does it really matter at all?

Well that is exactly the way I did it (except that I resized the E: partition and not C: (already had 3 partitions)

I'm afraid it might have to do something with my BIOS, as people report error 18 being caused by BIOS not being able to read so far on the disk during boot session. And solution should be making a small partition called /boot at the beginning of disk (in that case I have to kill whole disk :( )

---

### Post by merlinus on 2009-07-02
Windows should be first, then linux. Keep what you are calling c: (linux does not use drive letters), then create an extended partition, and create logical partitions for ubuntu within that.

You will need about 10G for /, 1.5G for /swap, and about 15G for /home.  I recommend a separate home partition -- it will make reinstalling and installing newer versions much easier, as it will not have to be formatted in future.

You may also wish to make a shared ntfs partition for data that can be used by both windows and ubuntu.

---

### Post by Melhisedek on 2009-07-04
There is some strange kind of bug with my BIOS or so it seems. I had to use a smaller disk and have both Windows and Linux partitions on it and now it works flawlessly. Just have to config my mouse :)

Thank you for your time folks!

---

### Post by ipburbank on 2009-07-04
Yeah, I just switched my BIOS from IDE to AHCI and it worked!
If someone else is having the problems I don't know if it will work for you, but I'd be interested to know either way.

~glad my system is finally installed, Istvan.

---

