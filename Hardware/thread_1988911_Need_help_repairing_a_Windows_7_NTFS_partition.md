---
title: "Need help repairing a Windows 7 NTFS partition"
date: 2012-05-28
forum: Hardware
---

### Post by McGuffin on 2012-05-28
Hi

I'm having something of a problem trying to repair a laptop, which is a Dell Inspiron N5030 running Windows 7, via an Ubuntu live CD.

I do not have a Windows 7 installation disk or repair disk, so I am attempting to fix it through Ubuntu.  I found various suggestions on older threads and elsewhere about how to fix this problem, but none of the solutions I've found seem to have worked.

First I tried using ntfs-3g and ntfsprogs to run the ntfsfix command, which gives the following output:

```
sudo ntfsfix /dev/sda3
Mounting volume... pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... Failed to empty $FILE_LogFile/$DATA: Input/output error.
FAILED
Failed to reset $Logfile: Input/output error.
```Then I tried lilo:

$ sudo lilo -M /dev/sda mbr

That seemed to execute without errors, but doesn't appear to have fixed the problem.


Finally, I tried to force a mount in order to recover any data, using:

$ sudo ntfs-3g -o force,rw /dev/sda3 /media/windows

That produced the following error:

> 
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's softRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details."I have no idea what this error message means (though I know that chkdsk is a DOS command - but because the Dell recovery partition is not booting, I can't run DOS!).

So, the question is is there anything else I can do in Ubuntu to fix the problem, or do I need to get my hands on a system repair disk?

I am on the verge of giving up, and trying to wipe the HD clean and install Ubuntu instead (if this is even possible? I don't know!) 

EDIT: I also used bootinfoscript, which gave the following:

>                   Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    30,926,847    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,926,848   625,140,399   594,213,552   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        CC70378A703779F2                       ntfs       Recovery
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 



Apologies for the long thread, any help greatly appreciated.

Thanks

McG

---

### Post by Bucky Ball on 2012-05-28
> In the first case run chkdsk /f on Windows
then reboot into Windows twice.

From your BootInfoScript. Try that. Can't give you details on how; think you boot into some kind of safe mode or from recovery. . You'll have to have a browse ...

sda1 and 2 look like they might be Dell recovery partitions, incidentally, if you don't have a recovery CD. There would be some key combination you hit at boot to start them up ...

---

### Post by kc1di on 2012-05-28
Hi McGuffin,
I guess I have a question for you. and that is does windows boot at all. I'm not exactly sure what the problem is.  you say you have a bad partition but never say what the problem really is.

please give us a little more to go on like what are symptoms?

Will try to help

---

### Post by kagashe on 2012-05-28
Download freeDOS Live CD from [here]("http://www.z80.eu/freedoscd.html").

Run chkdsk <drive letter> /f

Try to boot into Windows.

Kamalakar

---

### Post by McGuffin on 2012-05-28
> **kc1di said:**
> Hi McGuffin,
I guess I have a question for you. and that is does windows boot at all. I'm not exactly sure what the problem is.  you say you have a bad partition but never say what the problem really is.

please give us a little more to go on like what are symptoms?

Will try to help


My apologies, I've been so wrapped up in thinking about solutions, I forgot to explain the problem!

The Dell Inspiron loading screen and progress bar appears, then it flips to black screen with a winking cursor for a couple seconds, then it displays:

"A disk read error occurred
Press Ctrl+Alt+Del to reRECOVERY****"

The 4 *'s are strange symbols I've never seen before - don't know if the're important but the first looks like an l with a ^ on top, a 'squashed' r, an upside-down 'F' and something that looks like the greek letter pi.

Pressing ctrl+alt+del just seems to reset the problem, and I end up back in the same place.

---

### Post by McGuffin on 2012-05-28
> **kagashe said:**
> Download freeDOS Live CD from [here]("http://www.z80.eu/freedoscd.html").

Run chkdsk <drive letter> /f

Try to boot into Windows.

Kamalakar

The link to the LiveCD that your link leads to doesn't appear to be working.  Do you have an alternative source for the FreeDOS LiveCD?

---

### Post by wilee-nilee on 2012-05-28
Can you f8 the windows to a command line or a safe boot to run the chkdsk?

Lilo is also a bootloader.

---

### Post by kagashe on 2012-05-28
> **McGuffin said:**
> The link to the LiveCD that your link leads to doesn't appear to be working.  Do you have an alternative source for the FreeDOS LiveCD?

Click [here]("http://ftp.gwdg.de/pub/misc/freedos/files/distributions/1.0/").

You need to download [fdfullcd.iso]("http://ftp.gwdg.de/pub/misc/freedos/files/distributions/1.0/fdfullcd.iso").

Please note that this is an old version of freedos with Live CD but should be sufficient to run chkdsk.

The current version of freedos does not come on Live CD version.

Kamalakar

---

### Post by Bucky Ball on 2012-05-28
You need to try this:

> **wilee-nilee said:**
> Can you f8 the windows to a command line or a safe boot to run the chkdsk?

... before doing any of this:

> **kagashe said:**
> Click [here]("http://ftp.gwdg.de/pub/misc/freedos/files/distributions/1.0/").

You need to download [fdfullcd.iso]("http://ftp.gwdg.de/pub/misc/freedos/files/distributions/1.0/fdfullcd.iso").



If you can get to a command line in Win with F8 and run chkdsk you should make some progress.

---

### Post by ahallubuntu on 2012-05-28
Download a Windows 7 disc and burn your own Windows 7 version that matches your own version (e.g. Home Premium) per instructions:

[http://forum.notebookreview.com/windows-os-software/428068-legal-windows-7-download-links-just-like-vista-before.html](http://forum.notebookreview.com/windows-os-software/428068-legal-windows-7-download-links-just-like-vista-before.html)

First try Startup Repair and chkdsk from a command prompt.  If that doesn't work, try repairing your existing installation.

Of course, it is assumed that you have checked the hard drive's S.M.A.R.T. status (SmartMonTools) and that there are no glaring errors like bad sectors; if so, don't bother trying to fix it.  Instead, recover what you need with file recovery tools and replace the hard drive.

---

### Post by SavinderShergill on 2012-05-28
[SIZE=3][FONT=Calibri]Hi,[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]My name is Savinder and I work for the Social Media and Community Team at Dell[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]It appears to be an issue with the operating system corruption. I would like to inform that the windows operating system cannot be repaired with the help of Ubuntu media CD. You would require to have a Win 7 Media DVD.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I have the following resolutions for you:[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]There might be a chance that the hard drive has gone bad hence you can run  ePSA diagnostics by following the steps below to verify the same: [http://dell.to/MTVApn](http://dell.to/MTVApn)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]If the test passes you can follow the steps in the following link to further troubleshoot the issue: [http://dell.to/eM8hJ6](http://dell.to/eM8hJ6)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Even if it does not fix the issue then you would need to reinstall windows on the system, for which you would need the windows DVD. I would request you to call dell technical support for the same.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]However if you have never ever formatted the hard drive then you can take the system back to factory settings by following the steps below: But doing so you would lose the data on the system: [/SIZE][/FONT][[FONT=Calibri][SIZE=3]http://dell.to/KLvum8[/SIZE][/FONT]]("http://dell.to/KLvum8")[SIZE=3][FONT=Calibri]. So request you to please take a backup of your data on a pen drive.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Hope the information helps you to resolve the issue.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Thanks,[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Dell-Savinder S[/FONT][/SIZE]

---

