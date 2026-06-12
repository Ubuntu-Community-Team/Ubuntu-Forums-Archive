---
title: "After Ubuntu install, WinXP won't bon't from GRUB"
date: 2008-11-24
forum: General Help
---

### Post by tvdij on 2008-11-24
All,

I had Windows XP installed on my desktop then installed Ubuntu. Ubuntu works fine but when trying to boot to Windows XP I just get a black screen. (I click Windows XP from GRUB menu, and screen goes black)

Win XP is on the first partition on the first hard drive (I have 2 hd's both are SATA)

fdisk -lu returns the following

```

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07662532

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   266245244   133122591    7  HPFS/NTFS
/dev/sda2       266245245   312496379    23125567+   5  Extended
/dev/sda5       266245308   310488254    22121473+  83  Linux
/dev/sda6       310488318   312496379     1004031   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2de02ddf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   160071659    80035798+   7  HPFS/NTFS

```

Also, here is my "menu.lst" file.

```

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=64e9839a-3c69-443b-bd27-9e88202a272c ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=64e9839a-3c69-443b-bd27-9e88202a272c ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=64e9839a-3c69-443b-bd27-9e88202a272c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=64e9839a-3c69-443b-bd27-9e88202a272c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1
boot

```

I can only boot to XP when using the Super Grub Disk CD rom boot disk. However, I don't want to use a CD rom to boot between the 2 OSes on a permanent basis. 

Any suggestions?

Thanks.

---

### Post by caljohnsmith on 2008-11-24
How about posting the output of the following in order to clarify your setup:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And also please post:
```
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda1 /mnt/sdb1
```
Where "-l" is a lowercase L, not a one. We can work from there if you want. :)

---

### Post by tvdij on 2008-11-24
Here is the system response to the first batch of code.

```

adrian@adrian-desktop:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
adrian@adrian-desktop:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff04

adrian@adrian-desktop:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
adrian@adrian-desktop:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
0000

```

And the system response to the second batch of terminal entries
```

adrian@adrian-desktop:~$ sudo mkdir /mnt/sda1 /mnt/sdb1
adrian@adrian-desktop:~$ sudo mount /dev/sda1 /mnt/sda1
adrian@adrian-desktop:~$ sudo mount /dev/sdb1 /mnt/sdb1
adrian@adrian-desktop:~$ ls -l /mnt/sda1 /mnt/sdb1
/mnt/sda1:
total 3667885
drwxrwxrwx 1 root root          0 2008-11-16 10:06 ATI
drwxrwxrwx 1 root root       4096 2008-11-22 13:00 $AVG8.VAULT$
-rwxrwxrwx 1 root root        210 2008-11-16 03:03 boot.ini
drwxrwxrwx 1 root root       4096 2008-11-16 09:25 Documents and Settings
-rwxrwxrwx 1 root root 1610141696 2008-11-24 12:20 hiberfil.sys
drwxrwxrwx 1 root root          0 2008-11-16 11:39 MSOCache
-rwxrwxrwx 1 root root      47564 2006-02-28 05:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-11-22 16:02 ntldr
-rwxrwxrwx 1 root root 2145386496 2008-11-24 12:20 pagefile.sys
drwxrwxrwx 1 root root      12288 2008-11-23 16:16 Program Files
drwxrwxrwx 1 root root          0 2008-11-16 09:28 RECYCLER
drwxrwxrwx 1 root root       4096 2008-11-16 09:24 System Volume Information
drwxrwxrwx 1 root root      57344 2008-11-24 03:17 WINDOWS

/mnt/sdb1:
total 48
-rwxrwxrwx 1 root root     0 2008-11-16 09:20 AUTOEXEC.BAT
-rwxrwxrwx 1 root root     0 2008-11-16 09:20 CONFIG.SYS
drwxrwxrwx 1 root root     0 2008-11-15 15:18 Documents
drwxrwxrwx 1 root root  4096 2008-11-24 00:09 Games
-rwxrwxrwx 1 root root     0 2008-11-16 09:20 IO.SYS
-rwxrwxrwx 1 root root     0 2008-11-16 09:20 MSDOS.SYS
drwxrwxrwx 1 root root  4096 2007-09-14 12:45 My Pictures
drwxrwxrwx 1 root root 24576 2008-11-16 11:11 My Videos
drwxrwxrwx 1 root root  4096 2008-11-16 06:50 $RECYCLE.BIN
drwxrwxrwx 1 root root     0 2008-11-16 10:05 RECYCLER
drwxrwxrwx 1 root root  4096 2008-11-18 00:32 Software
drwxrwxrwx 1 root root  4096 2008-11-16 09:25 System Volume Information
drwxrwxrwx 1 root root  4096 2008-11-24 00:09 TV

```

