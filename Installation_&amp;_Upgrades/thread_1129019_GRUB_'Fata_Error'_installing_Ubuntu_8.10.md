---
title: "GRUB 'Fata Error' installing Ubuntu 8.10"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by Rmc22 on 2009-04-18
I've just attempted a manual install of 8.10, but seem to have failed to install the GRUB bootloader.

I've got Win XP on the original 'C' drive HDD, and the plan was to install Ubuntu in 100Gb of unallocated space on a second HDD which I added a while ago.

I selected manual partitioning, first created 20Gb for /root in ext3 format; then created 70Gb as /home (ext3 too); then created 4Gb of swap (swap format).

The installation proceeded fine until near the end, when I got some kind of 'Grub Fatal error' and I think reference to failing to install Grub.  There's no bootloader when I reboot, it just goes straight to windows as normal.

I'm guessing I should have created a /boot partition too?  My assumption was that the installation CD would still stick the bootloader on the C drive windows HDD in 'manual', but now that appears to have been wrong.  

Can anyone confirm my mistake and suggest the best solution?  There's obviously no personal data at all on the new installation yet, and there's still 16Gb of unpartitioned space on the second HDD if that may help.

---

### Post by Rmc22 on 2009-04-18
Any ideas?

Thought this might be a simple one to answer...

---

### Post by meierfra. on 2009-04-19
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Rmc22 on 2009-04-19
meierfra,

Thanks for the reply.  Just to be clear, the Boot Info Script has to be run from the machine under Ubuntu/Live CD, and not via the (working) Windows OS, does it?  I'm a bit confused.

---

### Post by Rmc22 on 2009-04-19
OK, got it to work via Live CD.  Hope this load helps....

