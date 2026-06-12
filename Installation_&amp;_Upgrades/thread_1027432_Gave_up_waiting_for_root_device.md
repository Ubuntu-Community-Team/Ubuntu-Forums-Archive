---
title: "Gave up waiting for root device"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by milidoni on 2009-01-01
I have installed 8.10 using wubi on my d: drive (I have only one physical drive) and that worked fine. For some reason this drive got corrupted and I had to delete it, reformat it & restore the ubuntu disks (d:\ubuntu\disks) from backup. After the restore I get this error message : Gave up waiting for root device. ALERT! /dev/by-uuid/xxxx does not exist. I tried to modify the menu.lst using root=/dev/sda2/ instead of the UUID but the error is still there. 
Can somebody suggest what to do ?
Thanks
Stelios

---

### Post by caljohnsmith on 2009-01-01
That sounds really strange that Kubuntu was working, but then when you restored the backup it now gives that error. One thing you could try is adding the following at the end of the kernel line:
```
rootdelay=120
```
If that doesn't work, and if you have a Live CD, how about booting that, open a terminal (or Konsole in Kubuntu) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by milidoni on 2009-01-01
I tried the delay option as suggested but things did not change. Please find below the requested output. Please have a look.

Thanks,
Stelios

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks 
                       /ubuntu/disks/boot/ /ubuntu/disks/boot/grub 
                       /ubuntu/disks/boot/grub

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Win_98
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 8064.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa090a090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   104872319    52436128+   7  HPFS/NTFS
/dev/sda2       104872320   114318539     4723110    c  W95 FAT32 (LBA)
/dev/sda3       114318540   312576704    99129082+   f  W95 Ext'd (LBA)
/dev/sda5       114318603   312576704    99129051    7  HPFS/NTFS

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 8006 MB, 8006926336 bytes
16 heads, 32 sectors/track, 30544 cylinders, total 15638528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6de3befc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8064    15638527     7815232    c  W95 FAT32 (LBA)

sfdisk -V /dev/sdb:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="FE54675654671127" LABEL="WIN_XP" TYPE="ntfs" 
/dev/sda2: LABEL="OBIPE" UUID="F003-3A35" TYPE="vfat" 
/dev/sda5: UUID="4A2425222425130D" LABEL="D_DATA" TYPE="ntfs" 
/dev/sdb1: LABEL="KINGSTON" UUID="7DB3-944B" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

C:\OracleOB.dat="OBI Preinstallation Environment"

c:\wubildr.mbr="Ubuntu"


==================== sda5/ubuntu/disks/boot/grub/menu.lst: ====================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

default     0

timeout     10

color cyan/blue white/blue

### BEGIN AUTOMAGIC KERNELS LIST

title    Ubuntu 8.10, kernel 2.6.27-9-generic
root     ()/ubuntu/disks
kernel      /boot/vmlinuz-2.6.27-9-generic root=UUID=AFE19870138EDB39 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash rootdelay=120
## kernel      /boot/vmlinuz-2.6.27-9-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash
initrd      /boot/initrd.img-2.6.27-9-generic

title    Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root     ()/ubuntu/disks
kernel      /boot/vmlinuz-2.6.27-9-generic root=UUID=AFE19870138EDB39 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd      /boot/initrd.img-2.6.27-9-generic

title    Ubuntu 8.10, kernel 2.6.27-7-generic
root     ()/ubuntu/disks
kernel      /boot/vmlinuz-2.6.27-7-generic root=UUID=AFE19870138EDB39 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash
initrd      /boot/initrd.img-2.6.27-7-generic

title    Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root     ()/ubuntu/disks
kernel      /boot/vmlinuz-2.6.27-7-generic root=UUID=AFE19870138EDB39 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd      /boot/initrd.img-2.6.27-7-generic

title    Ubuntu 8.10, memtest86+
root     ()/ubuntu/disks
kernel      /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title    Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title    Microsoft Windows XP Professional
root     (hd0,0)
savedefault
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title    Windows NT/2000/XP
root     (hd0,1)
savedefault
chainloader +1


============================== sda5/ubuntu/disks: ==============================

total 29296888
drwxrwxrwx 1 root root           0 2008-12-31 09:36 .
drwxrwxrwx 1 root root        4096 2008-12-31 09:12 ..
drwxrwxrwx 1 root root        4096 2008-12-31 09:36 boot
-rwxrwxrwx 1 root root 29000000000 2008-12-29 08:03 root.disk
-rwxrwxrwx 1 root root  1000000000 2008-11-30 18:38 swap.disk

=========================== sda5/ubuntu/disks/boot/: ===========================

total 25944
drwxrwxrwx 1 root root    4096 2008-12-31 09:36 .
drwxrwxrwx 1 root root       0 2008-12-31 09:36 ..
-rwxrwxrwx 1 root root  503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rwxrwxrwx 1 root root  503560 2008-11-20 23:30 abi-2.6.27-9-generic
-rwxrwxrwx 1 root root   85316 2008-11-04 20:53 config-2.6.27-7-generic
-rwxrwxrwx 1 root root   85316 2008-11-20 23:30 config-2.6.27-9-generic
drwxrwxrwx 1 root root       0 2008-12-31 09:36 grub
-rwxrwxrwx 1 root root 8921718 2008-11-30 17:09 initrd.img-2.6.27-7-generic
-rwxrwxrwx 1 root root 8923188 2008-12-19 11:34 initrd.img-2.6.27-9-generic
-rwxrwxrwx 1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rwxrwxrwx 1 root root 1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rwxrwxrwx 1 root root 1352144 2008-11-20 23:30 System.map-2.6.27-9-generic
-rwxrwxrwx 1 root root    1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rwxrwxrwx 1 root root    1130 2008-11-20 23:32 vmcoreinfo-2.6.27-9-generic
-rwxrwxrwx 1 root root 2339552 2008-11-04 20:53 vmlinuz-2.6.27-7-generic
-rwxrwxrwx 1 root root 2339712 2008-11-20 23:30 vmlinuz-2.6.27-9-generic

========================= sda5/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2008-12-31 09:36 .
drwxrwxrwx 1 root root 4096 2008-12-31 09:36 ..
-rwxrwxrwx 1 root root  191 2008-11-30 18:43 default
-rwxrwxrwx 1 root root   30 2008-11-30 18:43 device.map
-rwxrwxrwx 1 root root 5466 2009-01-01 16:51 menu.lst
-rwxrwxrwx 1 root root 5154 2008-11-30 17:09 menu.lst~

========================= sda5/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2008-12-31 09:36 .
drwxrwxrwx 1 root root 4096 2008-12-31 09:36 ..
-rwxrwxrwx 1 root root  191 2008-11-30 18:43 default
-rwxrwxrwx 1 root root   30 2008-11-30 18:43 device.map
-rwxrwxrwx 1 root root 5466 2009-01-01 16:51 menu.lst
-rwxrwxrwx 1 root root 5154 2008-11-30 17:09 menu.lst~

=============================== StdErr Messages: ===============================

Unknown MBR on /dev/sdb

00000000  fa be 00 7c bf 00 7a b9  00 01 fc 0e 1f 0e 07 f3  |...|..z.........|
00000010  a5 ea 16 7a 00 00 bb be  7b 33 c9 80 3f 80 75 06  |...z....{3..?.u.|
00000020  fe c5 8b f3 eb 07 80 3f  00 75 02 fe c1 83 c3 10  |.......?.u......|
00000030  81 fb fe 7b 72 e5 83 f9  04 74 0b 81 f9 03 01 74  |...{r....t.....t|
00000040  0a bb a5 7a eb 2c bb 87  7a eb 27 8b 4c 02 8b 14  |...z.,..z.'.L...|
00000050  b8 01 02 bb 00 7c cd 13  73 05 bb bc 7a eb 13 2e  |.....|..s...z...|
00000060  a1 fe 7d 3d 55 aa 74 05  bb bc 7a eb 05 ea 00 7c  |..}=U.t...z....||
00000070  00 00 2e 8a 07 3c 00 74  0c 53 bb 07 00 b4 0e cd  |.....<.t.S......|
00000080  10 5b 43 eb ed eb fe 4e  6f 20 62 6f 6f 74 61 62  |.[C....No bootab|
00000090  6c 65 20 70 61 72 74 69  74 6f 6e 20 69 6e 20 74  |le partiton in t|
000000a0  61 62 6c 65 00 49 6e 76  61 6c 69 64 20 50 61 72  |able.Invalid Par|
000000b0  74 69 74 6f 6e 20 74 61  62 6c 65 00 49 6e 76 61  |titon table.Inva|
000000c0  6c 69 64 20 6f 72 20 64  61 6d 61 67 65 64 20 42  |lid or damaged B|
000000d0  6f 6f 74 61 62 6c 65 20  70 61 72 74 69 74 69 6f  |ootable partitio|
000000e0  6e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |n...............|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  fc be e3 6d 00 00 00 0c  |...........m....|
000001c0  0c 0f 0c 0f e0 4f 80 1f  00 00 80 80 ee 00 00 00  |.....O..........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-01
OK, from your Live CD, how about posting the output of:
```
sudo mount /dev/sda5 /mnt
sudo blkid /mnt/ubuntu/disks/root.disk
```
Also, has your menu.lst always had the "ROOTFLAGS=syncio" with the kernel line?

---

### Post by milidoni on 2009-01-01
Thanks,
Your questions & requests have helped me find the problem. I have changed the menu.lst to root=/dev/sda5 (as I read it in the results.txt) and then I was able to boot to ubuntu! Your second request told me which UUID I should put it the menu.lst. Do I have to update fstub now with this correct UUID ?

```
/mnt/ubuntu/disks/root.disk: UUID="298bc9ae-66d9-40c0-918d-a097910edffa" TYPE="ext3" 

```

---

### Post by caljohnsmith on 2009-01-01
> **milidoni said:**
> Thanks,
Your questions & requests have helped me find the problem. I have changed the menu.lst to root=/dev/sda5 (as I read it in the results.txt) and then I was able to boot to ubuntu! Your second request told me which UUID I should put it the menu.lst. Do I have to update fstub now with this correct UUID ?

```
/mnt/ubuntu/disks/root.disk: UUID="298bc9ae-66d9-40c0-918d-a097910edffa" TYPE="ext3" 

```
Great, you saw where I was headed. :) Yes, you should update the fstab too if the UUID for the root "/" mount point is different than the UUID you show above.

---

### Post by milidoni on 2009-01-01
Thanks a lot,:D
Problem solved. 
On Dec. 30, I had all my code & documents (14 years of work) and ubuntu lost. On January 1st everything is ok. What a great way to start the year.
Thanks again

---

### Post by caljohnsmith on 2009-01-01
> **milidoni said:**
> Thanks a lot,:D
Problem solved. 
On Dec. 30, I had all my code & documents (14 years of work) and ubuntu lost. On January 1st everything is ok. What a great way to start the year.
Thanks again
You're welcome, glad you have it fixed now. I hope you might consider making backups of your important data in Ubuntu so you aren't in any precarious situation like this in the future. Cheers and Happy New Year. :)

