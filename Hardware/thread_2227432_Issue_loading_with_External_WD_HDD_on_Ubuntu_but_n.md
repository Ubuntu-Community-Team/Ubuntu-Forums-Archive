---
title: "Issue loading with External WD HDD on Ubuntu but not Windows 7"
date: 2014-06-02
forum: Hardware
---

### Post by Durabys on 2014-06-02
Hi everyone.
Little problem here. I have my Xubuntu and dad's Ubuntu machine telling me in a really big warning window way that the MBR on our 2TB Western Digital wdbaau0020hbk-01 is either A) corrupted by virus, B) missing or C) partially deleted. The problem being? That I can run it completelly fine on Windows 7 and XP dual-boots. So. Is there somekind of "abilities expanding" software package for External HDD loading/reading/writing for Linux that puts it on par with Windows?

Note: I do not knwo if this is the right sub-forum for this. So I politely ask the Admins/Mods to move to the right place if it isn't.

My spec:

-Computer-
Processor        : 4x Intel(R) Core(TM) i3-2377M CPU @ 1.50GHz
Memory        : 8060MB (1245MB used)
Operating System        : Ubuntu 14.04 LTS
User Name        : durabys (TJ)
Date/Time        : Út 3. &#269;erven 2014, 07:39:17 CEST
-Display-
Resolution        : 1366x768 pixels
OpenGL Renderer        : Mesa DRI Intel(R) Sandybridge Mobile 
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel PCH
-Input Devices-
 Power Button
 Lid Switch
 Sleep Button
 Power Button
 AT Translated Set 2 keyboard
 Logitech USB Receiver
 Logitech USB Receiver
 ETPS/2 Elantech Touchpad
 Video Bus
 Acer WMI hotkeys
 Acer BMA150 accelerometer
 HD WebCam
 HDA Intel PCH HDMI/DP,pcm        : 3=
 HDA Intel PCH Headphone
-Printers (CUPS)-
HP-Deskjet-5520-series        : <i>Default</i>
-SCSI Disks-
ATA WDC WD5000LPVT-2
WD Ext HDD 1021

Text of the error message:

[QUOTE=Failed to mount "ZALOHA_WD_2"]Error mounting /dev/sdb1 at  /media/durabys/ZALOHA_WD_2: Command-line `mount -t "ntfs" -o  "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177"  "/dev/sdb1" "/media/durabys/ZALOHA_WD_2"' exited with non-zero exit  status 12: Failed to read last sector (3907027119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
[/QUOTE]

And the greatest mystery? This External disk works absolutelly fine on  any Windows machine I have gotten my hands on. Help please.

And this is the error message from a print-screen.

---

### Post by jeremy31 on 2014-06-02
Supposedly there is some sort of locking program on WD.  You need to unlock it in windows.  I might have to look at mine again even though I have others that work perfect- toshiba and seagate

---

### Post by Durabys on 2014-06-02
> **jeremy31 said:**
> Supposedly there is some sort of locking program on WD.  You need to unlock it in windows.  I might have to look at mine again even though I have others that work perfect- toshiba and seagate

A what again? :confused:

---

### Post by jeremy31 on 2014-06-02
> **Durabys said:**
> A what again? :confused: Are you using the 32 bit version?  I have a much older WD(250GB) external and it now seems to work on LM17- based on Ubuntu 14.04 but I could never access it on LM16(13.10 Ubuntu based?)

---

### Post by Durabys on 2014-06-03
I use 64-bit Xubuntu and 64-bit Ubuntu. Will specify in the first post in a moment.

---

### Post by Durabys on 2014-06-03
Reposting.

My spec:

-Computer-
Processor        : 4x Intel(R) Core(TM) i3-2377M CPU @ 1.50GHz
Memory        : 8060MB (1245MB used)
Operating System        : Ubuntu 14.04 LTS
User Name        : durabys (TJ)
Date/Time        : Út 3. &#269;erven 2014, 07:39:17 CEST
-Display-
Resolution        : 1366x768 pixels
OpenGL Renderer        : Mesa DRI Intel(R) Sandybridge Mobile 
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel PCH
-Input Devices-
 Power Button
 Lid Switch
 Sleep Button
 Power Button
 AT Translated Set 2 keyboard
 Logitech USB Receiver
 Logitech USB Receiver
 ETPS/2 Elantech Touchpad
 Video Bus
 Acer WMI hotkeys
 Acer BMA150 accelerometer
 HD WebCam
 HDA Intel PCH HDMI/DP,pcm        : 3=
 HDA Intel PCH Headphone
-Printers (CUPS)-
HP-Deskjet-5520-series        : <i>Default</i>
-SCSI Disks-
ATA WDC WD5000LPVT-2
WD Ext HDD 1021

And this is the error message print-screen.

---

### Post by Durabys on 2014-06-03
Text of the error message:

[QUOTE=Failed to mount "ZALOHA_WD_2"]Error mounting /dev/sdb1 at /media/durabys/ZALOHA_WD_2: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb1" "/media/durabys/ZALOHA_WD_2"' exited with non-zero exit status 12: Failed to read last sector (3907027119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
[/QUOTE]

And the greatest mystery? This External disk works absolutelly fine on any Windows machine I have gotten my hands on. Help please.

---

### Post by Durabys on 2014-06-03
Eh. Guys and gals? I would really like any help here because I do not have the money to buy a new 2TB Ext. HDD for the forseeable future.

---

### Post by PatrickD-52761 on 2014-06-14
Hi Durabys,

When you first plugged the drive in on Windows, did you run any of the Western Digital Utilities? If so, you probably locked (encrypted) the drive. You'll have to re-run the utilities to unlock it.

---

### Post by Durabys on 2014-06-14
> **PatrickD-52761 said:**
> Hi Durabys,

When you first plugged the drive in on Windows, did you run any of the Western Digital Utilities? If so, you probably locked (encrypted) the drive. You'll have to re-run the utilities to unlock it.

I think I see the problem now. Normally, when one of my other three WD ext. HDD's load up, after being conected to a Windows OS computer, a "second" imaginery drive shows up in My Computer, full with Setup.exe files, Diagnostic tools and drivers..but not in this ones case. I cannot find the Utilities I had run because they would be on the non-existent "Imaginery" drive located among CD/DVD-rom's. Something is damaged here.

---

### Post by Mark Phelps on 2014-06-14
> Something is damaged here. 

Actually ... probably NOT.  The WD external drives come with the ability to set a password -- but the app the allows you to ENTER the password runs ONLY in MS Windows.  Thus, onc e you set a password, you can't access the drive except through MS Windows.

Since it sounds like you ran the setup from a CD, you will probably have to use that same CD to remove the password.

The other alternative, if you have the disk space, is to copy the files and folders to an internal drive and then use a partitioning tool to erase and repartition the external WD drive.  This way, it won't be password protected anymore.

---

### Post by Durabys on 2014-06-15
> **Mark Phelps said:**
> Actually ... probably NOT.  The WD external drives come with the ability to set a password -- but the app the allows you to ENTER the password runs ONLY in MS Windows.  Thus, onc e you set a password, you can't access the drive except through MS Windows.

Since it sounds like you ran the setup from a CD, you will probably have to use that same CD to remove the password.

The other alternative, if you have the disk space, is to copy the files and folders to an internal drive and then use a partitioning tool to erase and repartition the external WD drive.  This way, it won't be password protected anymore.

What CD. There never was a CD with it. There is no tool here I can access and I do not remember putting in ANY password and I am writing this currently from Win7, where this HDD works fine and I do not have to put in any password when I connect it to the Win7 computer.

EDIT
I found one CD WD Smartware. Checking. Wait please.

---

### Post by Durabys on 2014-06-15
Nope. It is for the other 1TB WD ext. HDD.

---

### Post by J_Me on 2014-06-15
I had similar problems with a WD external hard drive, could only mount it in windows. The solution was to delete the last thing that I copied to the drive before the problem started.

---

