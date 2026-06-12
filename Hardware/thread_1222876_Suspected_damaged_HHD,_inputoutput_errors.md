---
title: "Suspected damaged HHD, input/output errors"
date: 2009-07-25
forum: Hardware
---

### Post by frank26080115 on 2009-07-25
Here's the story. A few days ago, Vista decided not to boot up (stuck on scrolling green bar, or stuck on crcdisk.sys on safe mode boot). I decided to use my Ubuntu partition to back up my files from the NTFS partition on my laptop's HDD to an external HDD. During the back up process, I noticed some files would cause Ubuntu to feeze up for a minute, and then tell me the file couldn't be copied because of an input/output error. I tried these specific files again and they gave the same error.

I boot into my Vista installation disk and ran the startup repair, which allowed Vista to boot. In Vista, if I tried accessing the same files, Vista would also freeze, but won't show an error and I would be forced to reboot my computer.

One of the file in question is a zip file with three text documents inside. I am actually able to extract and view two of the text files in both OS, but the third would crash Vista and cause an input/output error in linux. If I tried to "cat filename" in console, the file would partially print and then suddenly, the input/output error would appear.

I ran chkdsk, it would get to stage 4/5 (verifying file) without a problem but freeze during stage 4 at 19% after 10 hours of waiting.

Vista will still run, but I feel like it's walking in a minefield, if anything tries to access a file that happens to be damaged, the system would freeze. Although right now I can still get work done and surf the internet for hours.

What do you think the problem is? I suspect a damaged HHD but the computer still runs fine.

EDIT:

I am trying to run NTFSCLONE but I can't

frank@frank-ubuntu:~$ sudo ntfsclone --rescue --force --save-image --overwrite /media/USB_HDD/NTFS_img/ntfs_img.diskimage /dev/sda3
ntfsclone v2.0.0 (libntfs 10:0:0)
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 303858446336 bytes (303859 MB)
Current device size: 303858450432 bytes (303859 MB)
Scanning volume ...
ERROR: Cluster 2709 referenced twice!
You didn't shutdown your Windowsproperly?

:-(

---

