---
title: "Very New"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by ls1z28 on 2009-01-05
Hi all, 
Very new to Ubuntu.  I downloaded 8.10 64 to DVD.  I am trying to do a dual boot with XP.  I have a devoted HD for Ubuntu.  I finally decided to do the install through windows.  When I rebooted, I got the choice to boot XP or Ubuntu.  When I chose Ubuntu, I got to GRUB with only a GRUB command prompt.  

I am not sure the problem here....any ideas?

I'm sure its a very easy fix, I just don't know where to start.  

Thanks in advance.

---

### Post by caljohnsmith on 2009-01-06
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by ls1z28 on 2009-01-06
OK heres what i got

ubuntu@ubuntu:~$ cd ~/desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
bash: cd: /home/ubuntu/desktop: No such file or directory
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2009-01-06
> **ls1z28 said:**
> OK heres what i got

ubuntu@ubuntu:~$ cd ~/desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
bash: cd: /home/ubuntu/desktop: No such file or directory
ubuntu@ubuntu:~$
Linux is case-sensitive, so the above "cd" command should actually be:
```
cd ~/[COLOR="red"]D[/COLOR]esktop
```
Please try again and let me know how it goes.

---

### Post by ls1z28 on 2009-01-06
OK heres what u need

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /NTBOOTDD.SYS 
                       /wubildr.mbr

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr.mbr /ubuntu/winboot/wubildr.mbr /ubuntu/disks 
                       /ubuntu/disks/boot/ /ubuntu/disks/boot/grub 
                       /ubuntu/disks/boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      128519       64228+  de  Dell Utility
/dev/sda2   *      128520   302552144   151211812+   7  HPFS/NTFS
/dev/sda3       302552145   312496379     4972117+  db  CP/M / CTOS / ...

sfdisk -V /dev/sda:

partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b53b12a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   245762369   122881153+   7  HPFS/NTFS
/dev/sdb2       245762370   488392064   121314847+   7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0B10" TYPE="vfat" 
/dev/sda2: UUID="A4F45743F45716C0" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sdb1: UUID="16288676288654A1" LABEL="Vista" TYPE="ntfs" 
/dev/sdb2: UUID="7EE493B1E4936A63" LABEL="Linux" TYPE="ntfs" 
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
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer

c:\wubildr.mbr="Ubuntu"


============================== sdb2/ubuntu/disks: ==============================

total 29296884
drwxrwxrwx 1 root root           0 2009-01-06 04:08 .
drwxrwxrwx 1 root root        4096 2009-01-06 04:04 ..
drwxrwxrwx 1 root root           0 2009-01-06 04:04 boot
-rwxrwxrwx 2 root root 29000000000 2009-01-06 04:08 root.disk
drwxrwxrwx 1 root root           0 2009-01-06 04:04 shared
-rwxrwxrwx 2 root root  1000000000 2009-01-06 04:08 swap.disk

=========================== sdb2/ubuntu/disks/boot/: ===========================

total 0
drwxrwxrwx 1 root root 0 2009-01-06 04:04 .
drwxrwxrwx 1 root root 0 2009-01-06 04:08 ..
drwxrwxrwx 1 root root 0 2009-01-06 04:04 grub

========================= sdb2/ubuntu/disks/boot/grub: =========================

total 0
drwxrwxrwx 1 root root 0 2009-01-06 04:04 .
drwxrwxrwx 1 root root 0 2009-01-06 04:04 ..

========================= sdb2/ubuntu/disks/boot/grub: =========================

total 0
drwxrwxrwx 1 root root 0 2009-01-06 04:04 .
drwxrwxrwx 1 root root 0 2009-01-06 04:04 ..

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  2a b1 53 0b 00 00 00 01  |........*.S.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 03 09 a6 0e 00 fe  |......?.........|
000001d0  ff ff 07 fe ff ff 42 09  a6 0e 3f 3c 76 0e 00 00  |......B...?<v...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on /dev/sda3

