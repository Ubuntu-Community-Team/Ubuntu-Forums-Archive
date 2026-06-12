---
title: "Failed installation, grub and disk unusable"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by cyaquino on 2009-08-26
[FONT=Verdana]I have a notebook with XP and Fedora 11, and I tried to install Ubuntu 9.04 from the live CD, on top of Fedora, and after the installation failed (88%), now when I restart it goes directly to grub, as if the MBR were broken...[/FONT]
 
[FONT=Verdana]Ubuntu said the disk had:[/FONT]
[FONT=Verdana]/dev/sda1 ntfs   4795MB   (Lenovo 3000 rescue hidden partition)[/FONT]
[FONT=Verdana]/dev/sda2 ntfs 68157MB   (Win XP SP3 partition)[/FONT]
[FONT=Verdana]/dev/sda3 ext3    205MB   (¿for grub?)[/FONT]
[FONT=Verdana]/dev/sda5        46859MB   (Fedora 11)[/FONT]
 
Booting again and entering grub commands in a terminal gives different numeric errors. Any clue please?

---

### Post by cyaquino on 2009-08-26
[COLOR=#1f497d][COLOR=#000000][SIZE=2]Also fails with:[/SIZE][SIZE=2]grub> rootnoverify (hd0,2)[/SIZE][SIZE=2]grub> makeactive[/SIZE][SIZE=2]grub> chainloader +1[COLOR=#1f497d]    => Error 13: invalid or unsupported executable format[/COLOR][/SIZE][COLOR=#1f497d][SIZE=2]and also with:[/SIZE][/COLOR][COLOR=#1f497d][SIZE=2][COLOR=#000000]root (hd0,3)[/COLOR][/SIZE][SIZE=2][COLOR=#000000]Filesystem type is ext2fs, partition type 0x83[/COLOR][COLOR=#1f497d]       => Error 27: unrecognized command[/COLOR][/SIZE][FONT=Times New Roman][SIZE=2][COLOR=#000000] [/COLOR][/SIZE][/FONT]
[/COLOR][/COLOR][/COLOR]

---

### Post by ronparent on 2009-08-26
If you are trying to boot xp, the correct root is (hd0,1) - ie /dev/sda2. The MBR is not broken but tries to find the stage1 and stage2 files in /boot/grub on the drive that grub is installed on. If you tried to install with the reformat option selected, you may have wiped out grub. You have to boot to the live cd and try to locate the /grub/stage1 file or the /boot/grub/stage1 file if any exist. I don't know the current status of your grub, but you will get nowhere trying to use it if it doesn't exist where the MBR directs you to.

---

### Post by presence1960 on 2009-08-26
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by cyaquino on 2009-08-27
Ok, here goes RESULTS.txt:
```
 
============================= Boot Info Summary: ==============================
 => Grub0.97 is installed in the MBR of /dev/sda and looks at sector 142759401 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sda. Stage2 looks on partition #3 for /grub/grub.conf.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd
sda2: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       126953112 sectors, but according to the info from 
                       fdisk, it has 133120000 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
sda3: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda4: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab
sdb1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros, 234441648 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xb495e3a4
Partition  Boot         Start           End          Size  Id System
/dev/sda1               2,048     9,367,551     9,365,504  27 Hidden HPFS/NTFS
/dev/sda2           9,381,960   142,501,959   133,120,000   7 HPFS/NTFS
/dev/sda3    *    142,512,615   142,914,239       401,625  82 Linux swap / Solaris
/dev/sda4         142,914,240   234,436,544    91,522,305   5 Extended
/dev/sda5         142,914,303   234,436,544    91,522,242  8e Linux LVM

Drive: sdb ___________________ _____________________________________________________
Disco /dev/sdb: 16.1 GB, 16131293184 bytes
25 cabezas, 25 sectores/pista, 50410 cilindros, 31506432 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x04030201
Partition  Boot         Start           End          Size  Id System
/dev/sdb1               2,048    31,506,431    31,504,384   b W95 FAT32

blkid -c /dev/null: ____________________________________________________________
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D84A0D7C4A0D58A0" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda2: UUID="AA2CAB4E2CAB13FB" LABEL="CHYN05" TYPE="ntfs" 
/dev/sda3: UUID="69f3680e-85f9-43c1-b924-ded41d214033" TYPE="swap" 
/dev/sda5: UUID="d682b85a-71f6-4a64-8e2e-e21f84007f14" TYPE="ext4" 
/dev/mmcblk0p1: SEC_TYPE="msdos" LABEL="YAQUINO" UUID="6269-4304" TYPE="vfat" 
/dev/sdb1: LABEL="KINGSTON" UUID="3433-3231" TYPE="vfat" 
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
/dev/mmcblk0p1 on /media/YAQUINO type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================ sda2/boot.ini: ================================
[boot loader]
timeout=20
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=FOTNWB
=============================== sda5/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=d682b85a-71f6-4a64-8e2e-e21f84007f14 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=69f3680e-85f9-43c1-b924-ded41d214033 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sda5: Location of files loaded by Grub: ===================

  74.9GB: boot/grub/stage2
 116.9GB: boot/initrd.img-2.6.28-11-generic
  76.8GB: boot/vmlinuz-2.6.28-11-generic
 116.9GB: initrd.img
  76.8GB: vmlinuz 

```

---

### Post by presence1960 on 2009-08-27
Your GRUB is not set up correctly, but even if it were you have no menu.lst on your Ubuntu partition (sda5). Your GRUB points to sda3 which is swap. That is not good. You can try to fix it, personally I would reinstall Ubuntu. When you get to the Ready to install window click the Advanced tab and choose to install GRUB to /dev/sda which will put GRUB on the MBR and will autodetect your windows OS. Below is a screenshot of that window:

---

### Post by ronparent on 2009-08-27
+1

Presence1960 is right. Your installation did not complete and grub (which is installed last) evidently was not installed. Although that could be installed manually, there is likelyhood that something else is also incomplete. Your best bet is to reinstall.

---

### Post by cyaquino on 2009-08-27
Ok, just one thing. The installer tries to create a new Ubuntu instead of replacing the one existing. It has modified the partition table adding a #6 ext3 and a #7 swap.
How do I get the replacement of the existing Ubuntu? Should I select to manually assign partitions? (there was my first mistake...)

---

### Post by ronparent on 2009-08-27
Select manual. Don't expect to control the partition numbering. Depending on the state you left it in, just try to select the partitions you tired to install to previously.

Note - you may want to make the swap on a partition within the extended partition. Since you are limited to four primary partitions, counting the extended as a primary, in case you should want to install win 7. :)

