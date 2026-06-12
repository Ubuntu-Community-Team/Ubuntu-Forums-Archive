---
title: "Grub problem with 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Ken-san on 2009-10-30
Hi everyone, been trying to upgrade from scratch but with no success at the moment.

Here's what I did:

Booted one last time from 9.04.
Noted the partitions and mount points for my drives.
Rebooted into the 9.10 LiveCD.
Rearranged the partitions (I had a 15 GB unused one for XP).
Assigned mount points similar to the ones on 9.04, minus the XP partition in the installer, and changed all of them to ext4 (except for the /home partition).
Installed.
Rebooted.

Upon reboot, GRUB greeted me with an Error 15 after stage1.5 (which I found weird since I thought I was using GRUB2, which doesn't use stage1.5), 
So I rebooted back into the LiveCD, and tried this approach, with the following results (sdb5 is my / partition):
```

ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt
bash: groups: command not found
root@ubuntu:/# grub
bash: grub: command not found
root@ubuntu:/# update-grub
bash: update-grub: command not found

```

I'm currently stuck here; I don't get why it won't run any commands. I also ran a script found here:
[http://ubuntuforums.org/showthread.php?t=1022594](http://ubuntuforums.org/showthread.php?t=1022594)
and it reported this (also confirmed that I'm using the old version of GRUB):
```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x6df26de3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS

/dev/sda1 ends after the last cylinder of /dev/sda

Drive sdb: _____________________________________________________________________

Disco /dev/sdb: 250.1 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros, 488397168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x0001a771

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    52,436,159    52,436,097   7 HPFS/NTFS
/dev/sdb3          52,436,160   157,308,479   104,872,320   5 Extended
/dev/sdb5          52,436,223    62,926,604    10,490,382  83 Linux
/dev/sdb6          62,926,668    77,610,014    14,683,347  83 Linux
/dev/sdb7          77,610,078    84,951,719     7,341,642  83 Linux
/dev/sdb8          84,951,783    93,337,649     8,385,867  82 Linux swap / Solaris
/dev/sdb9          93,337,713   104,872,319    11,534,607  83 Linux
/dev/sdb10        104,872,383   157,308,479    52,436,097  83 Linux
/dev/sdb4         157,308,480   488,392,064   331,083,585   7 HPFS/NTFS

/dev/sdb1 ends after the last cylinder of /dev/sdb
/dev/sdb3 ends after the last cylinder of /dev/sdb
/dev/sdb5 ends after the last cylinder of /dev/sdb
/dev/sdb6 ends after the last cylinder of /dev/sdb
/dev/sdb7 ends after the last cylinder of /dev/sdb
/dev/sdb8 ends after the last cylinder of /dev/sdb
/dev/sdb9 ends after the last cylinder of /dev/sdb
/dev/sdb10 ends after the last cylinder of /dev/sdb
/dev/sdb4 ends after the last cylinder of /dev/sdb

Drive sdc: _____________________________________________________________________

Disco /dev/sdc: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros, 160836480 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x97b7f1d6

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   160,833,598   160,833,536   7 HPFS/NTFS

/dev/sdc1 ends after the last cylinder of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3A70C43C70C3FC9F" LABEL="Windows7_old" TYPE="ntfs" 
/dev/sdc1: UUID="2AA4DE1CA4DDEA79" LABEL="Storage" TYPE="ntfs" 
/dev/sdb1: UUID="1951147D1F44EF47" LABEL="Windows7" TYPE="ntfs" 
/dev/sdb4: UUID="32026AE5578131DE" LABEL="Programs" TYPE="ntfs" 
/dev/sdb5: UUID="2061f90a-e0b5-4f37-bca6-eb7b9b33b02a" TYPE="ext4" 
/dev/sdb6: UUID="5520071d-eff1-4333-b482-24c73fd1b584" TYPE="ext4" 
/dev/sdb7: UUID="f6453819-cf84-424d-9ce6-d2e3e51350a5" TYPE="ext4" 
/dev/sdb8: UUID="56a80c51-8545-423d-b782-cef1255038c4" TYPE="swap" 
/dev/sdb9: UUID="38912dc3-b194-47b8-9c6e-3c7d40ad37f4" TYPE="ext4" 
/dev/sdb10: UUID="7207a44e-6001-42d7-b3af-3578fa5c86da" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/Windows7_old type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb5 on /media/root type ext4 (rw)
/proc on /media/root/proc type none (rw,bind)
/sys on /media/root/sys type none (rw,bind)
/dev on /media/root/dev type none (rw,bind)
/dev/pts on /media/root/dev/pts type none (rw,bind)
/dev/sdb5 on /mnt type ext4 (rw)
/dev on /mnt/dev type none (rw,bind)
/proc on /mnt/proc type none (rw,bind)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.c....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 00 80 01 00 00 00  |N..F.s*.F.......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  e3 6d f2 6d 00 00 80 01  |...<.u...m.m....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.txt: línea 1135: cd: /media/root type ext4 (rw)
/dev/sdb5 on /mnt: No existe el fichero ó directorio
```

Any ideas, please?

---

### Post by wkulecz on 2009-10-30
No help, I've got the same problem with an AMD64 Destop install.

Grub didn't cause enough problems, so now we need Grub2 which is so different it shouldn't be called Grub at all!

No menu.lst file at all in /boot/grub.

--wally.

Edit:  Found a work-around.

My problem is/was grub2 got written to my SATA drive, not the hda that the BIOS was set to boot and 9.10 was installed to!  Changing the BIOS boot order got me the grub menu.

No indication that it was Grub2 instead of  Grub initially.  BUt it least I've booted 9.10 now.

My hda is a removable carrier that I use to swap in various boot devices, obviously this breaks that.
How do I install grub2 to my hda?

---

### Post by Sealbhach on 2009-10-31
Somebody else here with the same problem:

[http://ubuntuforums.org/showthread.php?p=8205673#post8205673](http://ubuntuforums.org/showthread.php?p=8205673#post8205673)

.

---

### Post by ssican on 2009-10-31
Grub 2 Basics :

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Ken-san on 2009-11-01
> **wkulecz said:**
> Edit:  Found a work-around.

My problem is/was grub2 got written to my SATA drive, not the hda that the BIOS was set to boot and 9.10 was installed to!  Changing the BIOS boot order got me the grub menu.

No indication that it was Grub2 instead of  Grub initially.  BUt it least I've booted 9.10 now.

I tried this as well and it worked (writing this from 9.10). GRUB2 installed to sda, and all my OS reside in sdb, so it seemed strange to me that it couldn't boot. Still, GRUB is installed in sdb and sdc; I need to change this eventually because sda is a storage hard disk (as in, storage for all the stuff I don't normally use). Will try the steps for reinstalling GRUB2 later. Thanks for all the advice.

---

