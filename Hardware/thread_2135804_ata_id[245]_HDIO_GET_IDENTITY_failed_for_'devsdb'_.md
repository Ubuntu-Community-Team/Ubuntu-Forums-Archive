---
title: "ata_id[245]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument"
date: 2013-04-15
forum: Hardware
---

### Post by urville on 2013-04-15
Exact story:
Computer has two onboard 320 gig sata drives and one 1tb Sata on USB via a kingwin adapter.
I am coming over from having Win home Server. The 1TB drive carries all my media and documents. 
I disconnect 1 tb on USB, it is still NTFS. 
I use the xubuntu 12.10 live cd, open gparted, and delete and reformat both 320 gig onboard drives to single ext4 partitions.
I start the xubuntu install and allow it to do as it likes with the drives.
it sets the main drive up as sda1 - root and sda2 swap
other drive is sdb1
Later, after install and a few apps installed I intend to try both XBMC and Serviio for both HTPC and stream to 360 use and see which i like. 
No errors so far. 
I install XBMC, shutdown. Plug in Kingwin USB/SATA device. Start machine. Get ata_id[245]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument, but everything still started up. Icons appear for all drives on desktop.
Enter XBMC, to add video from NTFS. Initial testing. Once I pick a serving software I will transfer off 1 tb, format ext4, and transfer back.
Cannot find mounts. At first I think its XBMC. Reboot. See error again.
get in, run ls -l /dev/disk/by-id and I can see the USB has taken sdb and it has made the sata sdc
reboot. error.
look in media, nothing. Click on the desktop icon for the non root 320 gig and it comes up and I had the file window open for media and I see it propagate, but only after I clicked on it. Click on the USB/SATA drive and it gives mount error. I hot unplug and plug and now it works too and propagates in media. 
Research.
I setup fstab to make mounts persistent. I use example of sda1. i clone sda1 and notate the fstab.

SDA1 is: > UUID=blah blah / errors=remount -ro 0 1 (I may have the 1 and zero switxhed)

So I make the sdb:
> UUID for the extra 320 gig /media/name1 errors=remount -ro 0 1

Then I make the USB:
> UUID for it /media/name2 errors=remount -ro 0 1

research. oh crap i have to backup errors=remount -ro in mtab
clone the mtab info but appropriate for each drive
Original:
> /dev/sda1 / ext4 errors=remount -ro 0 0

added:
> /dev/sdb1 /media/name1 ext4 errors=remount -ro 0 0
/dev/sdc1 /media/name2 ntfs errors=remount -ro  0 0

reboot
Still get ata_id[245]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
machine boots, drives are mounted in media, but desktop icons no longer appear.

How do i fix the actual error issue though and do things look... right?

---

### Post by urville on 2013-04-17
bump?

---

