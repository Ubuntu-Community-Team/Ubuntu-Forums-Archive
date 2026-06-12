---
title: "Laptop running windows / pc Ubuntu - 1TB drive wd mybook mounting problem"
date: 2010-05-04
forum: Hardware
---

### Post by OCN on 2010-05-04
I felt this is the right forum to post this, hardware problem being 1b external hdd / laptop eh

I have been using my WD External drive/mybook as they call it with Ubuntu, until now recently connected it to my laptop running windows vista, I know it sucks but I just got this laptop and using it instead of my tower to save power and just run the laptop 24x7 pretty much and the tower when I need it and during the day I keep it on but anyway's. I copied a lot of files over to the external drive, disconnected it and pluged it back over to my laptop running windows and none of the files were shown, the files I just copied but the other stuff is still on it. 

I get this message when reconnecting it to Ubuntu when trying to use it. 

> Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.Have I damaged the drive, I hope not and hope to fix this problem to run on both OS.

Have I damaged the drive, I hope not and hope to fix this problem to run on both OS.

I have been using Ubuntu for about 6 months but still feel like a noobie, and a problem like this, I feel lost.

any help to fix this is much appreciated.

---

### Post by Sven6210 on 2010-05-17
I have the same 1 TB WD MyBook which I operate under an EeeBox B202 in dual boot system with Windows XP and Ubuntu 10.04, Acyually I hardly use Windows XP, only in the beginning I was sometimes switching back when I wanted to do something that I did not manage to work with Ubuntu by then. Right now everything works quite well with Ubuntu.

I never have had the problem you mention. But are you sure your WD MyBook is formatted with NTFS? Mine is formatted with VFAT respectively FAT32.

In order to find out how the device is formatted just enter:

   sudo fdisk &#8211;l
  
I can manually mount it with

sudo mount /dev/ sdb1 /media/MyBook/ -t vfat -o iocharset=utf8,umask=000

 In order to be able to use the above command you need to make sure that the directory "/media/MyBook" exists.

Good luck

Sven

---