Thanks

---

### Post by caljohnsmith on 2008-11-24
OK, so Windows is indeed in sda1, and since you are booting the sda drive on start up, your Grub entry for Windows is OK. It might be that your Windows partition boot sector is slightly corrupt, so to check if that is the problem, how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical" like the screen shown below, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens when you try and boot XP again. Or let me know if testdisk claims the sectors are identical. :)

[IMG]http://www.cgsecurity.org/mw/images/Backup_bs.gif[/IMG]

---

### Post by tvdij on 2008-11-24
I want to go ahead and say thanks for all the help thusfar for a linux newbie.

I installed testdisk and got to the "Rebuild BS" part, but after choosing that i get "Extrapolated boot sector and current boot sector are identical." like you mentioned.

---

### Post by caljohnsmith on 2008-11-24
> **tvdij said:**
> I want to go ahead and say thanks for all the help thusfar for a linux newbie.

I installed testdisk and got to the "Rebuild BS" part, but after choosing that i get "Extrapolated boot sector and current boot sector are identical." like you mentioned.
You're welcome, and I hope we can get your Windows booting again. :) How about booting your Windows Install CD, press "r" at the first main menu to get the "recovery console", and then run:
```
fixboot
chkdsk /r
```
And run the chkdsk as many times as it takes until it reports no errors. If you don't have a Windows Install CD, you can instead download a Windows Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). Let me know if either command returns errors, and after you are done running the commands, reboot and try to boot Windows again; let me know exactly what happens. :)

---

### Post by tvdij on 2008-11-24
Okay,

I ran 

"chkdsk /r"
"CHKDSK found and fixed one or more errors on the volume."

ran "chkdsk /r" again and the system returned:
"CHKDSK has finished checking the volume"

I tried booting XP but same thing happened, a blank screen

---

### Post by caljohnsmith on 2008-11-24
OK, I forgot that in your first post you said you can boot XP from the Super Grub Disk; is that still true? If it is, how about temporarily replacing Grub with a Windows MBR so that you should be able to boot directly into Windows again; that will give us a better idea if the problem is truly Grub-related. From your Windows Install CD, just run:
```
fixmbr
```
And then reboot, and you should be able to boot into Windows. You can temporarily use your Super Grub Disk to boot Ubuntu in the meantime, and if booting Windows works with a Windows MBR, we can add Ubuntu to the Windows boot loader so you can boot either Windows or Ubuntu on start up. Let me know how it goes. :)

---

### Post by tvdij on 2008-11-25
I restored the Windows XP MBR, and Windows is booting fine, thank you. Do you have a link to using Windows XP bootloader to dual-boot linux?

---

### Post by TeXtonyx on 2008-11-25
> **tvdij said:**
> I restored the Windows XP MBR, and Windows is booting fine, thank you. Do you have a link to using Windows XP bootloader to dual-boot linux?

It may seem like that is difficult but in practice I can add a 
new entry to the boot.ini menu in 12 seconds. But I have also
already downloaded free Bootpart and have installed grub to the
/boot partition of Ubuntu. So I'm going to provide some details,
I have two drives, Debian is on one and Ubuntu on the other, and
your situation is easier.

The advantage of installing grub to the first (bootable) Debian 
partition is that it doesn't write to the MBR. I use free Bootpart
to write an entry to my boot.ini :

-------------------------------------

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
/NOEXECUTE=OPTIN /FASTDETECT
c:\ubuntu.bin="Ubuntu"
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS

c:\debian.bin="Debian"

-------------------------------------

I can boot XP or Ubuntu or Debian from the XP boot.ini menu and it took a couple of minutes.

[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)  The file is,  26,172 bootpa26.zip
so it takes maybe 15 seconds to download.

