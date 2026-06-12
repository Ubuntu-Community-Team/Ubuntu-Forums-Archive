---
title: "hard disk not detecting"
date: 2017-01-12
forum: Hardware
---

### Post by dcompany on 2017-01-12
My old windows laptop internal drive was crashed. I took that hard drive outside and connected that to IDE/SATA Adaptor cable. In device manager it shows as 2TB hard drive, even though its actual size is 320GB. This must be due to logical error . Am unable to access any files in that.
I tried many softwares found over net to fix bad sector, nothing worked and also took started running for days so I had canceled the operation.
Any suggestion , if I can fix bad sectors of Hard disk using Linux ?

---

### Post by osharuk on 2017-01-12
NOTE...my first post so don't shoot me down!
NOTE2: I accept no responsibility for any data loss in any way shape or form. Use at your own risk.

My first questions would be how valuable is your data?
Secondly, what are you trying to achieve? Are you trying to recover the files from the HDD or boot into windows again once you "fix" the bad sectors so you can recover the files in windows?

Having bad sectors means that the drive is on its way out and needs replacing ASAP. I suggest you attempt to recover the data but note that the more you use the drive (attempting to "recover it") the more potential damage it could do to your disk and the more data you could loose. If you have very valuable data STOP! There are companies that can recover the data but it can be expensive.

If you just want to do the best you can with recovery, there are a few options.
1. use a Linux live CD to boot up, mount the failing drive AND an additional drive to accept the data and copy from one to another.
2. use GRC Spinrite to attempt to recover the sectors. I've heard many good things about this program but never used it myself. (PS, its not free...but not expensive either)

If you go with option 1, there are many forum posts on how to mount a drive in linux, but I would suggest you format the donor drive with fat32 so that Windows will be able to read the disk later:

fdisk -l | grep "dev"
This will print out what disks and partitions there are available to the system (/dev/sdb for example would be device/SATA Device B) whereas (/dev/sdb1 would be the 1st partition on that drive)

lets assume that you get something like:
"/dev/sdb1" from the above command for the failing disk, and
"/deb/sdc1" for the donor disk.

Make 2 directories to mount the drives:
mkdir /mnt/faileddrive
mkdir /mnt/donordrive

now use the mount command to mount drives to the filesystem (you can try auto and ntfs...)
mount -t ntfs /dev/sdb1 /mnt/faileddrive
mount -t auto /dev/sdc1 /mnt/donordrive

Hopefully both drives will be mounted and you can now try to copy your files over from one drive to another with the "cp" command.
cp /mnt/faileddrive/[PATH TO FOLDER YOU WANT TO BACKUP] /mnt/donordrive/

Good luck and maybe someone from the forum can eyeball my response for completeness and accuracy and for any other suggestions.

:)

---

