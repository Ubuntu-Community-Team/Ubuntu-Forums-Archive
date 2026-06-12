---
title: "Dual Booting with Windows Vista, can't access either OS, deleted grub"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by garymce on 2009-01-27
Hello

I'm sure you guys must get hundreds of threads like these, and I've been looking around trying to find similar problems but I haven't seen any that are particular to the massive cock-up I've made of this.

I've been using Vista for the past few months, having previously tried a single-boot Ubuntu installation on my old computer, and I decided tonight to try and get Vista and Ubuntu and have the best of both worlds.

I ran through the Ubuntu setup, chose Manual during the disk setup portion and asked it to format sda3 with ext3 and I set the mount point as "/" although I'm not sure if this was the right choice.

Setup then detected my Vista user account and asked if I wanted to import files and settings from it, which was a good sign! I told it to skip that step, and it then proceeded to list a summary. I foolishly clicked Advanced and saw the "Install Boot Loader" or similar, which was already checked, and underneath there was a drop-down menu asking where the loader would be installed to, which said "hdd0". I clicked it and for whatever reason decided that sda1, the Vista partition, would be the right place to install the boot loader instead, which in hindsight was probably a bad idea.

Installation asked me to restart, and when it got past the POST stage I was presented with a "grub >" interface, and I had absolutely no idea what to do then. I completely forgot about the Live CD, and instead inserted my Windows Vista disc and used the Recovery Console to try and fix the boot manager. However, Recovery Console couldn't detect the Vista operating system, and thus couldn't repair anything. I had also neglected to make a system restore point beforehand so that isn't an option either.

Here is the output from "fdisk -lu"

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x35d54527

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    81920078    40960008    7  HPFS/NTFS
/dev/sda2        81920160   934824023   426451932    7  HPFS/NTFS
/dev/sda3   *   934825984   976766975    20970496   83  Linux
```

sda1 is my Windows Vista partion, sda2 is the file storage partition, and sda3 is the Ubuntu partition.

So this is the current situation; although fdisk can see the Vista partition, I can't find it in Ubuntu's file browser, the Vista recovery disc can't find it, and the recovery disc also seems to have deleted grub since when I boot up now all I get is "No operating system" after it verifies the DMA pool data.

If anyone could help me recover my operating systems, I would be eternally grateful.

Thanks for your time
-Gary

---

### Post by Svensk023 on 2009-01-27
you should try re-installing ubuntu with a live CD or DVD, that will hopefully fix your problems. This will reset everything to default and, for me at least, has allowed me to one again access both Ubuntu and my windows vista OS's

---

### Post by ranch hand on 2009-01-28
I don't think I would reinstall yet.
```

/dev/sda3   *   934825984   976766975    20970496   83  Linux

```
indicates that you should be booting from there.

I would use the LiveCD and check the /boot/grub/menu.lst there first.  I may be a fairly simple edit job.

---

### Post by caljohnsmith on 2009-01-28
> **garymce said:**
> I foolishly clicked Advanced and saw the "Install Boot Loader" or similar, which was already checked, and underneath there was a drop-down menu asking where the loader would be installed to, which said "hdd0". I clicked it and for whatever reason decided that sda1, the Vista partition, would be the right place to install the boot loader instead, which in hindsight was probably a bad idea.

Unfortunately, yes, choosing "sda1" was not a good idea, because that means Grub was installed to the boot sector of your sda1 NTFS Windows partition; the sda1 partition won't be mountable, readable, or bootable until you can fix the boot sector. That's also (unfortunately) why the Vista recovery console couldn't detect your Vista install. How about booting your Vista CD again, go to the command line, and try:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
From that listing, find the drive letter for your sda1 NTFS partition (probably it will be "C"), and then do:
```
E:\boot\bootsect.exe /nt60 C:
```
Replace "E" above with the drive letter of your Vista CD, and replace "C" with the drive letter of your sda1 NTFS partition. Let me know if you can make it that far or if you run into problems. Also, to get Grub working, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> root (hd0,2)
grub> setup (hd0)
grub> quit
```
And please post the output before typing "quit". Then reboot, and see if you get the Grub menu OK. We can work from there if you want.

---

