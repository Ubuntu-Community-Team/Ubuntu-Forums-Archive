---
title: "Error 16: Inconsistent filesystem stucture"
date: 2008-07-31
forum: General Help
---

### Post by ypellet on 2008-07-31
Hello,

I'm having some difficulties installing Ubuntu on my laptop using Wubi.

Laptop: Compaq 6910p, 2G of RAM, 80G HD (50% free space), Windows XP

After the Wubi installation, I rebooted the laptop and choose "Ubuntu" from the menu.  I'm getting the following messages :

[LIST]
[*]Try (hd0,0): NTFS5:
[*]Booting GRLDR...
[*]Press 'ESC' to enter the menu...
[/LIST]

And finally :

```
initrd /ubuntu/install/boot/initrd.gz
Error 16: Inconsistent filessystem structure
Press any key to continue
```

I'm getting the same problem even if I press ESC and choose any other item in the GRUB4DOS menu...

Here's what I know for sure and what I've tried :

[LIST]
[*]The ISO I'm using is not corrupted, I've installed it on a workstation using Wubi and it work fine.
[*]There is no fragmentation on the disk (ran defrag 3 times to be sure)
[*]No corruption on the NTFS (ran chkdsk /r two times)
[*]I'm using the latest version of Wubi (8.04.1-rev506)
[*]Windows was shutdown properly every time I rebooted
[/LIST]

I've been trying to find a solution for my problem for the past two days.  I've tried almost everything I could read in various forums and nothing get me past this "error 16"...

Please, help me!

Thank you for your time!

---

### Post by tinybit on 2008-07-31
Press c to gain a command-line prompt. At the prompt, enter these commands:

```

geometry (hd0)
geometry (hd1)
geometry (fd0)

```

Please post the message output.

If you are using NTFS filesystems, please search this forum for Bean123's post on NTFS filesystem check, and complete those check.

---

### Post by ypellet on 2008-08-01
Yes I'm using NTFS...

I've bean lookink for the post of Bean123, but I didn't find anything specific about "NTFS filesystem check"...

Like I said, I've done the basics I've red in this forum (chkdsk, defrag and proper shutdown of Windows).

Here are the details you ask for:

[LIST]
[*]geometry (hd0)
[INDENT]drive 0x80(LBA): C/H/S=16383/255/63, Sector Count/Size=263192895
[INDENT]Partition num: 0, Filesystem type is ntfs, partition type 0x7[/INDENT]
[/INDENT]
[*]geometry (hd1)
[INDENT]Error 21: Selected disk does not exist[/INDENT]
[*]geometry (fd0)
[INDENT]Drive 0x0(CHS): C/H/S=80/2/18, Sector Count/Size=2880/512[/INDENT]
[/LIST]

Thank you!

---

### Post by bean123 on 2008-08-01
To test ntfs, download fstest.exe from:

