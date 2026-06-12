---
title: "Recovering MBR and windows startup after removing Ubuntu disk"
date: 2008-10-25
forum: General Help
---

### Post by 5circles on 2008-10-25
I'm hoping the forum can help even though I'm (partly) now back in Windows land.

I had a second drive installed in a Windows system.  This drive was   set up for Ubuntu, but not currently being used, which makes what happened even more puzzling.

I decided to wipe the drive and remove it from the system.  Warning to others - if I'd removed the drive first, then rebooted, I would have seen the problem and recovery would have been simpler.

After the wipe (done with Eraser) was complete, I removed the drive.  When I rebooted, I saw a Grub Error 21 error.  Obviously the second drive was somehow involved in boot up.  But since I'd wiped it, I assumed that putting it back wouldn't do any good.  Perhaps I was wrong on that, but when I tried it later it didn't help.

I booted from the Recovery CD for the system (windows XP) and ran fixmbr.  Now I no longer see the Grub error 21, but instead a message that says 'system32\hal.dll is missing - please reinstall'.  I don't know how to do that, or if I should just try more serious recovery procedures - and risk losing the rest of the data and apps.

I've now booted from the Live Ubuntu 8.04 CD, and am in the middle of copying the files from the hard drive to the other hard drive that I reinstalled.  There are 3 partitions - 7 Gig system recovery, 177 Gig main, and a 2 Gig (don't know what this is - it looks like something for Windows System Restore).

Once I have all that data copied over, I'll feel more comfortable trying something more extreme.  But if anyone can suggest a way to recover easily, I'll be very grateful.

Thanks
Mike

---

### Post by caljohnsmith on 2008-10-25
Hi Mike, sometimes a hal.dll error can be simply because your boot.ini file specifies the wrong partition/drive for Windows. From your Live CD, how about opening a terminal (applications > accessories > terminal) and post the output of:
```
sudo fdisk -lu
```
And for whichever is your Windows partition, e.g. sdaX, do:
```
sudo mount /dev/sdaX /mnt
ls -l /mnt
cat /mnt/boot.ini
```
And please post the output (note "-l" is a lowercase L, not a one). We can work from there. :)

---

### Post by 5circles on 2008-10-25
From fdisk:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    14621039     7310488+   c  W95 FAT32 (LBA)
/dev/sda2   *    14621040   386603279   185991120    7  HPFS/NTFS
/dev/sda3       386603280   390715919     2056320    c  W95 FAT32 (LBA)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007d0fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    14329979     7164958+   b  W95 FAT32
/dev/sdb2        14329980   606196709   295933365    7  HPFS/NTFS
/dev/sdb3       606196710   625137344     9470317+   b  W95 FAT32

```


This is from the mounted drive.  It looks like it is showing the modified boot.ini after the recovery tool made changes.

```
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS


[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
```

Mike

---

### Post by caljohnsmith on 2008-10-26
It would help if you would actually post the output of those previous commands I gave, because then I could see a directory listing of your Windows partition and check if all the boot files are there. :) So if it's not too much trouble, please post:
```
sudo mkdir /mnt/sda2
sudo mount /dev/sda2 /mnt/sda2
ls -l /mnt/sda2
```

---

### Post by 5circles on 2008-10-26
Hi.  I apologize - I thought I'd posted all the relevant output, but I see that I hadn't posted all that you asked for - particularly the output of the ls.  I will post that as a separate message - I have to go back to the other system and reboot.

Also, I'm not sure if this is even going to be possible or worth it.  Here is a message that I thought was posted last night, but apparently didn't get posted because I'd timed out.

> It is maybe too late to do a decent job of recovery now.

After I had a copy of all partitions on the original disk I tried a couple more recovery steps from HP.  The system told me that it wouldn't lose data and it appeared it would give me a chance to do a system restore.

Unfortunately, I now seem to be in limbo.  All the data seems to be there (plus I have the additional copy).  But when the system came up after the restart (and chkdsk) things didn't look good. The HP_Administrator and the Guest accounts are the only users. The System Restore didn't help because it  All the icons for applications are still there, but many of them don't work. 

I don't know if having the second drive installed when I tried to do the restore stopped it working, because it look like some drive letters are mangled.  But it is still probably too late.

Or is it?

I still have the information copies on the second drive, but some of what was on the first drive has been replaced.

Thanks
Mike

---

### Post by ciscosurfer on 2008-10-26
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by 5circles on 2008-10-26
> **caljohnsmith said:**
> It would help if you would actually post the output of those previous commands I gave, because then I could see a directory listing of your Windows partition and check if all the boot files are there. :) So if it's not too much trouble, please post:
```
sudo mkdir /mnt/sda2
sudo mount /dev/sda2 /mnt/sda2
ls -l /mnt/sda2
```

Note that I'm using sdb2 because that's where I copied all the partitions before further messing things up:

```
sudo mkdir /mnt/sdb2
   No output
```

```
 sudo mount /dev/sdb2 /mnt/sdb2
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb2 /mnt/sdb2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb2 /mnt/sdb2 ntfs-3g force 0 0

```
Followed choice 2
```
sudo mount -t ntfs-3g /dev/sdb2 /mnt/sdb2 -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.

```

```

 ls -l /mnt/sdb2
total 2110694
drwxrwxrwx 1 root root       4096 2008-05-28 01:36 5CirclesOld
drwxrwxrwx 1 root root       4096 2008-09-18 00:27 5CirclesResearch
drwxrwxrwx 1 root root          0 2006-06-15 02:10 ACTfromSpringbank - delete when checked
-rwxrwxrwx 1 root root        363 2006-01-28 19:20 Alerts.txt
-rwxrwxrwx 1 root root        100 2005-03-16 02:44 AUTOEXEC.BAT
-rwxrwxrwx 1 root root        211 2005-12-30 20:41 BOOT.BAK
-rwxrwxrwx 1 root root        281 2005-12-30 20:55 boot.ini
drwxrwxrwx 1 root root      32768 2005-12-30 20:55 cmdcons
-rwxrwxrwx 1 root root     260272 2004-08-10 12:00 cmldr
drwxrwxrwx 1 root root          0 2005-01-28 01:43 CMPNENTS
drwxrwxrwx 1 root root       4096 2008-04-02 04:20 comScore
-rwxrwxrwx 1 root root         73 2007-05-17 06:33 config.001
-rwxrwxrwx 1 root root         73 2007-02-17 22:34 config.bak
drwxrwxrwx 1 root root          0 2008-10-25 01:23 Config.Msi
-rwxrwxrwx 1 root root         73 2007-05-17 06:33 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-04-16 17:35 Documents and Settings
drwxrwxrwx 1 root root      32768 2008-07-24 23:00 Downloads
drwxrwxrwx 1 root root          0 2007-05-17 05:47 drivers
-rwxrwxrwx 1 root root      46080 2007-09-05 03:42 FaxAdditionalK1s.doc
drwxrwxrwx 1 root root          0 2007-05-17 05:47 fb725c11dd63f849766f6549
drwxrwxrwx 1 root root       4096 2008-05-28 01:39 FinancialData
drwxrwxrwx 1 root root          0 2006-09-25 00:55 Focus Group Articles
-rwxrwxrwx 1 root root 2138427392 2008-10-24 04:44 hiberfil.sys
drwxrwxrwx 1 root root          0 2007-05-17 05:47 History
drwxrwxrwx 1 root root       4096 2007-07-09 22:09 hp
-rwxrwxrwx 1 root root          2 2005-03-16 01:32 hpbi.log
-rwxrwxrwx 1 root root    3397690 2007-05-30 20:13 HuskyInstallerLog.txt
drwxrwxrwx 1 root root    2056192 2007-06-19 04:19 I386
-rwxrwxrwx 1 root root          0 2005-01-28 09:41 IO.SYS
drwxrwxrwx 1 root root       4096 2008-03-07 02:31 JuraDesigns2006TaxReturn
drwxrwxrwx 1 root root       4096 2008-03-12 00:47 JuraDesigns2007TaxReturn
drwxrwxrwx 1 root root       8192 2008-05-01 20:35 JuradesignsWebSite
drwxrwxrwx 1 root root          0 2006-04-23 22:58 KPCMS
drwxrwxrwx 1 root root          0 2007-05-17 05:46 Local Settings
drwxrwxrwx 1 root root          0 2007-06-07 03:47 moin
-rwxrwxrwx 1 root root          0 2005-01-28 09:41 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-02-15 20:48 MSOCache
drwxrwxrwx 1 root root          0 2008-04-18 19:10 My Images
drwxrwxrwx 1 root root       4096 2007-09-05 04:21 My Web Sites
drwxrwxrwx 1 root root          0 2007-05-17 05:46 NetworkService
drwxrwxrwx 1 root root          0 2008-01-16 18:23 NewBusiness2008

-rwxrwxrwx 1 root root      47564 2004-08-10 12:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-09-15 23:10 ntldr
drwxrwxrwx 1 root root          0 2007-05-17 05:52 NVIDIA
drwxrwxrwx 1 root root      20480 2007-05-17 05:54 Office2k3
drwxrwxrwx 1 root root      32768 2008-10-25 01:23 Program Files
-rwxrwxrwx 1 root root          0 2008-05-28 01:36 pspbrwse.jbf
drwxrwxrwx 1 root root       4096 2007-07-19 20:32 Python22
drwxrwxrwx 1 root root       4096 2008-06-04 23:02 Python25
drwxrwxrwx 1 root root          0 2006-10-29 19:24 RECYCLER
drwxrwxrwx 1 root root      12288 2007-06-19 04:19 SC
drwxrwxrwx 1 root root       4096 2008-05-15 02:17 SIERRA
-rwxrwxrwx 1 root root         49 2008-06-04 10:46 smp.bat
drwxrwxrwx 1 root root       4096 2008-03-17 20:21 SnowshoeLabs
-rwxrwxrwx 1 root root       3540 2007-01-12 05:35 spsslogfile.log
drwxrwxrwx 1 root root       4096 2006-11-30 08:20 sshadmin
drwxrwxrwx 1 root root          0 2007-07-19 20:32 STATBOX
drwxrwxrwx 1 root root          0 2008-01-12 21:35 SwSetup
-rwxrwxrwx 1 root root   16450560 2005-12-30 21:14 SYSCMNDR.SYS
drwxrwxrwx 1 root root          0 2005-12-30 20:42 sysprep
-rwxrwxrwx 1 root root         18 2008-10-25 18:55 SYSREST
drwxrwxrwx 1 root root       4096 2008-10-26 05:10 System Volume Information
drwxrwxrwx 1 root root          0 2008-07-18 00:36 Temp
drwxrwxrwx 1 root root          0 2007-05-17 05:47 Temporary Internet Files
-rwxrwxrwx 1 root root        331 2008-09-02 04:28 temp.qba.nd
drwxrwxrwx 1 root root          0 2006-11-30 08:59 tools
drwxrwxrwx 1 root root          0 2007-05-20 02:35 Trax
drwxrwxrwx 1 root root     139264 2008-10-24 04:55 WINDOWS
drwxrwxrwx 1 root root      49152 2007-07-19 20:32 WINNT

```

It looks like I had System Commander running at one time.

Does this help?

---

### Post by caljohnsmith on 2008-10-26
Yes, that helps, it looks like you have all the three main Windows boot files, so that's good. Also, it looks like your boot.ini points to the correct disk and partition, so that's fine too. While you have Windows mounted, make sure you have the following files:
```
C:\Windows\system32\ntoskrnl.exe
C:\Windows\system32\hal.dll
```
Do you have your Windows Install CD? If so, I would recommend that you boot that up, go to the "recovery console", and run:
```
chkdsk /r
```
And run chkdsk as many times as it takes until it reports no errors. Let me know if chkdsk reports any errors, and if it fixes anything, go ahead and reboot to see if anything changed. Also, just to make sure, you have your BIOS set to boot your sda drive before the sdb drive, correct? That's important at this point, although your BIOS is probably all ready set that way. And last question, was Windows booting fine from Grub when you had your dual boot setup?

---

### Post by TeXtonyx on 2008-10-26
If you install grub to the boot partition during Step 7, Advanced
of the live cd Ubuntu installation, then you never get the Windows
MBR overwritten so you can't boot from it. You can add Ubuntu to
the boot menu with Easybcd (Vista) or Bootpart (XP). Yes, it takes
5 minutes more. How many hours have you spent on this? This is the
second post about this I've made today, and your problem, sometimes
not so severe, appears at least 10 times a month on the forum from
different high and dry users. How many of these people are happy
with their Ubuntu experience? How many converts come to believe?

The other thing is that if you choose guided install, resize Windows,
part of the Windows boot sector can get corrupted, so that fixmbr
isn't enough. Resizing/shrinking the Windows partition and leaving
the space created as unallocated, gives one the choice of 'guided
install using largest free space' from the live cd install. This
way you get to check that your Windows installation is still able
to boot before installing Ubuntu with the boot sector option. 
That narrows troubleshooting now, much easier. Maybe your problem
could have been fixed with testdisk. But you didn't know about it.

Like most people I used to ignore the advice of making backups.
After many learning experiences I finally saw the light. With
Acronis I can back up Windows and Linux and restore Windows or
Linux. All the applications and data work. I've tried the repair
install with the Windows cd more than once. If you rewrite Windows
to Windows.000 it will spare your data and some of the applications
will still work, but that is not nearly as convenient or complete.

---

### Post by 5circles on 2008-10-26
Caljohnsmith, 

I'm still wondering about the advisability of continuing on this path versus a reinstall of Windows with better cleanup.  But even though that might be better long term, reinstalling all the apps is a pain, so I want to keep trying.  But now that I've messed up the orginal drive (by letting too much of the recovery be done), can I try the same thing with the second drive or am I going to run into trouble because Windows is connected with the drive configuration?  I can copy back the files from the second drive to the first drive and then try again with chkdsk.  That seems safest as long as a file copy will be OK (other than the boot area).

The ntoskrnl.exe and hal.dll files are there.

No, Grub wasn't working earlier.  I started this thread because I was surprised after removing the second drive to find that it was somehow connected with the boot up process.   I really want to get back to a Windows XP system and then add in Ubuntu again.

---

### Post by 5circles on 2008-10-26
TeXtonyx,

I take your point about backups.  While I'm pretty good about backing up data, I haven't been as good on Disaster Recovery.  But, as I mentioned in the other reply, I'm not in this situation because I didn't do the right thing with a Ubuntu installation (except perhaps historically).  I have another system that I just added Easybcd to, and I'm grateful for the help.  When I get this XP system back up I'll be looking at the right approach for long term stability.  Thanks

---

### Post by TeXtonyx on 2008-10-26
Another advantage of installing grub to the /boot partition is
that if Windows goes down, you can still boot Ubuntu with the
Super Grub disk. This advice if for the future and the theme is
don't put all your eggs in one basket which includes backing up.

There is still some chance that your system can be recovered, so
good luck.

---

### Post by caljohnsmith on 2008-10-26
Just to clarify, was Windows working fine until you installed Ubuntu on the external drive, and since then you haven't been able to boot Windows? 

If you had Windows working before installing Ubuntu, then I agree with you, I like your idea of copying the backup Windows back to your sda drive; then you can run chkdsk as you say, and you will probably have a better chance of recovery. How exactly are you going to do the file copy?

---

### Post by 5circles on 2008-10-26
> **caljohnsmith said:**
> Just to clarify, was Windows working fine until you installed Ubuntu on the external drive, and since then you haven't been able to boot Windows? 

It is even more odd than that.  A little background might be in order.  This system is about 3 years old and gone through various convolutions with the main drive -  including (I think) having system commander at one point, and a small Windows 2000 partition - I think that was when I had problems with compatible apps.  I restored at one point from the original disks without losing apps - which is probably why the apps are in a mess.  I'm not certain if I ever had Linux running, but if I did it was on a second drive.  The drive that caused the problem was an internal drive that I'd previous used in a different system (with Ubuntu), and moved to this one when I needed some more space to move things around.  I made the mistake of running eraser, whereas I should have first removed the drive to check whether everything still worked.  I never tried to install Ubuntu.  Perhaps I should have done, because then the install might have made the Windows side work.

> If you had Windows working before installing Ubuntu, then I agree with you, I like your idea of copying the backup Windows back to your sda drive; then you can run chkdsk as you say, and you will probably have a better chance of recovery. How exactly are you going to do the file copy?

I'm trying to keep all the files I copied from the original system intact.  There is enough space on the second drive to create another partition, so I'm trying to shrink the partition I created earlier.  Unfortunately, when I just tried this with gparted it failed (twice).  I don't know if it was because the partition was NTFS - chosen because that was how the original was set up.  I don't think I have enough drive space around to make a copy another way, so I'll just have to reformat the partition on the first drive and copy again.  I will do the actual file copy using 'cp - dpRuv' as I did before.

---

### Post by TeXtonyx on 2008-10-26
There is a total backup which requires a storage area as large as
the original drive. That copies the location of free space too.
The next kind of backup copies all the files and MBR. It might
take up 20GB for a 60GB hard drive, depending on the level of
compression. This will completely restore your system.

Then there is another kind of backup where you save important docs
and pictures etc, data IOW, to a safe place. Suppose you backup or
copy in this sense, your Program Files folder which has all of your
applications installed into it. 

If you install Windows fresh, it will create a new Programs Folder.
If you copy the content of your backed up Programs folder into this
new folder, most of your applications will not work. The reason is
that when one installs an application a lot of information 
writes to the Registry. So the old programs in the new Program Files 
folder have to have matching information in the Registry. When
Windows is freshly installed it creates a new Registry. If you have
a backed copy of the old Registry (matching the old applications)
you can write that into the new Registry and many more of your
applications will work. Other things, such as an old Firefox 
profile, can be used to overwrite a newly installed FF profile.
You can usually recover your emails if you backed up that folder.
I wasn't sure you had thought of the role of the Registry...

---

### Post by 5circles on 2008-10-27
Well, I think I'm at the end of the road for an easy recovery - unless anyone has any other ideas.

I copied all the files over and then ran the recovery console.  It won't run chkdsk or fixmbr - says the disk has unrecoverable errors.  Diskpart only shows the NTFS partition - not that it would probably make much difference if it could see the other.

I even ran Supergrub, but just ended up with a situation where the computer said it didn't have the required kernel files - same as if I booted directly.

I think I'll have to run the recovery and then try the registry copy.  That's something I hadn't heard of before.

Thanks
Mike

---

### Post by caljohnsmith on 2008-10-27
> **5circles said:**
> Well, I think I'm at the end of the road for an easy recovery - unless anyone has any other ideas.

I copied all the files over and then ran the recovery console.  It won't run chkdsk or fixmbr - says the disk has unrecoverable errors.  Diskpart only shows the NTFS partition - not that it would probably make much difference if it could see the other.

I even ran Supergrub, but just ended up with a situation where the computer said it didn't have the required kernel files - same as if I booted directly.

I think I'll have to run the recovery and then try the registry copy.  That's something I hadn't heard of before.

Thanks
Mike
In your first post you said you could run fixmbr fine, but now it doesn't work? When you boot your Windows Install CD, does it find your Windows on that HDD? 

You didn't mention what method you are using, but if you are just going to copy all the files over, then you could first reformat that HDD, create a new NTFS partition, copy the files over, use "fixboot" to install the Windows boot sector to the partition, and maybe that would work. In other words, if your files are OK but chkdsk is just choking on a bunch of file system errors, it might be enough to start with a clean NTFS partition. Or instead of reformatting, if you delete the Windows partition and create it anew, that might be enough before doing the rest. I don't know for sure if it would work, but it might be worth a try before a total reinstallation.

---