---

### Post by ben44b on 2009-01-07
I have the same problem but I can't figure out how to change mine from the above example.

My RESULTS.TXT reads:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    75152069    37576003+  83  Linux
/dev/sda2        75152070    78156224     1502077+   5  Extended
/dev/sda5        75152133    78156224     1502046   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4dda4ad7-95f2-4dd8-ad07-788ca35fc362" TYPE="ext3" 
/dev/sda5: UUID="47859a69-50d1-4965-ae92-f8157af9be48" TYPE="swap" 

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
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bernie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bernie)

=========================== sda1/boot/grub/menu.lst: ===========================

default 0

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
# kopt=root=UUID=4dda4ad7-95f2-4dd8-ad07-788ca35fc362 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=4dda4ad7-95f2-4dd8-ad07-788ca35fc362

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

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=4dda4ad7-95f2-4dd8-ad07-788ca35fc362 ro xforcevesa quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
rootdelay=90

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=4dda4ad7-95f2-4dd8-ad07-788ca35fc362 ro xforcevesa  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=4dda4ad7-95f2-4dd8-ad07-788ca35fc362 ro xforcevesa quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
rootdelay=90

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=4dda4ad7-95f2-4dd8-ad07-788ca35fc362 ro xforcevesa  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4dda4ad7-95f2-4dd8-ad07-788ca35fc362 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=47859a69-50d1-4965-ae92-f8157af9be48 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 23832
drwxr-xr-x  3 root root    4096 2009-01-07 19:26 .
drwxr-xr-x 20 root root    4096 2009-01-06 23:43 ..
-rw-r--r--  1 root root  508385 2008-12-19 12:57 abi-2.6.27-11-generic
-rw-r--r--  1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91358 2008-12-19 12:57 config-2.6.27-11-generic
-rw-r--r--  1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-07 19:15 grub
-rw-r--r--  1 root root 8210415 2009-01-04 00:49 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8208970 2009-01-07 19:26 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1031799 2008-12-19 12:57 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1074 2008-12-19 12:58 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2248912 2008-12-19 12:57 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 232
drwxr-xr-x 2 root root   4096 2009-01-07 19:15 .
drwxr-xr-x 3 root root   4096 2009-01-07 19:26 ..
-rw-r--r-- 1 root root    197 2008-12-31 21:48 default
-rw-r--r-- 1 root root     15 2008-12-31 21:48 device.map
-rw-r--r-- 1 root root   8108 2008-12-31 21:48 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-31 21:48 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-31 21:48 installed-version
-rw-r--r-- 1 root root   8712 2008-12-31 21:48 jfs_stage1_5
-rw-r--r-- 1 root root   3207 2009-01-07 19:15 menu.lst
-rw-r--r-- 1 root root   3181 2009-01-05 23:04 menu.lst~
-rw-r--r-- 1 root root   4853 2009-01-04 18:04 menu.lst.backup
-rw-r--r-- 1 root root   4853 2009-01-04 17:55 menu.lst_original
-rw-r--r-- 1 root root   7352 2008-12-31 21:48 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-31 21:48 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-31 21:48 stage1
-rw-r--r-- 1 root root 121460 2008-12-31 21:48 stage2
-rw-r--r-- 1 root root   9556 2008-12-31 21:48 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

Any help would be appreciated.

---

### Post by caljohnsmith on 2009-01-07
Ben44b, so are you getting an "ALERT! /dev/by-uuid/xxxx does not exist" error? If so, how about doing the following from your Live CD:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change the first Ubuntu entry to add "rootdelay=120" at the end of the kernel line, and also replace the "rootdelay=90" at the end of the entry with "quiet" like:
```
title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=4dda4ad7-95f2-4dd8-ad07-788ca35fc362 ro xforcevesa quiet splash [COLOR="Red"]rootdelay=120[/COLOR]
initrd /boot/initrd.img-2.6.27-11-generic
[COLOR="Red"]quiet[/COLOR]
```
Next reboot, select the first Ubuntu entry in your Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by ben44b on 2009-01-07
Thanks for the reply CalJohnS.

My Ubuntu loaded correctly for the 1st time in a long time.

Is there anything else I should do?


Thanks.

---

### Post by ben44b on 2009-01-07
test

---

### Post by caljohnsmith on 2009-01-08
> **ben44b said:**
> Thanks for the reply CalJohnS.

My Ubuntu loaded correctly for the 1st time in a long time.

Is there anything else I should do?


Thanks.
Glad to hear that worked to boot Ubuntu OK; one last thing you could do would be to add the "rootdelay=120" to your default kernel options line in your menu.lst, that way when you get a kernel upgrade, the same rootdelay will be automatically added to the kernel line in your menu.lst. But it's up to you whether you want to do that or not, because it might be that a newer kernel won't have the same problem; therefore you might not need to add the rootdelay. I think if I were in your shoes, I would choose not to have the rootdelay added by default, because you can always add it after-the-fact if you find the newer kernel has the same booting problem. But if you would rather have the rootdelay added to help ensure you don't have any problems with a newer kernel, you could first do:
```
gksudo gedit /boot/grub/menu.lst
```
That will pull up your menu.lst, and then at the end of the "# defoptions" line add:
```
# defoptions=quiet splash [COLOR="Blue"]rootdelay=120[/COLOR]
```
Anyway, cheers and have fun with Ubuntu. :)

---

### Post by jrarrmy on 2009-01-08
Hey everyone, I'm quite new to this, but just bought and assembled a brand new system with core 2 duo and biostar motherboard. I ran unetbootin to install ubuntu to this fresh system. 

So, I'm also getting this gave up waiting message. Tried changing the rootdelay to 120 same error comes back.

"- Boot args (cat /proc/cmdline)
  - check rootdelay= (did the system wait long enough?)
  - check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! does not exist. Dropping to a shell!"

Is there anything I should be changing my root to?


Thank-you

---

### Post by caljohnsmith on 2009-01-08
Jrarrmy, in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by jrarrmy on 2009-01-08
Hey Cal, 

I don't suppose what you're suggesting can be done with just the usb? I don't have a cd drive installed on this system, I suppose I could, but I didn't bother after burning a copy of the install cd didn't work.

Also, I don't think there is a desktop or even internet capability without an operating system yet right?

---

### Post by jrarrmy on 2009-01-08
The weirdest thing just happened, I was trying to reset the computer so I could hit f1 or esc to get into cmos bios setup and check if it still had the right hard drive boot info, seeing as boot scsi things had come up which looked like a problem.  So I missed those settings and it went into the unet startup again but I still hit esc and f1. The screen went black and said boot: then went back to the unet startup screen again, and while I was on this other computer looking for answers it just decided to run without enter being pushed and that loaded right into what I assume is Ubuntu desktop...

crazy. hopefully that means it's ok? I guess I can skip forward to the next install steps, or will that mysterious problem cause issues again in the future?

---

### Post by jrarrmy on 2009-01-08
Wow that was crazy easy and fast once I got past that confusing seemingly unnecessary point. I'm now online on the Ubuntu system.

---