00000000  eb 7c 90 44 65 6c 6c 20  38 2e 30 00 02 08 20 00  |.|.Dell 8.0... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 51 94 08 12  |........?...Q...|
00000020  ab bc 97 00 e3 25 00 00  00 00 00 00 02 00 00 00  |.....%..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 00 00 00 00 44  65 6c 6c 52 65 73 74 6f  |..)....DellResto|
00000050  72 65 46 41 54 33 32 20  20 20 10 00 01 00 00 00  |reFAT32   ......|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 33 c0  |..............3.|
00000080  8e d0 bc 00 07 fc b9 80  00 8e d8 be 00 7c b8 00  |.............|..|
00000090  20 8e c0 33 ff f3 66 a5  ea 9d 00 00 20 0e 1f 66  | ..3..f..... ..f|
000000a0  a1 1c 00 66 40 66 a3 62  00 c7 06 5e 00 00 02 c7  |...f@f.b...^....|
000000b0  06 60 00 00 20 c6 06 5c  00 02 e8 ad 00 0f b6 06  |.`.. ..\........|
000000c0  0d 00 c1 e0 09 a3 6a 00  66 0f b7 06 0e 00 66 03  |......j.f.....f.|
000000d0  06 1c 00 66 a3 6c 00 66  a1 24 00 66 d1 e0 66 03  |...f.l.f.$.f..f.|
000000e0  06 6c 00 66 a3 70 00 66  a1 2c 00 66 a3 74 00 b8  |.l.f.p.f.,.f.t..|
000000f0  00 30 8e c0 c7 06 5e 00  00 00 a3 60 00 e8 5f 01  |.0....^....`.._.|
00000100  33 db be 8f 01 8b fb b9  0b 00 f3 a6 74 1f 83 c3  |3...........t...|
00000110  20 3b 1e 6a 00 72 eb e8  ea 00 66 81 3e 74 00 ff  | ;.j.r....f.>t..|
00000120  ff ff 0f 75 ca be a5 01  e8 56 00 eb fe 26 8b 47  |...u.....V...&.G|
00000130  1a a3 74 00 26 8b 47 14  a3 76 00 a1 7c 00 a3 5e  |..t.&.G..v..|..^|
00000140  00 c7 06 60 00 70 00 e8  15 01 a1 6a 00 01 06 7c  |...`.p.....j...||
00000150  00 e8 b0 00 66 81 3e 74  00 ff ff ff 0f 75 dc 8a  |....f.>t.....u..|
00000160  16 40 00 33 ed ea 00 00  70 00 b4 42 8a 16 40 00  |.@.3....p..B..@.|
00000170  be 5a 00 cd 13 72 05 0a  e4 75 01 c3 be 9a 01 eb  |.Z...r...u......|
00000180  a7 b4 0e ac bb 07 00 cd  10 80 3c 00 75 f3 c3 44  |..........<.u..D|
00000190  45 4c 4c 42 49 4f 20 42  49 4e 44 69 73 6b 20 65  |ELLBIO BINDisk e|
000001a0  72 72 6f 72 00 4e 6f 20  6c 6f 61 64 65 72 00 00  |rror.No loader..|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-06
OK, so it is clear that you installed Ubuntu inside Windows via a Wubi install; unfortunately though, it does not look like your Ubuntu has a menu.lst, so that's why you get the Grub prompt when you try and boot Ubuntu. Since you want to give Ubuntu it's own drive anyway, have you considered just installing Ubuntu directly to the 250 GB drive by setting up partitions for it and using the Ubuntu installer? I think that would be a lot more ideal in your situation since you can give Ubuntu it's own drive. If you want to try that, here is a tutorial that might help you:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

If you decide to do that, I would recommend clicking the "advanced" button near the end of the installation and choose to have Grub installed to /dev/sdb, or the 250 GB drive you will be installing Ubuntu to. That way your Windows drive and Ubuntu drive will be independent of each other as far as booting goes. You would have to just once go into your BIOS and set the Ubuntu drive to boot first, and then I can help you set up your Grub menu to boot Windows in addition to Ubuntu. If that sounds like what you want, let me know after you are done installing, and please post the output of that script again. Otherwise let me know how it goes or if you run into problems. :)

---

### Post by ls1z28 on 2009-01-06
Well I initially tried the way you just suggested.  After it was installed there, I would restart and get GRUB error 21.  I had to repair my MBR so I could at least get windows to boot and then I reformatted the 2nd drive and started over and tried the wubi install.    

I will try the non wubi install again.

---

### Post by ls1z28 on 2009-01-06
OK, I loaded the op sys and Grub to /dev/sdb.  When computer starts it defaults to windows, with no choice to boot anything else.  I went into set up and set the HDD boot order to the only other choice I had which were other bootable devices.  I restarted and again it defaulted to windows with no choice of operating system.

---

### Post by caljohnsmith on 2009-01-06
> **ls1z28 said:**
> OK, I loaded the op sys and Grub to /dev/sdb.  When computer starts it defaults to windows, with no choice to boot anything else.  I went into set up and set the HDD boot order to the only other choice I had which were other bootable devices.  I restarted and again it defaulted to windows with no choice of operating system.
If you have no way of booting the Ubuntu sdb drive, you could install Grub to the MBR of your Windows drive. The disadvantage of doing that is your drives will be dependent on each other for booting, but many people do it that way without a problem usually. So that means you would always have to have both drives connected in order too boot. If that sounds OK, how about doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit
```
Please post the output of all the above commands before doing "quit". Then reboot, and let me know how it goes.

---

### Post by ls1z28 on 2009-01-06
Well before I do that, I looked a bit closer and noticed that my system for one reason or another in the set up screen, does not recognize the 2nd drive.  I know I have the most current bios.  Before I installed Ubuntu, I was using that 2nd drive as a storage drive with no problems at all. I had it partitioned in NFTS and all was good.  Any ideas as to why my computer in the set up screen does not see this 2nd drive??