---

### Post by cyaquino on 2009-08-27
:( After a long reinstallation, a window appears: 
 
**Cannot install GRUB on /dev/sda **
**Execution of grub-install /dev/sda failed. **
**Fatal error.**
 
When accepted, it goes on to the "Live session user"
 
Then a crash report window appears, related to "**ubiquity**" application.
 
After restart, it comes to the **grub>** prompt, expecting something as first.
 
I put the mount point **/ **on sda5 and told to install grub on /dev/sda where MBR should be.
 
Thanks for any clue!
 
Five days without help. Should I boot from a Windows utilities disk and try to repair the MBR?

---

### Post by presence1960 on 2009-08-27
> **cyaquino said:**
> :(  After a long reinstallation, a window appears: 
 
**Cannot install GRUB on /dev/sda **
**Execution of grub-install /dev/sda failed. **
**Fatal error.**
 
When accepted, it goes on to the "Live session user"
 
Then a crash report window appears, related to "**ubiquity**" application.
 
I put the mount point / on sda5 and told to install grub on /dev/sda
 
Thanks for any clue!

"After a long installation" is a telling sign, you definitely have other problems going on. Ubuntu should never be a long installation. Without more info I would look into your hard disk and/or memory. There definitely is something else going on there preventing the install of GRUB to sda and the long installation also is not a good sign.

---

### Post by ronparent on 2009-08-27
In case of miscommunication, the grub program itself normally installs to /boot/grub within the filesystem on sda5. The bootloader for grub is installed to the MBR of sda. Can you verify the existence of /boot/grub/ plus the stage1, stage2 etc. at that location? Do you know how to navigate to the location of the file system on sda5?

---

### Post by cyaquino on 2009-09-02
:D I finally made it! With an utility disk I removed the wrong Active flag (set to the swap partition!), and marked the XP as primary active. So I recovered the XP boot. Then I removed the additional Linux partitions and last I proceeded with a fresh Ubuntu installation.
Now I'm dealing with the configuration details...

---