### Post by ben44b on 2009-01-08
My ubuntu did load correctly but it is still not loading I would say normally. It still takes a while after GRUB loading...and then I still have to choose from a list which kernel to load. I would like to reinstall Ubuntu but my hard drive is still not detected.  ?


Thanks

---

### Post by caljohnsmith on 2009-01-08
> **ben44b said:**
> My ubuntu did load correctly but it is still not loading I would say normally. It still takes a while after GRUB loading...and then I still have to choose from a list which kernel to load. I would like to reinstall Ubuntu but my hard drive is still not detected.  ?

Thanks
Are you referring to your 40 GB HDD that currently has Ubuntu? If so, what exactly do you mean when you say the HDD is not detected?

---

### Post by ben44b on 2009-01-08
When I turn on my computer, it doesn't detect a hard drive so it begins to search for a network. (CLIENT MAC ADDRESS with a spinning thing)

I have to CTRLALTDEL, and then it finds GRUB. Then it takes a while and I'm presented with the list of kernels to load. I have to do this every time for Ubuntu to work.

??

---

### Post by caljohnsmith on 2009-01-08
> **ben44b said:**
> When I turn on my computer, it doesn't detect a hard drive so it begins to search for a network. (CLIENT MAC ADDRESS with a spinning thing)

I have to CTRLALTDEL, and then it finds GRUB. Then it takes a while and I'm presented with the list of kernels to load. I have to do this every time for Ubuntu to work.

??
That sounds like an issue with your BIOS boot order; I would go into your BIOS and make sure the HDD is before any network devices in your BIOS boot order.

---

### Post by ben44b on 2009-01-08
OK. Went into BIOS and the boot order is ok. I disabled the network pre-loaded environment whatever so now it doesn't look for a network. 

If I power on my computer it says no operating system found; but then if I CTRL+ALT+DEL to restart, it'll say GRUB loading. But again very slowly...

?

---

### Post by caljohnsmith on 2009-01-09
> **ben44b said:**
> OK. Went into BIOS and the boot order is ok. I disabled the network pre-loaded environment whatever so now it doesn't look for a network. 

If I power on my computer it says no operating system found; but then if I CTRL+ALT+DEL to restart, it'll say GRUB loading. But again very slowly...

?
So which is the first drive in your BIOS boot order? Is it a CD/DVD drive, and if so, which place is your HDD in? It still sounds like you might have an issue with the booting order of drives, so please let me know how you have your BIOS boot order currently set up.

---

### Post by ben44b on 2009-01-09
Ok. Went back into the BIOS and found how to see my boot order (F12)
The order was:

1. +Removable drives
2. +hard drive
3. cd/rom
4. network.

If this is the problem, how do I change the order?


Thanx

---

### Post by caljohnsmith on 2009-01-09
> **ben44b said:**
> Ok. Went back into the BIOS and found how to see my boot order (F12)
The order was:

1. +Removable drives
2. +hard drive
3. cd/rom
4. network.

If this is the problem, how do I change the order?


Thanx
I would set your CD/DVD drive as first in the BIOS boot order, and then let the hard drive be second. After that you could have the removable and network drives. How about trying that, and let me know if you still get the no operating system found error.

---

### Post by Jexel on 2009-01-09
I have the same issue. Can somebody let me know what I should do?

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05560555

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62916607    31457280    7  HPFS/NTFS
/dev/sda2       104859648   781420543   338280448    7  HPFS/NTFS
/dev/sda3        62926605   103024844    20049120   83  Linux
/dev/sda4       103024845   104856254      915705    5  Extended
/dev/sda5       103024908   104856254      915673+  82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: partition 2 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6C78DB7978DB408E" TYPE="ntfs" 
/dev/sda2: UUID="A212E22012E1F965" TYPE="ntfs" 
/dev/sda3: UUID="4d3dd97d-7535-40e6-8be7-8a25f858c3fe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="d82e885c-ae9d-4738-b10e-864884bde59f" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================== sda1/Boot: ==================================

total 536
drwxrwxrwx 1 root root   4096 2008-03-20 19:11 .
drwxrwxrwx 1 root root  20480 2009-01-09 13:07 ..
-rwxrwxrwx 1 root root  24576 2009-01-09 15:57 BCD
-rwxrwxrwx 1 root root  21504 2009-01-09 15:47 BCD.LOG
-rwxrwxrwx 2 root root      0 2007-11-18 04:53 BCD.LOG1
-rwxrwxrwx 2 root root      0 2007-11-18 04:53 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2007-11-18 04:53 bootstat.dat
drwxrwxrwx 1 root root      0 2008-03-20 19:11 cs-CZ
drwxrwxrwx 1 root root      0 2008-03-20 19:11 da-DK
drwxrwxrwx 1 root root      0 2008-03-20 19:11 de-DE
drwxrwxrwx 1 root root      0 2008-03-20 19:11 el-GR
drwxrwxrwx 1 root root      0 2008-03-20 19:11 en-US
drwxrwxrwx 1 root root      0 2008-03-20 19:11 es-ES
drwxrwxrwx 1 root root      0 2008-03-20 19:11 fi-FI
drwxrwxrwx 1 root root      0 2008-03-20 19:11 Fonts
drwxrwxrwx 1 root root      0 2008-03-20 19:11 fr-FR
drwxrwxrwx 1 root root      0 2008-03-20 19:11 hu-HU
drwxrwxrwx 1 root root      0 2008-03-20 19:11 it-IT
drwxrwxrwx 1 root root      0 2008-03-20 19:11 ja-JP
drwxrwxrwx 1 root root      0 2008-03-20 19:11 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-03-20 19:11 nb-NO
drwxrwxrwx 1 root root      0 2008-03-20 19:11 nl-NL
drwxrwxrwx 1 root root      0 2008-03-20 19:11 pl-PL
drwxrwxrwx 1 root root      0 2008-03-20 19:11 pt-BR
drwxrwxrwx 1 root root      0 2008-03-20 19:11 pt-PT
drwxrwxrwx 1 root root      0 2008-03-20 19:11 ru-RU
drwxrwxrwx 1 root root      0 2008-03-20 19:11 sv-SE
drwxrwxrwx 1 root root      0 2008-03-20 19:11 tr-TR
drwxrwxrwx 1 root root      0 2008-03-20 19:11 zh-CN
drwxrwxrwx 1 root root      0 2008-03-20 19:11 zh-HK
drwxrwxrwx 1 root root      0 2008-03-20 19:11 zh-TW

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4d3dd97d-7535-40e6-8be7-8a25f858c3fe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4d3dd97d-7535-40e6-8be7-8a25f858c3fe ro quiet splash rootdelay=120
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4d3dd97d-7535-40e6-8be7-8a25f858c3fe ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=4d3dd97d-7535-40e6-8be7-8a25f858c3fe ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=4d3dd97d-7535-40e6-8be7-8a25f858c3fe ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-8-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=4d3dd97d-7535-40e6-8be7-8a25f858c3fe ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=4d3dd97d-7535-40e6-8be7-8a25f858c3fe ro  single
initrd		/boot/initrd.img-2.6.27-8-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4d3dd97d-7535-40e6-8be7-8a25f858c3fe ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4d3dd97d-7535-40e6-8be7-8a25f858c3fe ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4d3dd97d-7535-40e6-8be7-8a25f858c3fe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d82e885c-ae9d-4738-b10e-864884bde59f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1 /media/sda1 ntfs-3g defaults,umask=007,gid=46 0 0
/dev/sda2 /media/sda2 ntfs-3g defaults,umask=007,gid=46 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,umask=007,gid=46 0 0

================================== sda3/boot: ==================================

total 47168
drwxr-xr-x  3 root root    4096 2009-01-06 02:43 .
drwxr-xr-x 21 root root    4096 2009-01-09 13:07 ..
-rw-r--r--  1 root root  507990 2008-11-21 13:46 abi-2.6.27-10-generic
-rw-r--r--  1 root root  508385 2008-12-19 17:57 abi-2.6.27-11-generic
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507735 2008-11-06 19:20 abi-2.6.27-8-generic
-rw-r--r--  1 root root   91358 2008-11-21 13:46 config-2.6.27-10-generic
-rw-r--r--  1 root root   91358 2008-12-19 17:57 config-2.6.27-11-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-06 19:20 config-2.6.27-8-generic
drwxr-xr-x  2 root root    4096 2009-01-10 00:54 grub
-rw-r--r--  1 root root 8125942 2008-11-29 14:38 initrd.img-2.6.27-10-generic
-rw-r--r--  1 root root 8128385 2009-01-06 02:43 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8104377 2008-11-06 00:19 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8124874 2008-11-18 08:32 initrd.img-2.6.27-8-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029828 2008-11-21 13:46 System.map-2.6.27-10-generic
-rw-r--r--  1 root root 1031799 2008-12-19 17:57 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029612 2008-11-06 19:20 System.map-2.6.27-8-generic
-rw-r--r--  1 root root    1074 2008-11-21 13:48 vmcoreinfo-2.6.27-10-generic
-rw-r--r--  1 root root    1074 2008-12-19 17:58 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-06 19:22 vmcoreinfo-2.6.27-8-generic
-rw-r--r--  1 root root 2247280 2008-11-21 13:46 vmlinuz-2.6.27-10-generic
-rw-r--r--  1 root root 2248912 2008-12-19 17:57 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-06 19:20 vmlinuz-2.6.27-8-generic