### Post by garymce on 2009-01-28
@ranch hand
/boot doesn't contain a /grub folder in it, I'm guessing that shouldn't be the case.

@caljohnsmith

I just tried the first part of your suggestion, trying to fix Window's MBR listing. This is what the result was.
```

DISKPART > list volume

Volume ### | Ltr | Label | Fs   | Type      | Size   | Status
Volume 0   |  E  | VISTA | UDF  | DVD-ROM   | 2943MB | Healthy
Volume 1   |  C  |       | RAW  | Partition | 39GB   | Healthy
Volume 2   |  D  | Files | NTFS | Partition | 407GB  | Healthy

```

I then followed your instructions for running bootsect.exe, this is the result;
```

E:\boot\bootsect.exe /nt60 C:

Target volume will be updated with BOOTMGR compatible bootcode
C:(\\?\Volume{13416947-ed94-11dd-a0d7-806e6f6e6963})
   Could not open the volume root directory
      Parameter is incorrect

```

I'm just about to reboot after trying your second suggestion, here's the output from Terminal;
```
grub> root (hd0,2)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

I'll edit the topic with the result of the reboot in a moment.

EDIT: That didn't work either.

```

GRUB loading stage 1.5.

GRUB loading, please wait.
Error 17

```

This is starting to get very heart-breaking :-p
Also, whenever I reboot after using the Live CD, my computer totally locks up at Verifying DMI Pool Data and I have to do a hard reset before it will progress, might this be causing a problem?

---

### Post by caljohnsmith on 2009-01-28
Ouch, looks like your computer has multiple problems right now. How about booting the Vista CD again, and this time try:
```
bootrec /fixboot
```
I'm doubtful if that will work since the previous bootsect command didn't work, but it is worth a quick try. If it says anything that hints at success, how about booting the Live CD again and posting the output of:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt && ls -l /mnt
```
If that still doesn't work, we can try to fix the Vista boot sector with "testdisk", but let me know first how far you get. Also, your Grub error 17 is a real bugaboo, because to get a Grub error 17 before seeing the Grub menu in your circumstances sometimes can be because of how your HDD is set up in BIOS. Is your HDD IDE or SATA? Also, can you go into your BIOS, and please let me know what HDD-related settings you have like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. In the meantime, I would recommend downloading the [Super Grub Disk]("http://www.supergrubdisk.org"), because I've seen where sometimes simply using a slightly different version of Grub can circumvent a Grub error 17 in your type of circumstance. Once you burn Super Grub and boot it up, try using it to reinstall Grub to your MBR (Master Boot Record). Sorry I don't remember the specifics of how to do it with Super Grub, but the menus are mostly friendly. Let me know how that goes or if you run into problems.
[QUOTE=garymce]Also, whenever I reboot after using the Live CD, my computer totally locks up at Verifying DMI Pool Data and I have to do a hard reset before it will progress, might this be causing a problem?[/QUOTE]
Yes, that definitely could be a problem. Let's try the above steps first though and we can come back to this.

---

### Post by garymce on 2009-01-28
Well "bootrec /fixboot" didn't work, I was told no recognisable operating system was installed.

> Is your HDD IDE or SATA? Also, can you go into your BIOS, and please let me know what HDD-related settings you have like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc.

My hard drive is a SATA drive, however in the BIOS it's listed as an IDE drive despite being hooked up via the skinny red cable to the L-shaped SATA slots, go figure.
All I could find relating to the hard drive was in the Standard CMOS Setup section, I've written it down;
```

IDE Channel 0 Master [Samsung HD502IJ]
IDE Channel 0 Slave  [None]
IDE Channel 1 Master [Sony DVD RW DW-Q1]
IDE Channel 0 Slave  [None]

IDE HDD Auto-Detection [Press Enter]
IDE Channel 0 Master   [Auto] (other options are None and Manual)
Access Mode            [Auto] (other options are CHS, LBA and Large)

The following is greyed out;
Capacity       500GB

Cylinder       65535
Head              16
Precomp            0
Landing Zone   65534
Sector           255

```

That's all I could find relating to the hard drives.

---