```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdg
 => Windows is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2    *        128,520   481,596,569   481,468,050   7 HPFS/NTFS
/dev/sda3         481,596,570   488,263,544     6,666,975  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb5f2b551

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   614,405,924   614,405,862   7 HPFS/NTFS
/dev/sdb2         614,405,925 2,713,603,409 2,099,197,485   6 FAT16
/dev/sdb3       2,713,603,410 2,897,194,229   183,590,820   5 Extended
/dev/sdb5       2,713,603,473 2,752,673,489    39,070,017  83 Linux
/dev/sdb6       2,752,673,553 2,889,386,639   136,713,087  83 Linux
/dev/sdb7       2,889,386,703 2,897,194,229     7,807,527  82 Linux swap / Solaris


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 16.0 GB, 16039018496 bytes
75 heads, 40 sectors/track, 10442 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d12b891

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *             40    31,326,207    31,326,168   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0713" TYPE="vfat" 
/dev/sda2: UUID="7AC8E14FC8E10A69" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sdb1: UUID="CE24167D241668AB" LABEL="Data" TYPE="ntfs" 
/dev/sdb5: UUID="44f9cfa0-6403-4f00-8397-d6bf56eec62d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="db750e98-725e-4f43-8eaf-e9f449003d6d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: TYPE="swap" UUID="d372d8bf-1789-4d6f-bc57-4b56e128af1f" 
/dev/loop0: TYPE="squashfs" 
/dev/sdg1: UUID="B64C33A04C3359F7" LABEL="FreeAgent 750Gb" TYPE="ntfs" 
/dev/sdh1: LABEL="DATABAR16GB" UUID="3042-575A" TYPE="vfat" 

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
/dev/sdg1 on /media/FreeAgent 750Gb type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdh1 on /media/DATABAR16GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=44f9cfa0-6403-4f00-8397-d6bf56eec62d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=db750e98-725e-4f43-8eaf-e9f449003d6d /home           ext3    relatime        0       2
# /dev/sdb7
UUID=d372d8bf-1789-4d6f-bc57-4b56e128af1f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


1403.8GB: boot/grub/stage2
1403.8GB: boot/initrd.img-2.6.27-7-generic
1403.7GB: boot/vmlinuz-2.6.27-7-generic
1403.8GB: initrd.img
1403.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  9e ea 2b 66 d4 f4 e2 45  db 38 81 51 50 2e 6c db  |..+f...E.8.QP.l.|
00000010  91 eb d9 19 72 97 b4 f1  0f 6c 9c a4 52 e8 b4 27  |....r....l..R..'|
00000020  c0 b2 a2 b2 45 6b f9 cd  05 a9 d8 6b a4 81 d3 97  |....Ek.....k....|
00000030  a3 80 3f a6 82 00 94 be  8a 15 fd bf 63 32 b6 12  |..?.........c2..|
00000040  6e de 1e 34 09 89 14 78  15 33 e9 f5 49 d0 bf bb  |n..4...x.3..I...|
00000050  02 e8 b2 c4 b0 c1 35 27  ed 25 95 52 61 bc 11 ff  |......5'.%.Ra...|
00000060  fe 5d 0c 78 0b 72 3d 51  9f 76 40 e5 07 ec 1d 8c  |.].x.r=Q.v@.....|
00000070  c2 76 ff 4f dc dc d3 ec  2a cd ac 4b 05 8b bf c7  |.v.O....*..K....|
00000080  6b 31 86 e7 6f ec 12 89  d7 05 bd f0 c3 83 7a da  |k1..o.........z.|
00000090  b0 76 af c8 29 98 1e 5c  37 f8 54 f4 6d 72 ec cf  |.v..)..\7.T.mr..|
000000a0  cd 3f 06 c4 01 52 ab 85  60 00 4a 55 b4 8c 0a af  |.?...R..`.JU....|
000000b0  b5 ab 90 52 b3 58 e9 5d  e4 59 c2 85 0e 97 db da  |...R.X.].Y......|
000000c0  02 7f 34 5e be 2d 07 91  7f 04 c7 41 b4 80 ac eb  |..4^.-.....A....|
000000d0  97 d0 86 63 36 c6 62 f3  86 24 90 f3 84 13 bb e1  |...c6.b..$......|
000000e0  39 4a 83 64 06 a0 15 93  a5 75 4d e6 f3 c1 46 5d  |9J.d.....uM...F]|
000000f0  14 21 65 06 a8 79 67 c5  46 04 c6 f2 75 2a 58 00  |.!e..yg.F...u*X.|
00000100  39 9c e9 67 0b 0e 16 a4  b4 71 6e 33 ab da bf 19  |9..g.....qn3....|
00000110  ec fa 55 a6 76 27 c9 5b  49 b6 17 f3 6a e8 2f 4b  |..U.v'.[I...j./K|
00000120  92 12 27 25 7d d7 bc af  92 88 a9 cb a6 61 af 51  |..'%}........a.Q|
00000130  7b 59 d3 92 99 22 f1 fb  66 01 1d 01 63 e4 3e 57  |{Y..."..f...c.>W|
00000140  da c2 2f 62 de 0e 94 42  af 61 2f 8b 3c 78 ed b8  |../b...B.a/.<x..|
00000150  77 b0 20 0b fc db 3e df  28 14 84 60 80 31 74 7e  |w. ...>.(..`.1t~|
00000160  48 56 e1 90 a9 7b a8 c4  47 d8 1d e5 c0 35 fe 5b  |HV...{..G....5.[|
00000170  ec 7a b0 86 9c 6e a9 06  71 77 a0 79 f3 1d 10 08  |.z...n..qw.y....|
00000180  4c b9 8f 9a 41 a2 4b b8  fc ef cf 58 94 55 8f 10  |L...A.K....X.U..|
00000190  89 d0 e0 7e ae ec e7 ab  e3 d1 30 90 f9 e4 83 40  |...~......0....@|
000001a0  c4 00 25 f9 a3 c6 3d ae  b0 3a 86 ef 7e e7 00 f1  |..%...=..:..~...|
000001b0  71 9d ff 37 1a 0d 34 95  d5 f1 d0 4b eb e0 c8 09  |q..7..4....K....|
000001c0  5c 2a 44 fb 2a aa a4 8a  1e 8f 37 68 34 b5 7b d4  |\*D.*.....7h4.{.|
000001d0  65 9f f3 9a c0 25 8e d4  da 84 1d 04 d2 42 e4 de  |e....%.......B..|
000001e0  9e 92 c9 2f e8 be 06 60  41 c2 78 0f 8a 80 21 64  |.../...`A.x...!d|
000001f0  dc d8 e2 e9 77 5c eb f8  35 c1 0e 2a b6 06 cf 07  |....w\..5..*....|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by meierfra. on 2009-04-19
Try this:  Boot from the LiveCD, open a terminal

```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt --recheck /dev/sdb
sudo mount --bind {,/mnt}/dev 
sudo mount --bind {,/mnt}/proc
sudo mount --bind {,/mnt}/sys
sudo chroot /mnt

```
and at the new prompt

```
update-grub
```

Hopefully, this will  install Grub correctly.


There also  seems to a problem with  /dev/sdb2, the 1000GB partition in the Ubuntu drive.  What is on that partition?

---

### Post by Rmc22 on 2009-04-20
meierfra.,

I get the following error after the second command you gave, so have not proceeded any further:

> ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt --recheck /dev/sdb
Probing devices to guess BIOS drives. This may take a long time.
The file /mnt/boot/grub/stage1 not read correctly.
ubuntu@ubuntu:~$ 


Should I try the next steps, or not?  The 1000Gb partition is not a problem, just an unformatted partition set aside for future use.

Thanks,

Rmc22

---

### Post by meierfra. on 2009-04-20
Try this instead:

```
sudo mount /dev/sdb5 /mnt
```
(only do this if your rebooted since the last time you "mounted" /dev/sdb5)


```

sudo cp /etc/resolv.conf /mnt/etc
sudo mount --bind {,/mnt}/dev 
sudo mount --bind {,/mnt}/proc
sudo mount --bind {,/mnt}/sys
sudo chroot /mnt
```

and at the new prompt:

```
apt-get purge grub
apt-get install grub
```

[B]Open a new terminal:
[/B]

```
sudo grub-install --root-directory=/mnt --recheck /dev/sdb
```


**Back in the first terminal**

```
update-grub
```

---

### Post by Rmc22 on 2009-04-20
Thanks for the further instructions, but things are still going wrong near the end:

> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt --recheck /dev/sdb
Probing devices to guess BIOS drives. This may take a long time.
The file /mnt/boot/grub/stage1 not read correctly.
ubuntu@ubuntu:~$ update-grub
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###


Any more ideas?

---

### Post by apparle on 2009-04-20
It seems that the setup completed correctly but, just didn't install GRUB..
Try
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
this might solve the problem but I'm not much of an expert.

If nothing works reinstall the whole system again (I did that when I encountered the same problem)

---

### Post by meierfra. on 2009-04-20
Did you get any error messages during "apt-get install grub"?

Anyway, try this next

[http://pennsyvlania.ubuntuforums.org/showthread.php?t=944682#4](http://pennsyvlania.ubuntuforums.org/showthread.php?t=944682#4)

Let me know if you need more detailed instructions.

---

### Post by Rmc22 on 2009-04-20
Here's the entirety of the first screen, before I opened the second terminal:

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc
ubuntu@ubuntu:~$ sudo mount --bind {,/mnt}/dev 
ubuntu@ubuntu:~$ sudo mount --bind {,/mnt}/proc
ubuntu@ubuntu:~$ sudo mount --bind {,/mnt}/sys
ubuntu@ubuntu:~$ sudo chroot /mntapt-get purge grub
chroot: cannot change root directory to /mntapt-get: No such file or directory
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ sudo mount --bind {,/mnt}/sys
bash: ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ sudo mount --bind {,/mnt}/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get purge grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub* ubiquity* ubiquity-frontend-gtk*
0 upgraded, 0 newly installed, 3 to remove and 307 not upgraded.
After this operation, 11.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 102341 files and directories currently installed.)
Removing ubiquity ...
Purging configuration files for ubiquity ...
Removing ubiquity-frontend-gtk ...
Removing grub ...
Purging configuration files for grub ...
Processing triggers for man-db ...
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 307 not upgraded.
Need to get 402kB of archives.
After this operation, 938kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com intrepid/main grub 0.97-29ubuntu45 [402kB]
Fetched 402kB in 0s (448kB/s)
Preconfiguring packages ...
Selecting previously deselected package grub.
(Reading database ... 101786 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu45_i386.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu45) ...
 
```

I'll have a look at the link you posted next..

---

### Post by Rmc22 on 2009-04-20
Yes, it appears I have the '94%' bug.

I tried re-running the Live CD installation, deleted the previously made partitions for Ubuntu (20Gb Root, 70Gb Home, 4Gb Swap), then remade them just the same as they were, selected format as ext3 for first two (warning box said I shouldn't proceed without formatting them when I didn't first time) then continued with the installation.

At the 94% point, whilst the progress box says 'Installing System, Installing GRUB boot loader, Running "grub-install (hd0)" I then get the error:

'Unable to install GRUB in (hd0)
Executing 'grub-install (hd0) failed
This is a Fatal Error'

I'll now try to work out if the post re 94% error can give me a solution. But kind of disappointed that such a well developed package can get so far, just to fall over at the last hurdle...

---

### Post by apparle on 2009-04-21
I had that problem in 7.10 but never faced that problem again.........may be an installing from alternate CD may fix it but I'm not sure

---

### Post by 146590 on 2009-04-21
go "sudo grub"

then "update-grub"

---

### Post by Rmc22 on 2009-04-21
apparle - I verified the MD5 hash before burning the CD, then set Ubuntu on 'Check CD' option before installing, so I doubt the CD is a problem.

146590 - hasn't the "update-grub" command already been tried before in suggestions this post has received?

I think this may be a good old-fashioned, Windows-style, bug.  Shame it hasn't been fixed in the time since the earlier linked '94% bug' was first posted, October '08.

---

### Post by meierfra. on 2009-04-23
[QUOTE=Rmc22]I've got a similar problem, I've not found an answer either, let me know if you find one!![/QUOTE]
Did you ever try  out the method  from the link I posted?

If it does not work, please let me know. There are other things one can try.

---

### Post by apparle on 2009-04-26
> **Rmc22 said:**
> apparle - I verified the MD5 hash before burning the CD, then set Ubuntu on 'Check CD' option before installing, so I doubt the CD is a problem.

146590 - hasn't the "update-grub" command already been tried before in suggestions this post has received?

I think this may be a good old-fashioned, Windows-style, bug.  Shame it hasn't been fixed in the time since the earlier linked '94% bug' was first posted, October '08.

I am not at all saying that your CD is a problem.
Super GRUB Disk is a stand alone GRUB repairing disk which is only dedicated to bootloader reapir purpose. Try it.
When you put in the disk, it guides you all the way to repair your GRUB isntallation

---