=============================== sda3/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2009-01-10 00:54 .
drwxr-xr-x 3 root root   4096 2009-01-06 02:43 ..
-rw-r--r-- 1 root root    197 2008-07-12 07:40 default
-rw-r--r-- 1 root root     15 2008-07-12 07:40 device.map
-rw-r--r-- 1 root root   8056 2008-07-12 07:40 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-07-12 07:40 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-07-12 07:40 installed-version
-rw-r--r-- 1 root root   8608 2008-07-12 07:40 jfs_stage1_5
-rw-r--r-- 1 root root   5802 2009-01-10 00:54 menu.lst
-rw-r--r-- 1 root root   5800 2009-01-10 00:46 menu.lst~
-rw-r--r-- 1 root root   7324 2008-07-12 07:40 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-07-12 07:40 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-07-12 07:40 stage1
-rw-r--r-- 1 root root 108356 2008-07-12 07:40 stage2
-rw-r--r-- 1 root root   9276 2008-07-12 07:40 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by ben44b on 2009-01-09
Nope. Changed primary to Hard Drive 0 with CD/ROM 2nd. Still cannot find operating system.

Says Press F1 to repeat boot sequence.

?

---

### Post by caljohnsmith on 2009-01-10
I'm really not sure why your BIOS would continue to give you the "no operating system" found if you have your Ubuntu drive set first in the boot order. Does your BIOS offer a "quick boot menu" on start up where you can temporarily choose which drive gets booted first? Some BIOSes use F10/F12 to get the quick boot menu, but I don't know what it might be for yours. If you have that option, how about trying it and then selecting the Ubuntu drive to boot, and see if you still get the same behavior. Also, is the boot flag still set on the Ubuntu drive? If you do:
```
sudo fdisk -lu
```
Does that show an asterisk * under the "boot" category for partition sda1?

---

### Post by ben44b on 2009-01-11
This is what that command gave me:

bernie@bernie-desktop:~$ sudo fdisk -lu
[sudo] password for bernie: 

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    75152069    37576003+  83  Linux
/dev/sda2        75152070    78156224     1502077+   5  Extended
/dev/sda5        75152133    78156224     1502046   82  Linux swap / Solaris
bernie@bernie-desktop:~$

---

### Post by ben44b on 2009-01-18
If I re-install another Linux distro, will it recognize my hard drive or is this irrelevant to what's going on?

Thanx

---

### Post by caljohnsmith on 2009-01-18
I think you could have a hardware issue at this point. How old is your 40 GB HDD? Can you open up your computer and reseat the HDD cable connector? I've seen where that can sometimes be the issue. Also, I think it wouldn't hurt get some idea of your HDD's health, so if that sounds OK with you, how about doing:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And please post the contents of the two files on your desktop so I can see the results.

---

### Post by ben44b on 2009-01-19
Thanks for replying.

Here's what it gave:

before
```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda ATA IV family
Device Model:     ST340016A
Serial Number:    3HS8G8RW
Firmware Version: 3.19
User Capacity:    40,016,019,456 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Jan 19 20:40:49 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 422) seconds.
Offline data collection
capabilities: 			 (0x1b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					No Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  31) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   072   062   043    Pre-fail  Always       -       182752731
  3 Spin_Up_Time            0x0003   070   070   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   094   094   020    Old_age   Always       -       6225
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   088   060   030    Pre-fail  Always       -       718035136
  9 Power_On_Hours          0x0032   057   057   000    Old_age   Always       -       37770
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       261
194 Temperature_Celsius     0x0022   029   055   000    Old_age   Always       -       29
195 Hardware_ECC_Recovered  0x001a   072   062   000    Old_age   Always       -       182752731
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Device does not support Selective Self Tests/Logging
```

and after
```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda ATA IV family
Device Model:     ST340016A
Serial Number:    3HS8G8RW
Firmware Version: 3.19
User Capacity:    40,016,019,456 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Jan 19 21:05:51 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 422) seconds.
Offline data collection
capabilities: 			 (0x1b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					No Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  31) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   076   062   043    Pre-fail  Always       -       19388288
  3 Spin_Up_Time            0x0003   070   070   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   094   094   020    Old_age   Always       -       6225
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   088   060   030    Pre-fail  Always       -       718163778
  9 Power_On_Hours          0x0032   057   057   000    Old_age   Always       -       37770
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       261
194 Temperature_Celsius     0x0022   043   055   000    Old_age   Always       -       43
195 Hardware_ECC_Recovered  0x001a   076   062   000    Old_age   Always       -       19388288
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     37770         -

Device does not support Selective Self Tests/Logging
```

?

---

### Post by ben44b on 2009-01-24
Any ideas...?

---

### Post by hatmancan on 2009-01-28
#i am having the same problem from the begining of this thread.
i followed the steps and am attaching my output to see if anyone can make some suggestions on this
thanks
hat



============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks /ubuntu/disks/boot/ 
                       /ubuntu/disks/boot/grub /ubuntu/disks/boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7ddd7dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78108029    39053983+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6E7802FF7802C635" TYPE="ntfs" 
/dev/loop0: UUID="5056e0da-dc39-498d-9f1b-6ab42b06888b" TYPE="ext3" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


================================ sda1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\wubildr.mbr="Kubuntu"

============================== sda1/ubuntu/disks: ==============================

total 14648448
drwxrwxrwx 1 root root           0 2009-01-25 20:56 .
drwxrwxrwx 1 root root        4096 2009-01-25 20:51 ..
drwxrwxrwx 1 root root        4096 2009-01-28 12:26 boot
-rwxrwxrwx 2 root root 14000000000 2009-01-28 16:11 root.disk
drwxrwxrwx 1 root root           0 2009-01-25 20:51 shared
-rwxrwxrwx 2 root root  1000000000 2009-01-25 21:04 swap.disk

=========================== sda1/ubuntu/disks/boot/: ===========================

total 36336
drwxrwxrwx 1 root root    4096 2009-01-28 12:26 .
drwxrwxrwx 1 root root       0 2009-01-25 20:56 ..
-rwxrwxrwx 1 root root  508385 2009-01-22 15:09 abi-2.6.27-11-generic
-rwxrwxrwx 1 root root  507665 2008-11-04 17:00 abi-2.6.27-7-generic
-rwxrwxrwx 1 root root  507665 2008-11-20 19:46 abi-2.6.27-9-generic
-rwxrwxrwx 1 root root   91358 2009-01-22 15:09 config-2.6.27-11-generic
-rwxrwxrwx 1 root root   91364 2008-11-04 17:00 config-2.6.27-7-generic
-rwxrwxrwx 1 root root   91364 2008-11-20 19:46 config-2.6.27-9-generic
drwxrwxrwx 1 root root       0 2009-01-28 12:23 grub
-rwxrwxrwx 1 root root 8471385 2009-01-28 12:26 initrd.img-2.6.27-11-generic
-rwxrwxrwx 1 root root 8467991 2009-01-25 23:07 initrd.img-2.6.27-7-generic
-rwxrwxrwx 1 root root 8468247 2009-01-25 23:14 initrd.img-2.6.27-9-generic
-rwxrwxrwx 1 root root  124152 2008-09-11 17:11 memtest86+.bin
-rwxrwxrwx 1 root root 1031799 2009-01-22 15:09 System.map-2.6.27-11-generic
-rwxrwxrwx 1 root root 1029585 2008-11-04 17:00 System.map-2.6.27-7-generic
-rwxrwxrwx 1 root root 1029585 2008-11-20 19:46 System.map-2.6.27-9-generic
-rwxrwxrwx 1 root root    1074 2009-01-22 15:11 vmcoreinfo-2.6.27-11-generic
-rwxrwxrwx 1 root root    1073 2008-11-04 17:02 vmcoreinfo-2.6.27-7-generic
-rwxrwxrwx 1 root root    1073 2008-11-20 19:48 vmcoreinfo-2.6.27-9-generic
-rwxrwxrwx 1 root root 2248912 2009-01-22 15:09 vmlinuz-2.6.27-11-generic
-rwxrwxrwx 1 root root 2244464 2008-11-04 17:00 vmlinuz-2.6.27-7-generic
-rwxrwxrwx 1 root root 2244304 2008-11-20 19:46 vmlinuz-2.6.27-9-generic

========================= sda1/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2009-01-28 12:23 .
drwxrwxrwx 1 root root 4096 2009-01-28 12:26 ..
-rwxrwxrwx 1 root root  191 2009-01-25 21:51 default
-rwxrwxrwx 1 root root   30 2009-01-25 21:50 device.map
-rwxrwxrwx 1 root root 5570 2009-01-28 12:23 menu.lst
-rwxrwxrwx 1 root root 5078 2009-01-28 12:23 menu.lst~