I use Firefox (Debianspeak = Iceweasel) and download to my directory of C:\Downloads
When the download completes. The download complete window pops up.
I double-click on bootpa26.zip and extract bootpart.exe to C:\>
so it doesn't really take 15 seconds to extract bootpart.exe to C:\>

I have a Dos prompt icon on my Desktop, so I double-click it to open a command line.
Otherwise the Dos prompt is under Start->Accessories

C:\>bootpart  <enter>  [which then prints out the following]

Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : [http://www.winimage.com](http://www.winimage.com) and [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0 : 56d9f43b
0 : C:* type=7  (HPFS/NTFS), size= 65384518 KB, Lba Pos=63
1 : C:  type=5  (Extended), size= 15028807 KB, Lba Pos=130769100
2 : C:  type=83   (Linux native), size= 14354046 KB, Lba Pos=130769163
3 : C:  type=5   (Extended), size= 674730 KB, Lba Pos=159477255
4 : C:  type=82    (Linux swap), size= 674698 KB, Lba Pos=159477318
Physical number of disk 1 : 7e915766
5 : D:* type=83  (Linux native), size= 5454036 KB, Lba Pos=63
6 : D:  type=5  (Extended), size= 14900287 KB, Lba Pos=10908135
7 : D:  type=82   (Linux swap), size= 690763 KB, Lba Pos=10908198
8 : D:  type=5   (Extended), size= 14209492 KB, Lba Pos=12289725
9 : D:  type=83    (Linux native), size= 14209461 KB, Lba Pos=12289788
----------------------------------------

Probably the longest part of this is to identify the two correct Linux type 83 partitions

C:\> bootpart 2 ubuntu.bin Ubuntu <enter>
C:\> bootpart 5 debian.bin Debian <enter> [during grub install I put grub in the first 83 partition]

I don't know how long it takes you to type. But that's it. The two 512 byte segments
are created in C:\>  and entries are automatically generated in boot.ini. which I showed before
c:\ubuntu.bin="Ubuntu"
c:\debian.bin="Debian"

These are other advantages. It seems a lot quicker to me and more understandable to a new user. 
Here are some internet references,

[http://forums.majorgeeks.com/showthread.php?t=108021](http://forums.majorgeeks.com/showthread.php?t=108021)

[http://ubuntuforums.org/archive/index.php/t-499904.html](http://ubuntuforums.org/archive/index.php/t-499904.html)

[http://www.linux.com/feature/113945](http://www.linux.com/feature/113945)

The dd method of creating the 512 byte boot sector segment works
ok on the same drive but not on a second drive. Bootpart works
well across two drives and writes boot.ini automatically, much easier.

When I install Ubuntu during Step 7, Advanced, I click on Advanced
and choose /boot partition rather than the default of the MBR.

So in your case you need to reinstall grub to the /boot partition
of Ubuntu, not the MBR (hd0) which keeps the OS's independent of 
each other in case grub gets damaged, or you want to remove it,
or if XP breaks, you can boot Ubuntu with the Super Grub Disk
until you fix the Windows part and restore boot.ini bootloading.

---

### Post by caljohnsmith on 2008-11-25
I agree with TeXtonyx, probably the easiest way to add Ubuntu to your Windows boot loader is to use that "bootpart" program he linked to; that program automates the process of copying the Grub boot sector and adding it to the Windows boot.ini file so you don't have to do anything manually. But first you need to install Grub to the boot sector of your Ubuntu partition, so first do:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0,4)
grub> quit
```
Then follow TeXtonyx's instructions for using bootpart, and you should hopefully be all set. Let us know how it goes. :)

---

### Post by tvdij on 2008-11-25
The combination of the last two posts worked. 

Initially, I stalled bootpart and followed TeXtonyx's instructions. Bootpart didn't auto-add the C:\ubunu.bin to the boot.ini for whatever reason but i manually added it. Ubuntu was added to the MBR; I tried to boot ubuntu and it didn't work.

I then booted Ubuntu with Super Grub Disk and I setup grub on (hd0,0) as caljohn said.

Now when selecting Ubuntu on the MBR I get the grub screen and select whatever mode I wish to boot ubuntu in.

Thanks for the help guys, I certainly appreciate it. I'll try not to break Ubuntu anymore ;)

---

### Post by caljohnsmith on 2008-11-25
Glad to hear you have it working; cheers and have fun with Ubuntu. :)

---

