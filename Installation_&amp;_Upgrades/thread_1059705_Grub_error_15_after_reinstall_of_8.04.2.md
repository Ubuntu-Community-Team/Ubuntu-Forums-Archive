---
title: "Grub error 15 after reinstall of 8.04.2"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by vanhelmont on 2009-02-04
I tried to install 8.04.2 on a system that was working with 8.10.  
/boot is /dev/sda1
/home is /dev/sda2
/ is /dev/sda3
I didn't let it reformat /home
After installing from a cd and rebooting, i got "error 15"

Some of what I would expect to find in /boot isn't there:

~$ sudo mount -t ext3 /dev/sda1 bootpart

~$ ls -l bootpart

total 3607

-rw-r--r-- 1 root root  420395 2008-11-27 20:56 abi-2.6.24-23-generic

-rw-r--r-- 1 root root   74166 2008-11-27 20:56 config-2.6.24-23-generic

drwx------ 2 root root   12288 2009-02-03 15:04 lost+found

-rw-r--r-- 1 root root  103204 2007-09-28 11:03 memtest86+.bin

-rw-r--r-- 1 root root 1153225 2008-11-27 20:56 System.map-2.6.24-23-generic
-rw-r--r-- 1 root root 1907096 2008-11-27 20:56 vmlinuz-2.6.24-23-generic


so I tried to reinstall grub, but it doesn't think I have the partition /boot is on:
~$ grub

Probing devices to guess BIOS drives. This may take a long time.



       [ Minimal BASH-like line editing is supported.   For

         the   first   word,  TAB  lists  possible  command

         completions.  Anywhere else TAB lists the possible

         completions of a device/filename. ]

grub> root (hd0,0)

root (hd0,0)



Error 21: Selected disk does not exist

grub> quit

quit


I ran a couple of diagnostic things somebody had suggested for a similar problem:

~$ sudo fdisk -lu



Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0xab0a1495



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *          63      208844      104391   83  Linux

/dev/sda2          208845    82124279    40957717+  83  Linux

/dev/sda3        82124280   102607154    10241437+  83  Linux

/dev/sda4       102607155   135363689    16378267+   5  Extended

/dev/sda5       102607218   112840559     5116671   83  Linux

/dev/sda6       112840623   114880814     1020096   82  Linux swap / Solaris

/dev/sda7       114880878   135363689    10241406   83  Linux


~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

GRUB 


~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'

ff00



Any advice would be appreciated!

---

### Post by caljohnsmith on 2009-02-04
So it looks like for some reason Grub was not installed when you installed 8.04.2; any idea why? Did you change any of the settings under the "Advanced" button in the final stage of installation? It's possible to install Grub manually afterwards, but it is usually more trouble than it is worth if you can instead get Grub to install properly when you install Ubuntu. Also, did you get any errors during or after the installation was completed?

---

### Post by vanhelmont on 2009-02-04
Yes, from everything I can tell, grub did not install:(

and I have no idea why.  The only nonstandard thing I did was manual partitioning.  It formatted /boot and / partitions.  I checked the disk, and it has no errors.  I redid the install with exactly the same results.  I've tried to install grub from the live cd, and even when I mount and chroot to the hd grub can't find the hd (even though mount, fdisk, etc can).

There were no errors during the install, and the only errors afterward are the grub errors.

---

### Post by caljohnsmith on 2009-02-04
Before we try the manual method of installing Grub, I think it would help to get more info about your system, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and give us some idea if manually installing Grub will make sense at this point.

---

### Post by vanhelmont on 2009-02-04
Here are the contents of RESULTS.txt:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora Core release 2 
                       (Tettnang) Kernel on an
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xab0a1495

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       208,844       208,782  83 Linux
/dev/sda2             208,845    82,124,279    81,915,435  83 Linux
/dev/sda3          82,124,280   102,607,154    20,482,875  83 Linux
/dev/sda4         102,607,155   135,363,689    32,756,535   5 Extended
/dev/sda5         102,607,218   112,840,559    10,233,342  83 Linux
/dev/sda6         112,840,623   114,880,814     2,040,192  82 Linux swap / Solaris
/dev/sda7         114,880,878   135,363,689    20,482,812  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="a8fa4d7c-9536-484c-809a-02f24a4cc85c" TYPE="ext3" 
/dev/sda2: LABEL="/home" UUID="945b0a1d-86f8-4d92-b247-f46fd5a71915" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="6354ec54-c649-4355-b54f-c8bcc833c25c" TYPE="ext3" 
/dev/sda5: UUID="d9841b02-ee6e-4070-895e-c52499ea11dc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="360dcd62-d970-4477-ae97-2ff2d317f2c8" 
/dev/sda7: LABEL="/1" UUID="1a4c7a5b-ee44-4f35-94a7-b65bacedc3ee" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /home/ubuntu/bootpart type ext3 (rw)
/dev/sda3 on /mnt/root type ext3 (rw)
none on /mnt/root/proc type proc (rw)
/dev on /mnt/root/dev type none (rw,bind)

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: vmlinuz-2.6.24-23-generic

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6354ec54-c649-4355-b54f-c8bcc833c25c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=a8fa4d7c-9536-484c-809a-02f24a4cc85c /boot           ext3    relatime        0       2
# /dev/sda2
UUID=945b0a1d-86f8-4d92-b247-f46fd5a71915 /home           ext3    relatime        0       2
# /dev/sda5
UUID=d9841b02-ee6e-4070-895e-c52499ea11dc /usr/local      ext3    relatime        0       2
# /dev/sda6
UUID=360dcd62-d970-4477-ae97-2ff2d317f2c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=============================== sda7/etc/fstab: ===============================

LABEL=/1                /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
none                    /dev/pts                devpts  gid=5,mode=620  0 0
none                    /dev/shm                tmpfs   defaults        0 0
LABEL=/home             /home                   ext3    defaults        1 2
none                    /proc                   proc    defaults        0 0
none                    /sys                    sysfs   defaults        0 0
/dev/hda6               swap                    swap    defaults        0 0
/dev/cdrom              /mnt/cdrom              udf,iso9660 noauto,owner,kudzu,ro 0 0
/dev/cdrom1             /mnt/cdrom1             udf,iso9660 noauto,owner,kudzu,ro 0 0
/dev/fd0                /mnt/floppy             auto    noauto,owner,kudzu 0 0
none                    /var/lib/jack/tmp       tmpfs   defaults         0 0

=============================== StdErr Messages: ===============================

sed: can't read sda5/etc/issue: No such file or directory
```

Thanks!

---

### Post by caljohnsmith on 2009-02-04
From the script results and also from your first post, it looks like you are also missing an initrd-2.6.24-23-generic image to go with your vmlinuz-2.6.24-23-generic kernel. So I think there could have been more that went wrong with your install than just not having Grub installed. Do you have to have a boot partition? I think you might have better luck if you install without a boot partition. Or maybe it would help to try installing with the Alternate 8.04.2 CD instead.

---

### Post by vanhelmont on 2009-02-04
Thanks, it works now, but I don't know why!

I deleted my old sda7 partition, made a new partition from that plus the extra space at the end of the disk, and installed on that without /boot or /home partitions.  

Some Linux book I read several years ago talked about partitioning, and suggested a /boot partition, but I don't recall any reason.  I will try again later with my /home partition, just to see if it works.

---

### Post by caljohnsmith on 2009-02-04
Glad to hear you finally have a successful install. Let me know if you are successful installing with a home partition too, I would be interested.

---