Also the way you just suggested, where do I go for that command prompt to access GRUB?

---

### Post by caljohnsmith on 2009-01-06
> **ls1z28 said:**
> Well before I do that, I looked a bit closer and noticed that my system for one reason or another in the set up screen, does not recognize the 2nd drive.  I know I have the most current bios.  Before I installed Ubuntu, I was using that 2nd drive as a storage drive with no problems at all. I had it partitioned in NFTS and all was good.  Any ideas as to why my computer in the set up screen does not see this 2nd drive??

Also the way you just suggested, where do I go for that command prompt to access GRUB?
Is your external drive USB? If so, that might be the issue with your BIOS. That means installing Grub to the MBR of your Windows drive in order to boot your Ubuntu drive may not work, but I think it is worth a try. To run the Grub commands, you can do them in a terminal (Applications > Accessories > Terminal) like when you ran the script. Let me know how that goes.

---

### Post by ls1z28 on 2009-01-06
The 2nd drive is an internal SATA like the main drive.  Let me give this a try and see how it goes.

---

### Post by ls1z28 on 2009-01-06
OK here it is

```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd1,0)
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

```

---

### Post by ls1z28 on 2009-01-06
I configured GRUB and when I rebooted, I got GRUB error 21

---

### Post by caljohnsmith on 2009-01-06
> **ls1z28 said:**
> I configured GRUB and when I rebooted, I got GRUB error 21
That error actually makes sense since it means "Selected disk does not exist", which confirms that your BIOS does not seem to detect the Ubuntu drive on start up. That unfortunately doesn't leave you with a lot of options, but one thing you could do would be to resize your sda3 partition on the Windows drive to make room for a ~200 MB ext3 partition at the end; then you could make that your Ubuntu boot partition, so that you would actually be booting Ubuntu from your Windows drive while the main Ubuntu install would be on your 250 GB drive. I think there's a reasonable chance of it working, and I don't think it would take too much effort to find out. If you want to give it a shot, then shrink your sda3 partition at the end to free about 200 MB of space, and then create a new primary ext3 partition with that space. Then go through Ubuntu installer like you previously did, but when you get to the partitioning stage where you set mount points, set the mount point on the new partition as "/boot". Also you don't need to change the settings under the "advanced" button since you would want Grub installed to your Windows drive, which is what happens by default. Let me know how that goes if you decide to give it a try.

---

### Post by ls1z28 on 2009-01-06
Maybe you can answer this for me.  The 2nd drive doesnt show I THINK becasue its set as a storage drive.  The drive is a WD2500AAKS.  I went into data lifeguard and was going to re-do it as a bootable drive.  When I did this, the only option was to make it THE bootable drive, thus transfering my windows to this drive.  I really dont want to chance doing that and messing something up.  Do you have any idea on how to make the 2nd drive a bootable drive.  Its a SATA drive so from what I read, jumper settings dont mean anything.

---

### Post by caljohnsmith on 2009-01-06
> **ls1z28 said:**
> Maybe you can answer this for me.  The 2nd drive doesnt show I THINK becasue its set as a storage drive.  The drive is a WD2500AAKS.  I went into data lifeguard and was going to re-do it as a bootable drive.  When I did this, the only option was to make it THE bootable drive, thus transfering my windows to this drive.  I really dont want to chance doing that and messing something up.  Do you have any idea on how to make the 2nd drive a bootable drive.  Its a SATA drive so from what I read, jumper settings dont mean anything.
I don't understand what the data lifeguard tools mean exactly by making it a bootable drive, unless they simply mean setting the boot flag on one of the partitions. We didn't check that since you installed Ubuntu, so it could be that maybe none of the partitions have the boot flag set. So to see if that makes any difference, how about doing:
```
sudo sfdisk -A1 /dev/sdb
```
And let me know if that changes anything about booting the drive. Also, I would be hesitant to use the data lifeguard tools to transfer your Windows to that drive, because I'm not sure Windows would boot after being moved from an IDE drive to a SATA drive (maybe it would, I don't know).

---

### Post by ls1z28 on 2009-01-06
I ran data lifeguard (Western Digital's driver software), to make sure the driver was set right so the BIOS should be reading the drive.  Both of my drives are SATA and, LOL no I didn't switch the drives....Windows is staying right where it is.

---

### Post by ls1z28 on 2009-01-06
Well I am happy to report that I figured out that the drive was not turned on in the setup.  Once i turned it on, I got the chioce to boot what ever system.  

Now just need to figure out why I have no sound  LOL

THank you for you patience!!!!!

---

### Post by caljohnsmith on 2009-01-06
Glad you figured out the problem in your BIOS, and hope you can get your sound working too. Cheers and good luck. :)

---