========================= sda1/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2009-01-28 12:23 .
drwxrwxrwx 1 root root 4096 2009-01-28 12:26 ..
-rwxrwxrwx 1 root root  191 2009-01-25 21:51 default
-rwxrwxrwx 1 root root   30 2009-01-25 21:50 device.map
-rwxrwxrwx 1 root root 5570 2009-01-28 12:23 menu.lst
-rwxrwxrwx 1 root root 5078 2009-01-28 12:23 menu.lst~

=============================== StdErr Messages: ===============================

No errors were reported.

---

### Post by MaindotC on 2009-02-11
I need help as well.  I installed 8.10 to a USB drive and no matter what I do it drops into initramfs prompt.  I have [this thread](http://ubuntuforums.org/showthread.php?p=6716543#post6716543) showing what I did.  Here is the RESULTS.TXT output:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8c228c22

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   149,838,254   149,838,192  83 Linux
/dev/sda2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sda5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 16.1 GB, 16173236224 bytes
255 heads, 63 sectors/track, 1966 cylinders, total 31588352 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04dd5721

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    30,170,069    30,170,007  83 Linux
/dev/sdb2          30,170,070    31,583,789     1,413,720   5 Extended
/dev/sdb5          30,170,133    31,583,789     1,413,657  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1ba32785-e91c-4d20-a7d6-4eb09379d8a4" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="5b4614d9-0d9a-4a53-8c7b-a609a7b6bbde" 
/dev/sdb1: UUID="16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="8eafc852-76c5-457b-9037-58a6ce37638d" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/a34lkj2348dsf311/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=a34lkj2348dsf311)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

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
# kopt=root=UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=splash vga=791 quiet

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 ro splash vga=791 quiet
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 ro splash vga=791 quiet
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 ro splash vga=791 quiet
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 ro splash vga=791 quiet
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 ro splash vga=791 quiet
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1ba32785-e91c-4d20-a7d6-4eb09379d8a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5b4614d9-0d9a-4a53-8c7b-a609a7b6bbde none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  36.5GB: boot/grub/menu.lst
  23.1GB: boot/grub/stage2
  23.1GB: boot/initrd.img-2.6.24-16-generic
  23.2GB: boot/initrd.img-2.6.24-16-generic.bak
  23.2GB: boot/initrd.img-2.6.24-19-generic
  23.1GB: boot/initrd.img-2.6.24-19-generic.bak
  23.1GB: boot/initrd.img-2.6.24-21-generic
  23.2GB: boot/initrd.img-2.6.24-21-generic.bak
  23.1GB: boot/initrd.img-2.6.24-22-generic
  23.1GB: boot/initrd.img-2.6.24-22-generic.bak
  25.2GB: boot/initrd.img-2.6.24-23-generic
  44.9GB: boot/initrd.img-2.6.24-23-generic.bak
  23.0GB: boot/vmlinuz-2.6.24-16-generic
  23.1GB: boot/vmlinuz-2.6.24-19-generic
  23.1GB: boot/vmlinuz-2.6.24-21-generic
  23.1GB: boot/vmlinuz-2.6.24-22-generic
  49.1GB: boot/vmlinuz-2.6.24-23-generic
  25.2GB: initrd.img
  23.1GB: initrd.img.old
  49.1GB: vmlinuz
  23.1GB: vmlinuz.old

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5

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
uuid		16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5 rootdelay=90 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8eafc852-76c5-457b-9037-58a6ce37638d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   1.0GB: boot/grub/menu.lst
   1.2GB: boot/grub/stage2
   1.2GB: boot/initrd.img-2.6.27-7-generic
   1.1GB: boot/vmlinuz-2.6.27-7-generic
   1.2GB: initrd.img
   1.1GB: vmlinuz

```

I'm trying to boot from /dev/sdb1.

---

### Post by aweiis on 2009-05-29
I'm having a similar issue to those above. Ran the boot info script and got similar results to everyone else. Specifics posted below.  The problem is that I'm unable to edit the menu.lst file, for some reason. When I mount sda1 and gksudo gkedit /mnt/boot/grub/menu.lst, a blank txt file named "menu.lst" pops up.  According to the results of the boot info script, I have a legit menu.lst file, but am unable to access it, for whatever reason.  Considered creating a new one and saving it out, but I dont wan't to screw things up any worse than I, apparently, already have. The blkid command doesn't return anything either, for the record. 

FYI, I lost the ability to boot after running.. 
```

sudo grub
find /boot/grub/stage1
root (hd0, 0)
setup(hd0)
quit
sudo reboot

```   
.. from a Live disk. Thought it may fix my XP partition, which gets stuck on "starting up..." while booting ever since i upgraded to jaunty and overwrote my menu.lst file (another issue entirely, but if you know of a fix off the top of your head..). Seemed like a good idea at the time.

Anywho, without further ado..
```

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/hda
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  Ubuntu 9.04
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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive hda: _____________________________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hda: 729 MB, 729608192 bytes
255 heads, 63 sectors/track, 22 cylinders, total 356254 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001b350

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   468,664,244   468,664,182  83 Linux
/dev/sda2         468,664,245   488,392,064    19,727,820   5 Extended
/dev/sda5         468,664,308   488,392,064    19,727,757  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26142613

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   245,762,369   245,762,307   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8408b1b7-f2ae-49dd-8d91-4b64ff2d4ff7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="1bc61c1c-90f9-4160-8946-edff583f32aa" 
/dev/sdb1: UUID="76C8007DC8003DBD" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

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
# kopt=root=UUID=8408b1b7-f2ae-49dd-8d91-4b64ff2d4ff7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8408b1b7-f2ae-49dd-8d91-4b64ff2d4ff7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8408b1b7-f2ae-49dd-8d91-4b64ff2d4ff7 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8408b1b7-f2ae-49dd-8d91-4b64ff2d4ff7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8408b1b7-f2ae-49dd-8d91-4b64ff2d4ff7 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8408b1b7-f2ae-49dd-8d91-4b64ff2d4ff7 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8408b1b7-f2ae-49dd-8d91-4b64ff2d4ff7 ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP Professional x64 Edition
root		(hd1,0)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8408b1b7-f2ae-49dd-8d91-4b64ff2d4ff7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1bc61c1c-90f9-4160-8946-edff583f32aa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   7.3GB: boot/grub/menu.lst
   7.4GB: boot/grub/stage2
   7.4GB: boot/initrd.img-2.6.24-19-generic
   7.4GB: boot/initrd.img-2.6.24-19-generic.bak
   7.4GB: boot/initrd.img-2.6.27-11-generic
   7.4GB: boot/initrd.img-2.6.28-11-generic
   7.4GB: boot/vmlinuz-2.6.24-19-generic
   7.4GB: boot/vmlinuz-2.6.27-11-generic
   7.4GB: boot/vmlinuz-2.6.28-11-generic
   7.4GB: initrd.img
   7.4GB: initrd.img.old
   7.4GB: vmlinuz
   7.4GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect


```

Any help is, of course, greatly appreciated.

---

### Post by unutbu on 2009-05-29
Boot the LiveCD.
Open a terminal (Applications>Accessories>Terminal), and type
```

sudo mount /dev/sda1 /mnt
gksu gedit **/mnt**/boot/grub/menu.lst

```
Add 
```

rootdelay=120
```

to the end of the kernel line. After editing, the kernel line should look something like this:
```

kernel		/vmlinuz-2.6.27-11-generic root=/dev/mapper/vg1-OS3 ro quiet **rootdelay=120**
```

Save and exit gedit. Reboot.

---

### Post by aweiis on 2009-05-29
Thanks for the reply.


mistyped the path in my original post. /mnt/boot/grub/menu.lst comes up blank.

---

### Post by unutbu on 2009-05-29
Try again. It has got to be there. When you run boot_info_script, it 
mounts sda1 and looks for the menu.lst in /mnt/boot/grub/menu.lst. Since we see the contents in the RESULTS.txt file, it has got to be possible to access it from the LiveCD.

Here is an alternate way to do the same thing:

Boot from the LiveCD.
Open a terminal. Type
```

sudo mount /dev/sda1 /mnt
gksu nautilus

```
This will launch a file browser with root privileges. Then use the GUI to navigate to 
/mnt/boot/grub/menu.lst.

---

### Post by aweiis on 2009-05-30
I was able to get sda1 (and sdb1, for the record) to mount correctly by telling the boot info script not to umount when it finished running. So whatever command the boot info script is using to mount the filesystems is working correctly but, sudo mount /dev/sda1 /mnt is not.  Which may be an issue in and of itself. 

Added rootdelay=120 to the end of the kernel line and rebooted, to no avail. Still getting the same result on start-up. sudo blkid /tmp/BootInfo1/sda1/ubuntu/disks/root.disk still doesn't return anything.

---

### Post by unutbu on 2009-05-30
aweiis, 

I think the reason 
```

sudo mount /dev/sda1 /mnt
```

did not work for you is because sda1 has a mismatch between its filesystem type and its boot sector type:

```

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat16
```

I believe the boot_info_script uses the command
```

sudo mount -t ext3 /dev/sda1 /mnt
```

By explicitly declaring the filesystem type, it avoids the error.

To test if my guess is correct, you could boot a LiveCD and type
```

sudo mount -t ext3 /dev/sda1 /mnt
```

and see if sda1 is successfully mounted at /mnt.

If the above test is successful, then to fix the problem run
```

sudo umount /dev/sda1
sudo dd if=/dev/zero of=/dev/sda1 bs=512 count=1
```

Be careful you type this command exactly right, or you could lose data. The above command writes zeros on the first 512 bytes of your sda1 partition. This is the so-called boot sector which boot_info_script is reporting to contain a Fat16 bootloader currently.

If that is successful, you should now be able to mount sda1 with the simpler command
```

sudo mount /dev/sda1 /mnt
```

And if that is successful, then try to reboot. Maybe the boot problem will be fixed by the above too.


---------------------------------------------------------------------------------


Now regarding the command
```

sudo blkid /tmp/BootInfo1/sda1/ubuntu/disks/root.disk
```

It looks sort of like what someone using Wubi might use, 
but I don't think you are Wubi. 

The correct command for you would be 
```

sudo blkid -c /dev/null
```

---

### Post by moodog on 2009-07-09
Any chance you may be able to give me some help?

I installed XP, then ubuntu and then windows 7. Win7 install killed grub. I've since been trying to get it up and running with no real luck.

My partitions are configured as follows:

```
	   	Device Boot      Start         End      Blocks   Id  System
winxp		/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
WIN7		/dev/sda2           11504       19152    61440592+   7  HPFS/NTFS
ubuntu root (/)	/dev/sda3            8287       11473    25599577+  83  Linux
extended	/dev/sda4           11474       11503      240975    5  Extended
ubuntu /boot	/dev/sda5           11474       11503      240943+  83  Linux


   Device Boot      Start         End      Blocks   Id  System
ubuntu swap	/dev/sdb1               1         892     7164958+  82  Linux swap / Solaris
win Docs&Set	/dev/sdb2             893        5991    40957717+   7  HPFS/NTFS
ubuntu /home	/dev/sdb3           16191       48060   255995775   83  Linux
```

The output of the script is as follows:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #1 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 184400850 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e82c9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,199,154    51,199,092   7 HPFS/NTFS
/dev/sda2         184,795,695   307,676,879   122,881,185   7 HPFS/NTFS
/dev/sda3         133,114,590   184,313,744    51,199,155  83 Linux
/dev/sda4         184,313,745   184,795,694       481,950   5 Extended
/dev/sda5         184,313,808   184,795,694       481,887  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000a91a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    14,329,979    14,329,917  82 Linux swap / Solaris
/dev/sdb2          14,329,980    96,245,414    81,915,435   7 HPFS/NTFS
/dev/sdb3         260,092,350   772,083,899   511,991,550  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9630D75630D73BC5" TYPE="ntfs" 
/dev/sda2: UUID="019519DF0C2C78A3" TYPE="ntfs" 
/dev/sda3: UUID="750863c1-7d34-44af-b6f1-81f9ea44f5a8" TYPE="ext4" 
/dev/sda5: UUID="f688976f-622b-40ba-8ea1-9cfdbab0113e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: TYPE="swap" UUID="464b4846-07e9-4f3b-8c35-ddde760b9fac" 
/dev/sdb2: UUID="148A8A0D191A27A3" TYPE="ntfs" 
/dev/sdb3: UUID="a2971e1d-a113-4dd7-a372-29e0d4a9fa29" TYPE="ext4" 

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

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=f688976f-622b-40ba-8ea1-9cfdbab0113e /boot           ext3    relatime        0       2
# /home was on /dev/sdb3 during installation
UUID=a2971e1d-a113-4dd7-a372-29e0d4a9fa29 /home           ext4    relatime        0       2
# swap was on /dev/sdb1 during installation
UUID=464b4846-07e9-4f3b-8c35-ddde760b9fac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

192.168.1.32:/mnt/store         /media/spankytv         nfs     defaults        0       0
192.168.1.32:/mnt/recordings            /media/recordings               nfs     defaults        0       0


============================= sda5/grub/menu.lst: =============================

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
# kopt=root=UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f688976f-622b-40ba-8ea1-9cfdbab0113e

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		f688976f-622b-40ba-8ea1-9cfdbab0113e
kernel		/vmlinuz-2.6.28-13-generic root=UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 ro quiet splash 
initrd		/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		f688976f-622b-40ba-8ea1-9cfdbab0113e
kernel		/vmlinuz-2.6.28-13-generic root=UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 ro  single
initrd		/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f688976f-622b-40ba-8ea1-9cfdbab0113e
kernel		/vmlinuz-2.6.28-11-generic root=UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f688976f-622b-40ba-8ea1-9cfdbab0113e
kernel		/vmlinuz-2.6.28-11-generic root=UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f688976f-622b-40ba-8ea1-9cfdbab0113e
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=================== sda5: Location of files loaded by Grub: ===================


  94.4GB: boot/grub/stage2
  94.5GB: grub/menu.lst
  94.5GB: grub/stage2
  94.3GB: initrd.img-2.6.28-11-generic
  94.4GB: initrd.img-2.6.28-13-generic
  94.3GB: vmlinuz-2.6.28-11-generic
  94.3GB: vmlinuz-2.6.28-13-generic

```

---

### Post by unutbu on 2009-07-09
moodog, what error message (if any) do you see when you boot up?
I see GRUB has been installed on the MBR of sda, sdb and sda5.
Is you BIOS set to boot sda?
Can you get to the GRUB menu?

---

### Post by ben44b on 2009-07-11
Sorry. Got a new hard drive. Fixed problem.

Thanx for your reply.

---

### Post by ubunticated on 2009-07-21
Good morning.
 
I'm having somewhat of a similar problem.
 
After attempting to upgrade to 9.04, I ran into some errors, which, upon reboot, landed me in a perpetual black screen with a small, moveable clock/watch cursor.
 
Using apt-get, I fixed broken packages and upgraded everything, but I'm now at the BusyBox prompt, preceded by messages telling me that it has given up waiting for the root device and that such and such does not exist.  (I'll be glad to elaborate with detail.)
 
