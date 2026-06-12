---
title: "[SOLVED] Recovering directory from ext3 drive."
date: 2008-11-01
forum: General Help
---

### Post by jmail524 on 2008-11-01
Hi,

I hope that the gurus of data recovery might be able to help me on this one.

I have a 500GB hard drive that is formatted as ext3.  This drive is not my boot drive, just a drive that hold data I work on.  All of a sudden it started giving me mounting errors (bad superblock / dbus error).  The errors stopped but now the drive looks empty, no files are shown (even when I enable hidden file viewing).  How ever, the amount of free space reported is exactly (or at least very close) to how much free space the drive had before the files disappeared.

I downloaded and ran "testdisk".  It sees the partition and the files on the drive organized exactly how I remember them to be.  I have also tried "photorec", but it only seems to recover the deleted files from that drive.

I have not run "fsck" on the drive because I didn't want to make thing any worse that they already are. (Had a couple bad experiences with Window "scandisk" and complete loss of data on NTFS drives).

The hard drive may be going bad.  The manufacturer's diagnostic seems to lock-up on that drive only.

To me the problem is very unnerving because I don't wish to lose any data. (My backups I made have also gone bad.)  However, the fact that the correct amount of free space is being reported and also that "testdisk" sees the files (at lease the directory entries) and shows them in the correct order that I remember leads me to believe that the problem isn't all that serious .  I just don't know what to do next.  Any help is greatly appreciated.

Thanks.
Brian

---

### Post by ABCC on 2008-11-01
My first step would be to get a disk the same size or bigger and make a copy of the suspect drive using dd. Next step would be to mount (a copy of) the disk image as a block device and see what can be recovered by following whichever online guide seemed approriate.

---

### Post by ABCC on 2008-11-01
And if that fails you can try [http://www.garloff.de/kurt/linux/ddrescue/]("http://www.garloff.de/kurt/linux/ddrescue/"). For a guide see [http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html]("http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html")

---

### Post by jmail524 on 2008-11-08
Thanks ABCC for the links and advice.  It was very helpful in finding a resolution to my problem.

I attempted the 'dd_rescue' solution, but it did not work work for me.  I let 'dd_rescue' run for 3 days then I aborted the program.  It seemed to make fast progress through 80% of the drive then it seems to have stalled.  (I thought this was odd because the errors seem to be in the first 10% of the drive.)

The solution I have outlined below, in case it helps anyone else, seem to have recovered nearly all of my files.  (Hopefully it makes sense.)

Make sure the failed drive partition is not mounted.

I used the 'dd' command to make an image file of my failed hard drive partition (sda1) in a working partition on another hard drive (disk).  The flags 'noerror' cause the 'dd' command to continue copying even if a read error occurs and 'sync' pads the image file with spaces were the read error occured so that the image file is the exact same size as the source drive.
```
sudo dd if=/dev/sda1 of=/media/disk/image.img conv=noerror,sync
```
I then mounted the image file as loop device (loop0) using the loop setup command.
```
sudo losetup /dev/loop0 /media/disk/image.img
```
Next, I created a mounting point (/media/image).
```
sudo mkdir /media/image
```
Finally, I mounted the loop device (loop0) in the newly created mounting point (image).
```
sudo mount /dev/loop0 /media/image
```
When the drive was mounted, I was able to see nearly all of my files.  I was very lucky that I didn't lose anything of importance.

---

