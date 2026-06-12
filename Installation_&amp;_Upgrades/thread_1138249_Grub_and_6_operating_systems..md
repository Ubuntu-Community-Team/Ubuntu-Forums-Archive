---
title: "Grub and 6 operating systems."
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Jademalo on 2009-04-26
This is annoying me, i need some help.

Disk 1: Vista

Disk 2: Extended:Section 1: Ubuntu
                 Section 2: Swap
                 Section 3: XP
                 Section 4: Vista
                 Section 5: 7
        Section 2: Data

Disk 3: 7


Can someone make me a menu.lst file that will boot all of these operating systems from GRUB, or tell me another way of going about it and how i can manage to change windows to work that way.

If this sint possible, can someone tell me how i can get this all to boot like this? i suppoise this is a.. sexboot =p

I really want this to work..

Thanks =]

---

### Post by meierfra. on 2009-04-26
In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu or (if you can't  boot into Ubuntu) from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Jademalo on 2009-04-28
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista*** (Acctually this is windows 7)***
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000decff

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   209,712,509   209,712,447   5 Extended
/dev/sda5                 126    18,876,374    18,876,249  83 Linux
/dev/sda6          18,876,438    20,980,889     2,104,452  82 Linux swap / Solaris
/dev/sda7          20,980,953    41,945,714    20,964,762   7 HPFS/NTFS
/dev/sda8          41,945,778   125,837,144    83,891,367   7 HPFS/NTFS
/dev/sda9         125,837,208   209,712,509    83,875,302   7 HPFS/NTFS
/dev/sda2    *    209,712,510   976,768,064   767,055,555   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc0dad61e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   781,420,543   781,418,496   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d031d02

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   160,071,659   160,071,597   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0d1f0d1

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   160,081,919   160,079,872   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 16.0 GB, 16039018496 bytes
75 heads, 40 sectors/track, 10442 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             40    31,326,207    31,326,168   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="141178AE0097C978" LABEL="Scottys Files" TYPE="ntfs" 
/dev/sda5: UUID="4956c49b-4d04-4c25-ad89-bc068169d9ae" TYPE="ext3" 
/dev/sda6: TYPE="swap" LABEL="Ubuntu Linux Sw" UUID="f8040448-39c6-4300-9073-3c8eccb76a80" 
/dev/sda7: UUID="26345B59345B2B57" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda8: UUID="5BC997C42C32E9E3" LABEL="Windows Vista" TYPE="ntfs" 
/dev/sda9: UUID="77BA693C56194822" LABEL="Windows 7" TYPE="ntfs" 
/dev/sdb1: UUID="12185A7C185A5F33" LABEL="Vista (Sata)" TYPE="ntfs" 
/dev/sdc1: UUID="06FCB5A14CADCDBD" TYPE="ntfs" 
/dev/sdd1: UUID="224E81B24E817EF3" LABEL="Backup Disk" TYPE="ntfs" 
/dev/sde1: LABEL="_blank.png^M" UUID="5F10-6054" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/scotty/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=scotty)
/dev/sde1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


=========================== sda5/boot/grub/menu.lst: ===========================

default 1
timeout 20
color cyan/blue blink-white/blue

title Main Operating System:
root

title Windows Vista
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
savedefault
makeactive

title ----------------------
root

title Scotty's Operating Systems:
root

title Ubuntu Linux 9.04
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=4956c49b-4d04-4c25-ad89-bc068169d9ae ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Windows Vista (BOOTMGR)
root (hd0,1)
chainloader +1
savedefault
makeactive


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
UUID=4956c49b-4d04-4c25-ad89-bc068169d9ae /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f8040448-39c6-4300-9073-3c8eccb76a80 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


    .1GB: boot/grub/menu.lst
    .2GB: boot/grub/stage2
   8.5GB: boot/initrd.img-2.6.28-11-generic
   8.6GB: boot/vmlinuz-2.6.28-11-generic
   8.5GB: initrd.img
   8.6GB: vmlinuz

================================ sda2/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(4)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


================================ sdc1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(2)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(2)partition(4)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```






Thats the results of that script. In general, i now have my grub able to boot into all of my operating systems, but its annoying in the way that it works. I can boot into my vista on the other disk from grub, but to boot into my vista/xp/7 i have to load into the windows bootloader.. Is there any way that i can skip that bootloader step and just have all of them in grub by using:

Main operating Systems:
Vista
------
Scottys operating Systems:
Ubuntu
XP
Vista
7

Currently i have:

Main operating Systems:
Vista
------
Scottys operating Systems:
Ubuntu
Vista (BOOTMGR) -------------> XP/Vista/7

That is generally how i would like to ghave it set up..

thanks =]


Also, The only drive i want anything changed on is sda. sdb with the other vista on, i do not want anything changed, and grub seems to be able to boot into that quite happily.

---

### Post by meierfra. on 2009-04-29
[SIZE="4"][COLOR=blue] Boot into Vista on the 500GB drive[/COLOR][/SIZE]


** Step 1 Edit the Vista boot loader **

Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter". This will open a Vista  command line as an administrator. Type



```
  
bcdedit /set {bootmgr} device boot

```


[SIZE="4"][COLOR=blue] Boot into Ubuntu.[/COLOR][/SIZE]
 and open a terminal.


** Step 2 Add Vista,XP and  7 to "menu.lst" **

Open menu.lst via


```
gksudo gedit /boot/grub/menu.lst
```

Add the following to the end of the file:

title Scotty's XP
rootnoverify (hd0,6)
chainloader +1

title Scotty's Vista
rootnoverify (hd0,7)
chainloader +1

title Scotty's 7
[noparse]rootnoverify (hd0,8)[/noparse]
chainloader +1

Save the file 

** Step 3  Move the boot files  to  the partitions containing the  OS's**


```

cd /mnt
sudo mkdir {boot,XP,Vista,7}
sudo mount /dev/sda2 boot
sudo mount /dev/sda7 XP
sudo mount /dev/sda8 Vista
sudo mount /dev/sda9 7
sudo cp boot/{boot.ini,ntldr,NTDETECT.COM} XP
sudo cp {boot,Vista}/bootmgr
sudo cp -R  {boot,Vista}/Boot
sudo cp {boot,7}/bootmgr
sudo cp -R  {boot,7}/Boot

```


** Step 4  Fix the XP boot sector **

Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the XP partition (should be  #4) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, 


**Step 5 Make Vista the default boot on the Vista boot menu.**  

Reboot.
Choose "Scotty's  Vista" at the the grub menu. The Vista boot menu should appear.   Open the Vista  command line as above and type

```

bcdedit /set {bootmgr} default {current}
bcdedit /set {bootmgr} timeout 0

```

**Step 6 Make 7 the default boot on the 7 boot menu.**  

Reboot.

Choose "Scotty's 7"  at the grub menu. The  Windows 7 boot menu will
appear. Boot into 7.  Open the 7 command line as above and type

```

bcdedit /set {bootmgr} default {current}
bcdedit /set {bootmgr} timeout 0

```


If everything went well, you should now be able to boot into all your OSs directly from the Grub menu.

---