I've gone through many of the proposed fixes (e.g., bootdelay), but haven't had any luck.  Perhaps I'm performing these fixes incorrectly.
 
When I boot up and hit Esc, then press "e" to edit the entry for Ubuntu 8.10, kernel 2.6.27-8-eeepc, I see the following:
 
uuid  f34253e9-7cb9-47059c81-57b1dfb7db90
kernel  /boot/vmlinux-2.6.27-8-eeepc root=UUID-f34253e9-7cb9-47059c81-57b1dfb7db90 ro single lash clocksource=hpet
init  /boot/initrd.img-2.6.27-8-eeepc
quiet
 
(I'm not sure if this is related to my issue, but I have gotten an unstable clocksource message.)
 
Is there anything blatantly wrong that I'm not noticing?  I would be most appreciate to any guidance or resources.
 
Thanks!

Edited to add menu.lst:

> 
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
# kopt=root=UUID=f34253e9-7cb9-4705-9c81-57b1dfb7db90 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f34253e9-7cb9-4705-9c81-57b1dfb7db90

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
# defoptions=quiet splash clocksource=hpet

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

splashimage=f34253e9-7cb9-4705-9c81-57b1dfb7db90/boot/grub/splash.xpm.gz

title		Ubuntu 8.10, kernel 2.6.27-8-eeepc
uuid		f34253e9-7cb9-4705-9c81-57b1dfb7db90
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=f34253e9-7cb9-4705-9c81-57b1dfb7db90 ro quiet splash clocksource=hpet 
initrd		/boot/initrd.img-2.6.27-8-eeepc
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-eeepc (recovery mode)
uuid		f34253e9-7cb9-4705-9c81-57b1dfb7db90
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=f34253e9-7cb9-4705-9c81-57b1dfb7db90 ro  single
initrd		/boot/initrd.img-2.6.27-8-eeepc

title		Ubuntu 8.10, memtest86+
uuid		f34253e9-7cb9-4705-9c81-57b1dfb7db90
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



---

### Post by ben44b on 2009-07-21
Greetings,

In the end I tried a new hard drive and my problems were (somewhat solved). I don't know for sure but I'm just guessing that it might be the hard drive was failing.

Good luck

---

### Post by ubunticated on 2009-07-21
> **ben44b said:**
> Greetings,

In the end I tried a new hard drive and my problems were (somewhat solved). I don't know for sure but I'm just guessing that it might be the hard drive was failing.

Good luck

I certainly hope that's not the case, but I appreciate the heads up!

Fortunately, I have my critical data backed up, which I do quite religiously.  Given that, I'm okay with reinstall.  However, there are some recent e-mails that I would like to salvage, if possible, and I can view them when I boot up from a USB stick using a live version of Kubuntu.  However, I can't seem to change the permissions to move them around.  When I figure this out, assuming it's possible, I don't see why I couldn't just upload the Thunderbird mail profiles I want to keep, along with a few other files and folders I'd like to hang on to.

Any hints on this?

In the meanwhile, I'll keep researching and reading the wealth of information here at the forums.

Thanks again!

---

### Post by unutbu on 2009-07-21
> 
landed me in a perpetual black screen with a small, moveable clock/watch cursor.

ubunticated, if you are seeing a graphical icon for the cursor, you are past the GRUB stage of booting. I'm not sure how to fix the problem however. It would probably be easier to backup those email files and then reinstall.

When you boot Kubuntu from the LiveUSB, you should be able to copy the emails by doing the following:

Open a terminal (Applications>Accessories>Terminal).
```
sudo rsync -a /path/to/email/directory/ /path/to/backup/directory/

```
Using "sudo" will get you over any permission problems.

Change /path/to/email/directory to the, um, path to the email directory.
Change /path/to/backup/directory to some media outside the partition containing /path/to/backup/directory (since reinstalling will wipe it out.)

The "sudo rsync" command above will copy the entire email directory over to the backup directory.

---

### Post by usmanajmal on 2010-08-02
I faced same problem with Debain. As Ubuntu is debian based so thought to post my problem here:

rootdelay=90 or 120 is not working for me. 
Gave up waiting for root device message is still being encountered.
(initramfs) prompt comes up after an alert i.e. /dev/sda1 does not exit.

Following is the output of boot_info_script
```


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2326528. But according to the info from 
                       fdisk, sda5 starts at sector 44271616.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2326528. But according to the info from 
                       fdisk, sda6 starts at sector 86216704.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2326528. But according to the info from 
                       fdisk, sda7 starts at sector 128161792.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x359debae

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     2,120,579     2,120,517  83 Linux
/dev/sda2    *      2,121,728     2,326,527       204,800   7 HPFS/NTFS
/dev/sda3           2,326,528    44,269,567    41,943,040   7 HPFS/NTFS
/dev/sda4          44,269,568   625,139,711   580,870,144   f W95 Ext d (LBA)
/dev/sda5          44,271,616    86,214,655    41,943,040   7 HPFS/NTFS
/dev/sda6          86,216,704   128,159,743    41,943,040   7 HPFS/NTFS
/dev/sda7         128,161,792   170,104,831    41,943,040   7 HPFS/NTFS
/dev/sda8         170,106,880   212,049,919    41,943,040   7 HPFS/NTFS
/dev/sda9         212,051,968   253,995,007    41,943,040   7 HPFS/NTFS
/dev/sda10        253,997,056   295,940,095    41,943,040   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0217934c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,827,455     7,827,393   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="b33a1310-9fcf-4507-bacf-8afc05f422a8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="AEBAB67ABAB63EA1" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda3: UUID="D88CC37C8CC353A2" TYPE="ntfs" 
/dev/sda5: UUID="D88CC37C8CC353A2" TYPE="ntfs" 
/dev/sda6: UUID="D88CC37C8CC353A2" TYPE="ntfs" 
/dev/sda7: UUID="D88CC37C8CC353A2" TYPE="ntfs" 
/dev/sda8: UUID="9A64B92564B90553" LABEL="New Volume" TYPE="ntfs" 
/dev/sda9: UUID="7014C34D14C314CE" LABEL="New Volume" TYPE="ntfs" 
/dev/sda10: UUID="40BECECEBECEBBA2" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: LABEL="USMANAJMAL" UUID="382A-8A7B" TYPE="vfat" 

=============================== "mount" output: ===============================

none on / type tmpfs (rw,relatime,size=2633768k)
/ramdisk/dev/sr0 on /cdrom type iso9660 (ro,relatime)
/dev/loop0 on /FINNIX type squashfs (ro,relatime)
none on /UNIONFS type unionfs (rw,relatime,dirs=/tmp/UNIONFS=rw:/cdrom/FINNIX/overlay.d/baltorosOverlay=ro:/FINNIX=ro)
none on /proc type proc (rw,relatime)
none on /sys type sysfs (rw,relatime)
tmpfs on /dev type tmpfs (rw,relatime,size=10240k,mode=755)
devpts on /dev/pts type devpts (rw,relatime,mode=600,ptmxmode=000)
devshm on /dev/shm type tmpfs (rw,relatime)
none on /proc/bus/usb type usbfs (rw)
/dev/sdb1 on /mnt type vfat (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

default saved
timeout 30

title Linux 
root  (hd0,0)
kernel /boot/vmlinuz root=/dev/sda1 vga=791 nosplash
initrd /boot/initrd.img-2.6.26-2-686
savedefault 1

title Windows 7
root (hd0,1)
chainloader +1
savedefault 0

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda2       /media/SystemReserved  ntfs-3g  force   0    0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.26-2-686
    .0GB: boot/initrd.img-2.6.26-2-686.bak
    .0GB: boot/vmlinuz
    .0GB: initrd.img



```

/dev/sdb is just my USB flashdrive from which I ran the script. /dev/sda1 contains linux/ which is not booting.

Any idea what's going wrong?

---

### Post by mistakos on 2011-01-26
I have the same problem. Cannot be sure how to solve it from the previous answers cause i am very new to Linux and have almost no idea what everything means.. yet at least!! I just got a fresh copy of Ubuntu and BusyBox shell waits for me to type 'exit' in order to boot. Here are the results from Results.txt:

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks at sector 8126698 
    on boot drive #-127 for core.img, but core.img can not be found at this 
    location.
 => Lilo is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   150,312,959   150,310,912  83 Linux
/dev/sda2         150,315,006   156,301,311     5,986,306   5 Extended
/dev/sda5         150,315,008   156,301,311     5,986,304  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   390,716,864   390,716,802   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8011 MB, 8011087872 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62    15,635,593    15,635,532   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0fa27788-37aa-4694-9561-50de3165b2fd" TYPE="ext4" 
/dev/sda5: UUID="e1408242-eeb8-4c14-a8e1-387c42516784" TYPE="swap" 
/dev/sdc1: UUID="AB80-5D2D" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0fa27788-37aa-4694-9561-50de3165b2fd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0fa27788-37aa-4694-9561-50de3165b2fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0fa27788-37aa-4694-9561-50de3165b2fd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0fa27788-37aa-4694-9561-50de3165b2fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0fa27788-37aa-4694-9561-50de3165b2fd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e1408242-eeb8-4c14-a8e1-387c42516784 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.35-22-generic
    .0GB: boot/initrd.img-2.6.35-24-generic
    .0GB: boot/vmlinuz-2.6.35-22-generic
    .0GB: boot/vmlinuz-2.6.35-24-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  30 00 c8 ff 14 f9 da 31  00 c7 70 00 c6 ff f9 00  |0......1..p.....|
00000010  d9 c6 ff f8 d9 c5 ff f8  2a d8 31 00 c4 f0 0b 66  |........*.1....f|
00000020  f2 0b c7 bb 1c b0 96 df  0a 1f 01 11 01 bb a5 97  |................|
00000030  d0 ff fc f1 ea 30 00 e9  70 0c 31 00 35 70 0c ef  |.....0..p.1.5p..|
00000040  71 0c e5 70 0c 30 0c ec  e2 a9 76 0c fb ea 73 0c  |q..p.0....v...s.|
00000050  fb 71 0c e7 70 0c 90 e6  da ff fa 70 0c fa e5 71  |.q..p......p...q|
00000060  0c 8e d5 70 0c 30 00 70  0c f9 e1 d2 30 0c 80 d0  |...p.0.p....0...|
00000070  ff fa df cf ff fa 72 0c  62 cd 70 0c cb ff f9 7f  |......r.b.p.....|
00000080  0c 32 0c f9 f1 34 0c f3  9c 68 f3 0b 30 31 df 0a  |.2...4...h..01..|
00000090  1f 01 01 11 01 bb a6 97  ff fd f2 ec 04 ff fc 30  |...............0|
000000a0  00 fd f1 eb ff fd c4 f0  e9 30 00 e8 ff fd f1 18  |.........0......|
000000b0  71 0c 62 ed 75 0c e3 ff  fb f0 18 37 0c dd d7 b0  |q.b.u......7....|
000000c0  18 f0 18 72 0c d9 70 0c  d8 30 00 75 0c c8 d4 ff  |...r..p..0.u....|
000000d0  f9 b0 18 f9 e1 b4 18 70  0c ec f9 de 31 0c bc 18  |.......p....1...|
000000e0  db b4 18 70 18 b1 18 c3  71 24 f1 2f c8 bc b2 93  |...p....q$./....|
000000f0  df 0a 1f 01 09 11 01 bc  a7 f0 0b f4 ef ff fd 74  |...............t|
00000100  f3 ed 30 00 ec b0 0c 30  0c f0 18 fd b6 f1 73 0c  |..0....0......s.|
00000110  71 25 fd f0 31 32 25 ed  f3 18 85 71 0c fc b6 18  |q%..12%....q....|
00000120  dd ff fa e7 71 0c bb b1  18 35 0c d6 b6 18 70 9e  |....q....5....p.|
00000130  b0 18 d1 b2 18 14 f9 df  34 25 dc bf 18 f9 da c6  |........4%......|
00000140  f0 ff f2 9e 6a f2 17 b1  49 df 0a 1f 01 01 11 01  |....j...I.......|
00000150  bb a7 98 ff fd f5 f0 04  ff fd 31 0c f4 ee ff df  |..........1.....|
00000160  bc 00 a1 ff de b8 9e ff  dc b5 00 9a ff da b3 96  |................|
00000170  ff d8 b0 00 93 ff d6 ad  90 ff d4 ab 00 8e ff d3  |................|
00000180  a9 8a ff d1 a7 00 88 ff  d0 a5 86 ff cf a3 00 84  |................|
00000190  ff ce a2 82 ff ce a1 9e  81 3f 00 3f 01 3f 02 30  |.........?.?.?.0|
000001a0  02 fa dd 7b 31 f8 f2 9e  6c f2 0b f1 55 df 0a 1f  |...{1...l...U...|
000001b0  01 11 01 10 bc a8 98 ff  30 ac ff fd f6 22 00 fe  |........0...."..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 58 5b 00 00 00  |...........X[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 f7 00 00 00 00 00  |........>.......|
00000020  4c 94 ee 00 88 3b 00 00  00 00 00 00 02 00 00 00  |L....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 2d 5d 80 ab 20  20 20 20 20 20 20 20 20  |..)-]..         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 08 63 30 00  66 ba 00 00 00 00 bb 00  |}.f..c0.f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```If anyone can help me with that i would appreciate it a lot!!

---

### Post by wilee-nilee on 2011-01-26
> **mistakos said:**
> I have the same problem. Cannot be sure how to solve it from the previous answers cause i am very new to Linux and have almost no idea what everything means.. yet at least!! I just got a fresh copy of Ubuntu and BusyBox shell waits for me to type 'exit' in order to boot. Here are the results from Results.txt:

```
============================= Boot Info Summary: ==============================