### Post by caljohnsmith on 2009-01-28
OK, hopefully testdisk can fix your Vista partition, so how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows partition, choose "Boot", then choose "Backup BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Backup BS" in testdisk, try doing:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt && ls -l /mnt
```
And please post the output. About your Grub problem, how about going into your BIOS and change the "Access Mode" to LBA and see if you still get the Grub error 17. If you do, try "Large" for the Access Mode. If neither LBA or Large work, I would go ahead and set it back to "auto" for now. Let me know how that goes.

---

### Post by garymce on 2009-01-28
Here's the output from mount;
```
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /mnt && ls -l /mnt
total 3713009
-rwxrwxrwx 1 root root         24 2006-09-18 21:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-10-28 06:36 Boot
-rwxrwxrwx 1 root root     333203 2008-01-21 02:25 bootmgr
-rwxrwxrwx 1 root root       8192 2008-10-28 06:36 BOOTSECT.BAK
-rwxrwxrwx 2 root root         10 2006-09-18 21:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 13:02 Documents and Settings
drwxrwxrwx 1 root root          0 2008-12-04 17:54 NST
-rwxrwxrwx 1 root root 3801698304 2009-01-28 02:48 pagefile.sys
drwxrwxrwx 1 root root          0 2008-01-21 02:33 PerfLogs
drwxrwxrwx 1 root root       8192 2009-01-23 15:17 ProgramData
drwxrwxrwx 1 root root      12288 2009-01-16 20:17 Program Files
drwxrwxrwx 1 root root          0 2008-12-18 02:09 $Recycle.Bin
drwxrwxrwx 1 root root      20480 2009-01-27 02:16 System Volume Information
drwxrwxrwx 1 root root          0 2008-12-05 00:43 Temp
drwxrwxrwx 1 root root       4096 2008-12-18 02:08 Users
drwxrwxrwx 1 root root          0 2008-11-19 13:29 Utils
drwxrwxrwx 1 root root      28672 2009-01-24 13:49 Windows
ubuntu@ubuntu:~$ 

```

Whatever it was meant to do, it appears to have done it :-p

I did notice while using testdisk that something appears to have happened to the cylinders.
```

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS              0   1  1  5099  73 45   81920016 [Vista]

Boot sector
Warning: Incorrect number of heads/cylinder 16 (NTFS) != 255 (HD)
Status: OK

Backup boot sector
Warning: Incorrect number of heads/cylinder 16 (NTFS) != 255 (HD)
Status: OK

Sectors are identical.

```

I also did an fdisk -lu, here's the result;

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x35d54527

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    81920078    40960008    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        81920160   934824023   426451932    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *   934838415   976768064    20964825   83  Linux
ubuntu@ubuntu:~$ 

```

I'm about to try the BIOS config for Error 17, I'll edit with the result shortly.

Edit: **[COLOR="Red"]Success![/COLOR]** Changing Access Mode to LBA got Grub to boot up this time :) I never saw anything about Windows though, it just kicked right into Ubuntu without displaying any prompts. However, from inside Ubuntu I can mount and access both NTFS partitions rather than just the Files one as before.

Massive thank-you, you are a true hero sir!

---

### Post by caljohnsmith on 2009-01-28
I'm so glad to hear you can boot into Ubuntu and can also access your Vista partition now. :) To add Vista to your Grub menu, how about opening your menu.lst first:
```
gksudo gedit /boot/grub/menu.lst
```
And add at the very bottom:
```
title Windows Vista
root (hd0,0)
chainloader +1
```
Also, add a pound sign or hash # in front of the "hiddenmenu" line near the top:
```
# hiddenmenu
```
Save, reboot, try Vista from your Grub menu, and let me know how far you get. We can work from there if necessary.

---

### Post by garymce on 2009-01-28
That worked fine, I can choose from either of them along with some safe mode-style Ubuntu options too.

I can't thank you enough, you're a real saviour!

---

### Post by caljohnsmith on 2009-01-28
That's great news, I'm glad Vista booted OK. I'm also really glad that changing your BIOS settings was all it took to get Grub going, because getting a Grub stage1.5 error 17 can sometimes be a royal pain to troubleshoot. Cheers and enjoy your new Ubuntu install. :)

---

