---
title: "Can't boot into XP since installing 8.10. Grub related"
date: 2008-11-01
forum: General Help
---

### Post by OneOfaKindDPC on 2008-11-01
Hey all, I'm still learning my ways around Ubuntu. I've solved this problem before when reinstalling ubuntu. I cannot figure it out for the life of me this time around. I wiped my linux partition and put 8.10 on there (had 8.04 which was installed after xp prior). I had to change the entry in 8.04 from hd0,0 to hd 0,4 and it worked fine... not the case since the 8.10 upgrade =(

Heres a copy of my fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee426033

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         132       32663   261313290    7  HPFS/NTFS
/dev/sda2           32664       36483    30684150    f  W95 Ext'd (LBA)
/dev/sda3               1         131     1052226   83  Linux
/dev/sda5           32664       35080    19414521    7  HPFS/NTFS
/dev/sda6           35081       35471     3140676   82  Linux swap / Solaris
/dev/sda7           35472       36483     8128858+  83  Linux

default grubb is set for 0,0. the sda5 is where my xp is located at. so I switch it to hd0,4.

heres my entry...

title Windows XP Professional
root (hd0,4)
chainloader +1
makeactive

Whenever I try to use this entry I get this message...

Error 12:Invalid device requested.

Thank you for any help provided.

---

### Post by caljohnsmith on 2008-11-01
If somehow your Windows XP ended up on sda5, a logical partition, then you have to take special steps to boot Windows XP from a logical partition. How about first posting:
```

sudo mkdir /mnt/sda1 /mnt/sda5
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5
ls -l /mnt/sda1 /mnt/sda5
cat /mnt/sda1/boot.ini /mnt/sda5/boot.ini
```
Note the "-l" is a lowercase L, not a one. We can work from there. :)

---

### Post by OneOfaKindDPC on 2008-11-01
/mnt/sda1:
total 1954308
drwxrwxrwx 1 root root          0 2008-06-09 18:34 450f516ee25d7178b69b1a9d65ff
-rwxrwxrwx 1 root root    1355849 2005-04-26 22:55 4in1449v.zip
drwxrwxrwx 1 root root          0 2008-06-09 18:34 a02a47be44d1771c87
-rwxrwxrwx 1 root root         24 2006-04-21 14:51 autoexec.bat
-rwxrwxrwx 2 root root    5393675 2005-04-17 10:09 Azureus_2.2.0.2_Win32.setup.exe
-rwxrwxrwx 2 root root     167991 2005-04-26 22:43 bookmarks.html
drwxrwxrwx 1 root root       4096 2006-06-10 07:29 Boot
-rwxrwxrwx 1 root root        497 2006-06-10 07:29 Boot.BAK
-rwxrwxrwx 1 root root        211 2005-04-27 13:52 BOOT.BKK
-rwxrwxrwx 1 root root        211 2008-06-08 17:17 boot.ini
-rwxrwxrwx 1 root root     444796 2006-05-18 20:55 bootmgr
-rwxrwxrwx 1 root root       8192 2006-06-10 06:59 BOOTSECT.BAK
drwxrwxrwx 1 root root       4096 2008-09-07 00:29 Config.Msi
-rwxrwxrwx 1 root root         10 2006-04-21 14:51 config.sys
drwxrwxrwx 1 root root      69632 2008-07-15 11:44 D-Money
-rwxrwxrwx 1 root root      58444 2008-07-21 17:53 FinancialAidDescriptions.pdf
-rwxrwxrwx 2 root root    4827008 2005-04-16 00:10 Firefox Setup 1.0.3.exe
-rwxrwxrwx 2 root root        856 2005-08-27 13:29 flashplayer.xpt
drwxrwxrwx 1 root root          0 2005-06-03 03:38 found.000
drwxrwxrwx 1 root root          0 2005-06-22 11:53 found.001
-rwxrwxrwx 2 root root    5865372 2005-04-26 23:02 ga302t_v0293.zip
-rwxrwxrwx 1 root root 1073012736 2006-07-07 23:37 hiberfil.sys
-rwxrwxrwx 1 root root      36350 2005-05-14 01:28 install.log
drwxrwxrwx 1 root root       4096 2007-05-03 15:16 Intel10.3
-rwxrwxrwx 1 root root          0 2005-04-27 13:57 IO.SYS
drwxrwxrwx 1 root root          0 2006-05-03 12:06 Linksys Driver
drwxrwxrwx 1 root root          0 2008-07-10 00:22 Logs
-rwxrwxrwx 1 root root        278 2005-12-04 21:46 log.txt
-rwxrwxrwx 2 root root  907252910 2005-04-26 03:00 Microsoft.Windows.Longhorn.b5048.32bit.WinHec.DVD-WinBeta.rar
-rwxrwxrwx 1 root root          0 2005-04-27 13:57 MSDOS.SYS
drwxrwxrwx 1 root root          0 2006-01-11 13:41 MSOCache
-rwxrwxrwx 2 root root        144 2005-04-25 18:33 New Text Document (2).txt
-rwxrwxrwx 1 root root      47564 2008-04-23 17:30 NTDETECT.COM
-rwxrwxrwx 1 root root     302432 2005-04-01 12:14 ntldr
-rwxrwxrwx 2 root root        472 2006-05-18 23:00 ntsign_incr.txt
drwxrwxrwx 1 root root       4096 2008-06-30 01:46 NVIDIA
drwxrwxrwx 1 root root       4096 2006-06-11 20:21 ProgramData
drwxrwxrwx 1 root root      40960 2008-10-11 12:39 Program Files
drwxrwxrwx 1 root root          0 2006-05-19 00:42 $RECYCLE.BIN
drwxrwxrwx 1 root root          0 2006-05-18 22:36 Recycled
drwxrwxrwx 1 root root       4096 2008-06-09 18:33 RECYCLER
-rwxrwxrwx 2 root root     193770 2005-04-26 22:54 SATA_FloppyDisk.zip
-rwxrwxrwx 2 root root     305354 2005-02-11 00:40 ShowLetter.jpg
drwxrwxrwx 1 root root       4096 2007-09-28 13:36 System Volume Information
drwxrwxrwx 1 root root          0 2008-06-09 16:26 Temp
-rwxrwxrwx 1 root root         45 2005-05-29 00:23 TEST.XML
drwxrwxrwx 1 root root     434176 2008-09-15 23:31 The Rock
drwxrwxrwx 1 root root       4096 2006-06-10 14:47 Users
-rwxrwxrwx 2 root root       1870 2005-02-03 14:35 Verizon Online DSL Settings.htm
drwxrwxrwx 1 root root       4096 2007-10-16 16:05 WinXp CD
-rwxrwxrwx 2 root root    1311292 2005-02-01 16:52 ZippoWallpaper_1280.bmp

