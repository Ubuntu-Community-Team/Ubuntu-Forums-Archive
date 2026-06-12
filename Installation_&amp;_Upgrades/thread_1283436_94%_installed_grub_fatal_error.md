---
title: "94% installed grub fatal error"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by vkd on 2009-10-05
1. I am a complete new to linux but good at windows.
2. I am installing from a cd and without installation it works fine from cd.
3. When I install it goes as far as 94% and then boom!! Grub problem.
4. tried different partitions to install but result is the same.
5. 64 bit computer with 4 gig ram intel duo chip

here I ran the script "boot_info_script032"

results is: 
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 1005. But according to the info from fdisk, 
                       sda7 starts at sector 213135360.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00015841

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    10,233,404    10,233,342   7 HPFS/NTFS
/dev/sda2          10,233,405 2,930,272,064 2,920,038,660   f W95 Ext d (LBA)
/dev/sda5          10,233,468    71,665,964    61,432,497   7 HPFS/NTFS
/dev/sda6          71,666,028   213,131,922   141,465,895   7 HPFS/NTFS
/dev/sda7         213,135,360 1,532,602,367 1,319,467,008   7 HPFS/NTFS
/dev/sda8       1,532,604,416 2,909,321,772 1,376,717,357   7 HPFS/NTFS
/dev/sda9       2,929,886,568 2,930,272,064       385,497  82 Linux swap / Solaris
/dev/sda10      2,909,323,368 2,929,886,504    20,563,137  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="42F0D30FF0D30855" LABEL="XP" TYPE="ntfs" 
/dev/sda5: UUID="727C71217C70E0F1" LABEL="Vista64" TYPE="ntfs" 
/dev/sda6: UUID="884C8F984C8F7FA4" LABEL="WIN7" TYPE="ntfs" 
/dev/sda7: UUID="B006D24306D20A6C" LABEL="DATA_0" TYPE="ntfs" 
/dev/sda8: UUID="88E45DE6E45DD6D2" LABEL="DATA_1" TYPE="ntfs" 
/dev/sda9: UUID="a5d501e0-59c1-4cfd-a2cb-e5525e97eed5" TYPE="swap" 
/dev/sda10: UUID="80411439-7202-41de-8859-6406fa735741" TYPE="ext3" 

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
/dev/sda10 on /target type ext3 (rw,relatime,errors=remount-ro)
/proc on /target/proc type none (rw,bind)
/dev on /target/dev type none (rw,bind)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=80411439-7202-41de-8859-6406fa735741 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=a5d501e0-59c1-4cfd-a2cb-e5525e97eed5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda10: Location of files loaded by Grub: ===================


1496.6GB: boot/grub/stage2
1496.8GB: boot/initrd.img-2.6.28-11-generic
1496.7GB: boot/vmlinuz-2.6.28-11-generic
1496.8GB: initrd.img
1496.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 


Please if some kind soul spoonfeed me to install "step by step"
:)

---

### Post by vkd on 2009-10-05
any comments??

---

### Post by oldfred on 2009-10-05
Your results.txt looks like it is missing the obvious, no grub. If you only got to 94% I do not know what else has to be installed. 

Did you burn the CD at the slowest speed possible. Even if the LiveCD worked it may still of had a problem.

Some have reported success with the text only alternative installed. It is the same without the graphical interface and not a live CD.
[http://www.ubuntulinux.org/getubuntu/downloadmirrors#alternate](http://www.ubuntulinux.org/getubuntu/downloadmirrors#alternate)

---

### Post by vkd on 2009-10-05
Thanks Oldfred
downloading now and will post later with the results. & thanks again for taking time to reply

---

### Post by binary00mind on 2009-10-05
Hi vkd 
You asked for comments so I give you one. 
What I gather from your attachment you either have 2 Windows OS's XP Pro & Vista (which is unlikely since Vista would refuse to install on logical drive) or you erased Vista and installed XP Pro in place. 
Also from your attachment looks like you have corrupted MBR, look at  /sda5 /sda6 and /sda7
>  => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 1005. But according to the info from fdisk, 
                       sda7 starts at sector 213135360.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________
The XP Pro is on the first partition /sda1 and has Vista type NTFS file system but the operating system is XP Pro with boot.ini 
which under Vista one won't find boot.ini in the regular spot. 
My question to you is, during the grub install, there is a question if all operating system(s) were/are detected correctly. 
Have You seen your existing operating system(s)? (I mean Windows OS's) and if so, what did you see? 
Personally I've never had installed XP Pro with Vista NTFS file system nor Vista & XP side by side. 
I am guessing here. but by all means try oldfred method with the alternate text CD installer which is much better installation and see what happens.

---

### Post by vkd on 2009-10-05
Hi binary00mind
 
Thanks for your remarks:
 
1. Xp was installed first. vista 64 second & win7 last. All are working fine. It is 1.5 tb disk and has 5 partitions besides ext3 partitions. 3 have systems while 2 600gb each is data0 & data1. then the bug hit me to try linux. little help from google & decided on ubuntu. Last 15 gb went to ubuntu.
 
2. in partioning phase of installations I could see all the partitions & sys disks. Only one is primary & rest are all logical partitions. primary has xpp on it.
 
3. grub did not install at all. configuring hardware step excuted flawlessly & then fatal error. "can not install grub" no remarks were there.. I tried to install in advance options on all the partitions including the primary one and it always stopped at 94%. 
 
I welcome more remarks .

---

### Post by oldfred on 2009-10-05
I only have XP, but it is my understanding that Vista  & Win7 do something to combine the boot into one and then let you select which windows to boot. Often people delete a windows install partiton and their other windows will not boot at all, because the boot with the combined win boot was erased. Normally with Ubuntu you can chainboot directly into each windows install, but because of the combined windows boot you may only be able to boot to the combined win boot and then choose which windows to boot.

If your other windows installs are in extended partitions you have the workaround to allow extended partitions. We normally say to only have windows in a primary partitionm because it will not boot from an extended. You are actually booting all 3 from the one primary.

I would suggest not to ever delete your winxp without a lot of planning and backup.

---

### Post by binary00mind on 2009-10-05
Thanks vkd

Now the picture looks much better and more clear. 

You are going here for the grand slam. 
XP Pro, Vista64, Win7 and now Ubuntu...very interesting. 

Try the alternate text CD installer and in worst case scenario you can install grub on the floppy drive (which I am sure you own one) 
Note during alternate text CD installer, you must configure all mount points and defaults. Which I am also sure that you know about it. 
 
The largest HDD that I've ever owned is 750GB 
So let us know...there are a lot of guys/gals here, ready to help.

---

### Post by vkd on 2009-10-06
No Joy still..

grub installation still not working
tried lilo,  scans bios & hangs
grub will not install on fd0 as well
trying again to clean install on a single disk 80 gb.. will post results in the night dubai time..

---

### Post by vkd on 2009-10-06
mates  !!! giving up.!! will try for more few days from live cd. I find it is nice like old dos days. is fast but on my puter xp is extremely fast.
  btw it does install inside windows as application. 
Thanks for the help.

---