[B] => Grub1.97 is installed in the MBR of /dev/sda and looks at sector 8126698 
    on boot drive #-127 for core.img, but core.img can not be found at this 
    location.[/B]
 => Lilo is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   150,312,959   150,310,912  83 Linux
/dev/sda2         150,315,006   156,301,311     5,986,306   5 Extended
/dev/sda5         150,315,008   156,301,311     5,986,304  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   390,716,864   390,716,802   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8011 MB, 8011087872 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62    15,635,593    15,635,532   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0fa27788-37aa-4694-9561-50de3165b2fd" TYPE="ext4" 
/dev/sda5: UUID="e1408242-eeb8-4c14-a8e1-387c42516784" TYPE="swap" 
/dev/sdc1: UUID="AB80-5D2D" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0fa27788-37aa-4694-9561-50de3165b2fd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0fa27788-37aa-4694-9561-50de3165b2fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0fa27788-37aa-4694-9561-50de3165b2fd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0fa27788-37aa-4694-9561-50de3165b2fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0fa27788-37aa-4694-9561-50de3165b2fd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0fa27788-37aa-4694-9561-50de3165b2fd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e1408242-eeb8-4c14-a8e1-387c42516784 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.35-22-generic
    .0GB: boot/initrd.img-2.6.35-24-generic
    .0GB: boot/vmlinuz-2.6.35-22-generic
    .0GB: boot/vmlinuz-2.6.35-24-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  30 00 c8 ff 14 f9 da 31  00 c7 70 00 c6 ff f9 00  |0......1..p.....|
