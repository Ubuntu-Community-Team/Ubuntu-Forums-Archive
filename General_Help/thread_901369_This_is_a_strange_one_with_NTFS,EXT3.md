---
title: "This is a strange one with NTFS,EXT3"
date: 2008-08-26
forum: General Help
---

### Post by chrislynch8 on 2008-08-26
Hi,

Ok so this is what happened. I was backing up my home folder which is over 100Gb in size. I backed it up on a USB Hard Drive that was formatted as NTFS. THe backup ran and I could see the compressed zip file on the USB Drive.

The next time I mounted the USB Drive I could see the backup and I could create any files or folders on the USB Drive. THe permissions where (500).

I mount using
```
sudo mount -o rw /dev/sdc1 /media/usbdrive
```

I figured it was an issue with NTFS and Ubuntu. To create another backup I formated the drive in Ubuntu to EXT3

```
mkfs.ext3 /dev/sdc1
```

When this finished I add full permission to create folders etc on the USB drive (755). I was able to create the folder for my backup and run the script. I just backed up the /etc/ folder to test and see that the backup wasn't going to disappear again.

When the script finished I went into the folder and my old backup of the home folder was there all 60Gb of it.

Has this happened anyone before - I couldn'y see it under NTFS and I formated the drive as EXT3 and it appeared then again......

---