/mnt/sda5:
total 5423196
drwxrwxrwx 1 root root       4096 2008-10-20 17:53 Config.Msi
drwxrwxrwx 1 root root       4096 2008-06-08 17:30 Documents and Settings
-rwxrwxrwx 1 root root       1305 2008-09-29 22:43 IPH.PH
drwxrwxrwx 1 root root          0 2008-06-09 18:32 MSOCache
-rwxrwxrwx 1 root root 5553258496 2008-10-26 12:31 pagefile.sys
drwxrwxrwx 1 root root      12288 2008-10-11 12:39 Program Files
drwxrwxrwx 1 root root          0 2008-08-28 00:38 RECYCLER
drwxrwxrwx 1 root root       4096 2008-06-08 17:28 System Volume Information
drwxrwxrwx 1 root root       4096 2008-09-07 10:28 TEMP
drwxrwxrwx 1 root root      61440 2008-10-24 15:09 WINDOWS
d-rock@d-rock-desktop:~$ cat /mnt/sda1/boot.ini /mnt/sda5/boot.ini



Hope that helps, and thank you for the help.

---

### Post by caljohnsmith on 2008-11-01
Your Windows XP boot files are in your sda1 data partition, so it would be most ideal to move them back to the Windows sda5 partition and modify boot.ini so you can boot Win XP from sda5. To do that, follow all these steps carefully:
```
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5
sudo mv /mnt/sda1/boot.ini /mnt/sda1/ntldr /mnt/sda1/NTDETECT.COM /mnt/sda5/.
gksudo gedit /mnt/sda5/boot.ini
```
Next change the two "partition(1)" instances in your boot.ini as follows:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)[COLOR="Red"]partition(3)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR="Red"]partition(3)[/COLOR]\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
```
Next modify your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following entry for Windows at the end of your file:
```
title Windows XP
root (hd0,4)
chainloader +1
```
Reboot, and if you don't have any other Windows-related issues, that should be all it takes to boot Windows. If you do have problems, let me know exactly what happens after you choose Windows from the Grub menu. Otherwise let me know how it goes. :)

---

### Post by OneOfaKindDPC on 2008-11-01
We're close... I think hehe. I tried it just as you asked. When I selected XP at the boot screen it says 


Starting Up......
_

wouldn't go any further

---

### Post by caljohnsmith on 2008-11-01
OK, you probably just need testdisk to fix the Windows boot sector, so do:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens.

---

### Post by OneOfaKindDPC on 2008-11-01
It worked! thank you so much for your help. =)

Just gonna throw it out there because you seem quite knowledgeable. I'm having problems shutting down ubuntu 8.10. after it kills the GUI it shows the blinking _     usually thats as far as it goes, thought sometimes after about 20 seconds it will start going through the this of things to shutdown.... gets about 4 down to alca (I think thats what it was called) and just stay stuck until I kill the power.

---

### Post by caljohnsmith on 2008-11-01
Glad you have Windows booting OK now; about your shutdown issue, I'm not sure. Probably your best bet is to start a new thread and give all the details, and someone can probably help. Cheers and have fun.

---

### Post by OneOfaKindDPC on 2008-11-01
Will do, thanks again for your help. Couldn't have done it without your help. :guitar:

---