[http://grub4dos.sourceforge.net/grub4dos/](http://grub4dos.sourceforge.net/grub4dos/)

Then run the following test in windows:

fstest info C:\
fstest list C:\
fstest inode C:\$MFT
fstest inode C:\.

---

### Post by ypellet on 2008-08-01
Gee!  You guys are really fast!

**fstest.exe info c:\**
```
version: 1.0 build 3
part_base: 0x3F (0M)
part_leng: 0x950E482 (76316M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x1328
```

**fstest list C:\**
```
00026A7F             0  [cc_views]
0001EAD1             0  [Sharing]
0000492B          1532  AClient.cfg
00004922            49  AClient.dat
00020F45             0  [admin]
000060A5           483  AMCleanUp.log
000060A5           483  AMCLEA~1.LOG
00001D09             0  AUTOEXEC.BAT
00000DB2           221  boot.ini
00008E29             0  config.sys
00000DBA             0  [Documents and Settings]
00000DBA             0  [DOCUME~1]
000092C0             0  [Downloads]
000092C0             0  [DOWNLO~1]
0000780D             0  [IBM]
000070CA             0  [Installation Manager]
000070CA             0  [INSTAL~1]
00001D0A             0  IO.SYS
000093AA             0  [javadoc]
00001D0B             0  MSDOS.SYS
000099ED             0  [mvfslogs]
00004BC1             0  [Notes]
00000D98         47564  NTDETECT.COM
00000D94        250032  ntldr
0000001B     -83886080  pagefile.sys
00021E28             0  [pages]
00000F94             0  [Program Files]
00000F94             0  [PROGRA~1]
00007134             0  [RAD7]
00007140             0  [RAD7Shared]
00007140             0  [RAD7SH~1]
0000164F             0  [RECYCLER]
000201CC             0  [scripts]
00000DB8             0  [System Volume Information]
00000DB8             0  [SYSTEM~1]
00002005         31154  t.txt
00004497             0  [Temp]
00023102             0  [ubuntu]
000000C9             0  [Utils]
00022A1D             0  [WEB_2D_INF]
00022A1D             0  [WEB_2D~1]
0000001C             0  [WINDOWS]
00003C7B             0  [WinXP]
000204F4           208  WirelessDiagLog.csv
000204F4           208  WIRELE~1.CSV
0001CECF             0  [Workspaces]
0001CECF             0  [WORKSP~1]
0000CFEA             0  [WSAD51]
000076DA        188547  wubildr
00008B90          8192  wubildr.mbr
```

**fstest inode C:\$MFT**
```
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    $MFT
  $DATA (0x80) (nr,sz=293830656)
    4904+39168,63084272+534720
  $BITMAP (0xB0) (nr,sz=35872)
    4792+112
```

**fstest inode C:\.**
```
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=48)
  $FILENAME (0x30) (r,sz=68)
    .
  $OBJECT_ID (0x40) (r,sz=16)
  $SECURITY_DESCRIPTOR (0x50) (nr,sz=4144)
    44072+16
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=272)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=12288)
    46477768+24
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
```

Hope this helps...

Thanks!

---

### Post by bean123 on 2008-08-01
Basic information seems all right, perhaps you can also try the following:

fstest inode C:\ubuntu\install\boot\initrd.gz
fstest comp C:\ubuntu\install\boot\initrd.gz

---

### Post by ypellet on 2008-08-01
**fstest inode C:\ubuntu\install\boot\initrd.gz**
```
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=84)
    initrd.gz
  $DATA (0x80) (nr,sz=8367676)
    28051200+256,14311152+528,38512080+1016,45436512+2056,60803912+4416,71484208+3896,38596248+4176
```

**fstest comp C:\ubuntu\install\boot\initrd.gz**
```
File size : 8367676
Comparing ........
Succeed
```

Thanks again!

---

### Post by bean123 on 2008-08-01
Strange, fstest is ok, it shouldn't be the problem of ntfs. Perhaps you can also try grub2 ?

---

### Post by ypellet on 2008-08-01
I'm willing to give it a try...  Do you have some instructions?   I can't find much beside the grub2.rar on the GRUB4DOS project on SourceForge which contains two BIN files...

---

### Post by ypellet on 2008-08-09
Hi,

When I boot with Ubuntu Live CD, I'm not able to mount my NTFS partition, I'm told that it's an invalid NTFS partition...

Very strange...  

The OS was probably installed from a GHOST (or something similar).  Is it possible that the partition signature was altered and it's not 100% pure NTFS and that's why Ubuntu can't mount it and that's also why the NTFS installation with Wubi is not working properly?

Any idea what I could do to check this assumption or maybe correct it?

Thanks again!

---

### Post by bean123 on 2008-08-09
> **ypellet said:**
> Hi,

When I boot with Ubuntu Live CD, I'm not able to mount my NTFS partition, I'm told that it's an invalid NTFS partition...

Very strange...  

The OS was probably installed from a GHOST (or something similar).  Is it possible that the partition signature was altered and it's not 100% pure NTFS and that's why Ubuntu can't mount it and that's also why the NTFS installation with Wubi is not working properly?

Any idea what I could do to check this assumption or maybe correct it?

Thanks again!

Perhaps your partition is encrypted with TPM ?

---

### Post by ypellet on 2008-08-09
No, there's no encription on the partition...

Other ideas?

---

### Post by bean123 on 2008-08-10
> **ypellet said:**
> No, there's no encription on the partition...

Other ideas?

You can also try grub2:

[http://ubuntuforums.org/showthread.php?t=877750](http://ubuntuforums.org/showthread.php?t=877750)

---

