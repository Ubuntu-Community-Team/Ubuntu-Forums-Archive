---
title: "Ubuntu froze when transferring data from corrupted hdd, hdd now unclean"
date: 2013-11-15
forum: Hardware
---

### Post by hogswallop on 2013-11-15
Hi, I hope someone out there can help me as I am very new to anything Linux (all of 7 hours knowledge).

I am trying to retrieve data from my sister's old hard drive that is just about dead. I made a Live USB of ubuntu and had some success moving files from the corrupt hdd onto an external hdd. That is, until ubuntu froze while transferring. I did a hard shutdown (which I know now was a HUGE mistake) and now when I try to access the hdd I get this error message: 

'Unable to access "HDD"'
Error mounting /dev/sda2 at /media/ubuntu/Kathy: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda2" "/media/ubuntu/Kathy"' exited with non-zero exit status 13: The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
Failed to sync device /dev/sda2: Input/output error
Failed to close volume /dev/sda2: Input/output error

The hdd is then unmounted and I have to unplug it from power and plug it in again for it to be recognised in BIOS and ubuntu after rebooting. I am unable to find a way to perform a "clean shutdown" on this hdd as it is corrupt. I have tried all suggestions I have found related to System Restore and Startup Repair, including using the install disk to repair for Windows 7, but since the hdd is so far gone, nothing has been successful so far and shutting down using these recovery methods apparently doesn't equate to a clean shutdown.

Does anyone have any advice of what I could try next? Or any other programs I can use to retrieve the data? It is very important that I retrieve the data before flinging the hdd out the car window on a desolate highway.

Thanks in advance,
Suzanne

---

### Post by ajgreeny on 2013-11-15
You need a hard disk caddy and windows to plug it into.  Windows should mount the disk automatically and then allow you to remove it properly after which it should mount properly in Ubuntu.  You could also, of course, retrieve all those files that you need whilst still using this windows system rather than coming back to Ubuntu to do it.

---

### Post by hogswallop on 2013-11-15
I was trying to avoid getting a caddy. I have tried plugging it into my PC as a second hdd but it won't show. It only appears on my computer when it is the only hdd plugged in and use ubuntu.

I'll give the caddy a go and see what happens.

Thanks for your advice.

---

### Post by hogswallop on 2013-11-16
I bought a hard drive enclosure and mounted it. I mounted it in Windows but it would not eject. I tried accessing the drives both through windows and Ubuntu. In windows, it would not give access and wanted to format the drives but was not able to do so. I was not able to shut down windows when it was plugged in, it just froze on the shutdown screen. In ubuntu, it gave a similar "could not access" error due to being unclean. I think I have just about tried everything. I am desperate for ideas as my sister is unable to afford to send it for data recovery.

---

### Post by ajgreeny on 2013-11-16
The only other thing I can suggest is to try to force mount the disk in ubuntu with command ```
sudo mount -t ntfs-3g **/dev/sdb1** **/media/sdb1**/ -o force
``` though you may have to check the disk's /dev name first with ```
sudo fdisk -l
``` then change this command appropriately.  You will also have to make the folder /media/sdb1 (or whatever it now needs to be named) first.

---

### Post by efflandt on 2013-11-16
If it gets a drive letter in Windows did you try doing chkdsk /f on it from Windows? That is what gparted generally recommends when it sees a problem with an ntfs partition.

My boss' grandson had the hard drive fail on an old company laptop (WinXP refused to boot, even to safe mode, to protect data). At first I could copy part of it to USB drive using Ubuntu booted from USB. But copying locked up or stopped when it got to the bad part. I put it in an external USB enclosure and neither Windows nor Linux could mount it (I forget if sudo fdisk -l was still working). I let it sit for a couple of weeks and on a whim connected it to my Ubuntu desktop, and I was able to copy most of the user's directory from it except for a corrupted game directory. Sometimes you just get lucky.

The rest of the story: Replacement drive eventually refused to boot due bad sectors, chkdsk /f fixed everything except apparently unimportant dll, used Acronis to image it (file by file, not sector by sector) for warranty replacement drive (clonezilla would not work due to bad sectors). Then warranty drive refused to boot after viruses corrupted it, fixed with chkdsk /f and virus scan. Then the laptop screen got broken. Oh well, maybe he just wanted a newer laptop.

---

### Post by hogswallop on 2013-11-17
Updates!

Ajgreeny: As suggested, I popped in the sudo ffisk -l and got in return:
Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e4b3f38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    31266815    15633392    c  W95 FAT32 (LBA)

When I tried to force mount the drive, I got:
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

The drive is not showing up on the sidebar or in files.


Efflant: Yeah I tried chkdsk on Windows, but it would freeze the computer instantly when right clicking the drive. I was just about to give Clonezilla a go, but after reading your post, I might just try Acronis instead.

Thanks for your help guys!

---

