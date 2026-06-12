---
title: "NTFS mount issues on several drives after bootup"
date: 2009-02-21
forum: Hardware
---

### Post by MedianMajik on 2009-02-21
I've noticed that after I startup my computer Ubuntu displays the internal and external slaves hard drives as "greyed out" until I open them.  If I open them all up and wait a second for all of the folders, etc to appear I'm good to go.  This is a ridiculous hassle that I'm sure I can avoid.  I don't have the liberty of formatting all of the drives to ext3 (I would if I could).  My problem lies in auto-running torrenting, which will try to re-download files it can't locate.  I'm sure I could run a script to do this for me, but I hope there is a way I can allow Ubuntu to verify these drives as soon it boot up.

Also, I have a 750gb external in two partitions (100gb ext3 and 650ish NTFS).  I was wondering if it is possible to format the 100gb as NTFS and migrate the two partitions together without losing my other 650gb of data already on the drive.

Thanks for the help!:KS

---

### Post by kestrel1 on 2009-02-21
You need to auto mount your drives. You need to edit your fstab file to do this. This may help: [http://www.dedoimedo.com/computers/automount_ntfs.html](http://www.dedoimedo.com/computers/automount_ntfs.html)
With your external drive, I would use gparted & delete the 100gb partition & then resize the other partition to use the unpartitioned space.

---

### Post by MedianMajik on 2009-02-21
> **kestrel1 said:**
> You need to auto mount your drives. You need to edit your fstab file to do this. This may help: [http://www.dedoimedo.com/computers/automount_ntfs.html](http://www.dedoimedo.com/computers/automount_ntfs.html)
With your external drive, I would use gparted & delete the 100gb partition & then resize the other partition to use the unpartitioned space.Thanks for the link.  Would resizing the remaining partition cause it to format/lose data?

---

### Post by kestrel1 on 2009-02-21
No, you shouldn't have any loss of data, but of course this cannot be gauranteed. I personally have never had a problem doing this. If the data is real important, I would recommend backing it up first. Once the resize has completed you could then delete the backed up data. I have never bothered to back up & not had a problem.

---