00000010  d9 c6 ff f8 d9 c5 ff f8  2a d8 31 00 c4 f0 0b 66  |........*.1....f|
00000020  f2 0b c7 bb 1c b0 96 df  0a 1f 01 11 01 bb a5 97  |................|
00000030  d0 ff fc f1 ea 30 00 e9  70 0c 31 00 35 70 0c ef  |.....0..p.1.5p..|
00000040  71 0c e5 70 0c 30 0c ec  e2 a9 76 0c fb ea 73 0c  |q..p.0....v...s.|
00000050  fb 71 0c e7 70 0c 90 e6  da ff fa 70 0c fa e5 71  |.q..p......p...q|
00000060  0c 8e d5 70 0c 30 00 70  0c f9 e1 d2 30 0c 80 d0  |...p.0.p....0...|
00000070  ff fa df cf ff fa 72 0c  62 cd 70 0c cb ff f9 7f  |......r.b.p.....|
00000080  0c 32 0c f9 f1 34 0c f3  9c 68 f3 0b 30 31 df 0a  |.2...4...h..01..|
00000090  1f 01 01 11 01 bb a6 97  ff fd f2 ec 04 ff fc 30  |...............0|
000000a0  00 fd f1 eb ff fd c4 f0  e9 30 00 e8 ff fd f1 18  |.........0......|
000000b0  71 0c 62 ed 75 0c e3 ff  fb f0 18 37 0c dd d7 b0  |q.b.u......7....|
000000c0  18 f0 18 72 0c d9 70 0c  d8 30 00 75 0c c8 d4 ff  |...r..p..0.u....|
000000d0  f9 b0 18 f9 e1 b4 18 70  0c ec f9 de 31 0c bc 18  |.......p....1...|
000000e0  db b4 18 70 18 b1 18 c3  71 24 f1 2f c8 bc b2 93  |...p....q$./....|
000000f0  df 0a 1f 01 09 11 01 bc  a7 f0 0b f4 ef ff fd 74  |...............t|
00000100  f3 ed 30 00 ec b0 0c 30  0c f0 18 fd b6 f1 73 0c  |..0....0......s.|
00000110  71 25 fd f0 31 32 25 ed  f3 18 85 71 0c fc b6 18  |q%..12%....q....|
00000120  dd ff fa e7 71 0c bb b1  18 35 0c d6 b6 18 70 9e  |....q....5....p.|
00000130  b0 18 d1 b2 18 14 f9 df  34 25 dc bf 18 f9 da c6  |........4%......|
00000140  f0 ff f2 9e 6a f2 17 b1  49 df 0a 1f 01 01 11 01  |....j...I.......|
00000150  bb a7 98 ff fd f5 f0 04  ff fd 31 0c f4 ee ff df  |..........1.....|
00000160  bc 00 a1 ff de b8 9e ff  dc b5 00 9a ff da b3 96  |................|
00000170  ff d8 b0 00 93 ff d6 ad  90 ff d4 ab 00 8e ff d3  |................|
00000180  a9 8a ff d1 a7 00 88 ff  d0 a5 86 ff cf a3 00 84  |................|
00000190  ff ce a2 82 ff ce a1 9e  81 3f 00 3f 01 3f 02 30  |.........?.?.?.0|
000001a0  02 fa dd 7b 31 f8 f2 9e  6c f2 0b f1 55 df 0a 1f  |...{1...l...U...|
000001b0  01 11 01 10 bc a8 98 ff  30 ac ff fd f6 22 00 fe  |........0...."..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 58 5b 00 00 00  |...........X[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 f7 00 00 00 00 00  |........>.......|
00000020  4c 94 ee 00 88 3b 00 00  00 00 00 00 02 00 00 00  |L....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 2d 5d 80 ab 20  20 20 20 20 20 20 20 20  |..)-]..         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 08 63 30 00  66 ba 00 00 00 00 bb 00  |}.f..c0.f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```If anyone can help me with that i would appreciate it a lot!!

So the highlighted grub2 bootloader is looking at a non existent area.

Boot the thumb to a live session and run these two commands in the terminal.
```
sudo mount /dev/sda1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot to Ubuntu and run in the terminal.
```
sudo update-grub
```

Here is the link that shows these commands and others for reloading grub2.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Also make sure the sda HD is the first being read in the bios, I think you have been getting in via the lilo bootloader in sdb possibly, we want grub2 to do this.

---

### Post by mistakos on 2011-01-26
ok.. i boot to live cd, i wrote the 2 commands in the terminal and then i returned to my installed ubuntu and made the update. After a restart, still the same.. :(

---

### Post by mistakos on 2011-01-26
ok.. hahahaha!! i thought i'd test something but it backfired!! hahahaha!!! 

I booted in my copy of Ubuntu and i tried the above first two commands.. and now when i restart my PC, i get the message:

```
error: file not found.
grub rescue> _
```

and now.. it doesn't boot at all. i don't even know what command to write over there.. 

hahahahahah.. my PC will autodestruct in 5 secs.. ahahahhaha

---

### Post by wilee-nilee on 2011-01-26
> **mistakos said:**
> ok.. i boot to live cd, i wrote the 2 commands in the terminal and then i returned to my installed ubuntu and made the update. After a restart, still the same.. :(

Is the sda HD first to be read in the bios?

Also lets go back to your original thread to do this stuff, it may seem like this thread is similar, but its not, and full of other unrelated stuff.

---

### Post by mistakos on 2011-01-26
> **wilee-nilee said:**
> Is the sda HD first to be read in the bios?

Also lets go back to your original thread to do this stuff, it may seem like this thread is similar, but its not, and full of other unrelated stuff.


yes it is.. 

but now i cannot boot at all!! hahahah! sorry for laughing, but i feel so stupid!! hahahah



EDIT

ok.. the rest in the other thread :)

---

