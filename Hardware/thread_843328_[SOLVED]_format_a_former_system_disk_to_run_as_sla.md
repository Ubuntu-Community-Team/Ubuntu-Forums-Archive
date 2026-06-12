---
title: "[SOLVED] format a former system disk to run as slave."
date: 2008-06-28
forum: Hardware
---

### Post by Briped on 2008-06-28
Hello everybody,
Been there , done that, didn't succeed, so now I hope somebody in here can tell me how, or post a relevant link. I did search the forums, but didn't seem to find any relevant threads or posts.

I have with me a 40GB seagate, which used to run as a system disk (win -xp). Please help me kill it :)

According to Gparted it has 2 partitions:
/dev/sdc1, ntfs, /media/boot, 18,63 GB
/dev/sdc2, extended, subdivided into /dev/sdc5 (ntfs, /media/backup) 15,7 GB and /dev/sdc6 (FAT32 /media/recover) 2,93GB.

The HD is connected as an external drive via USB. My plans for it's future is to have it run on another dual boot xp/ubuntu 8.04 desktop as internal slave. Therefore I need to wipe it completely clean. I have tried doing this before on another HD, and as a result I have on my physical desktop next to me another 40GB HD that won't show up on Gparted - or anywhere else, for that matter. To avoid ending up with piles of unusable HDs on my desktop I would appreciate some advice concerning how to go about this. I prefer to keep the NTFS file system, as it needs to be readable from the xp partition.

Thanks so much,
Britta

---

### Post by ajgreeny on 2008-06-28
If you want to use the disk as a data disk, ie not with any applications on it, just documents, pictures etc etc, then it should be fine as ntfs.  Using gparted either on a live CD or using an installed gparted on your ubuntu system, delete the partitions currently on the disk and then simply make a new partition using the whole disk and format it as ntfs.  To do this you will need to make sure the disk is not mounted, or there could be trouble.

I can't imagine what the problem with the other disk that is not seen could be other than it being totally dead, not powered up, or something.  Is that disk seen if you run the live ubuntu CD on that machine and then use ```
sudo fdisk -l
``` in terminal?  If it isn't then it must be completely broken, I think.  There seems to be no other reason for that situation.  certainly there is no reason for gparted to stop a disk working completely, though if you have just wiped it and not made a new partition on it, it will not show up in nautilus or any other filemanager, and will be invisible except to system tools like gparted.

---

### Post by Briped on 2008-06-28
> **ajgreeny said:**
>  ... delete the partitions currently on the disk and then simply make a new partition using the whole disk and format it as ntfs.  To do this you will need to make sure the disk is not mounted, or there could be trouble.

So glad you mentioned it has to be unmounted. I had no idea. Is there any particular order I should delete the partitions in? Graphically Gparted shows two partitions inside one of the two major partitions. One FAT32 and one NTFS, should I just pick either, right click, delete and hold my fingers crossed?

> though if you have just wiped it and not made a new partition on it, it will not show up in nautilus or any other filemanager, and will be invisible except to system tools like gparted.

Hmmm, could be that's where I went wrong. I tampered with it before I turned ubuntu enthusiast, and used the appropriate windows facility. As far as I remember I simply deleted the partitions, and when I wanted to format, it couldn't be found again, which is why I worry if I'll make the same mistake with this one. It's not my gut feeling there's anything wrong with it. It does power up, and it does show under device manager in windows - where I can't 'get at it'. I did try to run Gparted as a live CD, but think the CD must have been corrupted in some way. I'll give it another go later.

Thanks,
Britta

---

### Post by Briped on 2008-06-29
I tried deleting the partitions as advised above, but I don't seem to have much luck with it.
What happens is that I unmount the partitions and right click for deletion one by one. The first two partitions (/dev/sdc1 and /dev/sdc6) show up in 'jobs pending'. Now I unmount /dev/sdc5, and immediately it gets marked by a warning triangle. I persist, right click - delete, and get 'unable to delete /dev/sdc5. Please unmount any partitions having a number higher than 5', but /dev/sdc6 is already unmounted and marked for deletion..:confused: Should I go ahead and click 'apply' to delete the first two partitions before deleting /dev/sdc5, or how do I solve this problem?

Thanks,
Britta

---

### Post by Briped on 2008-06-29
The key to solving the issue was closing Gparted, unmounting the 3 partitions in the file manager, reopening Gparted, marking everything for deletion, deleting it and then reformatting in NTFS.

---

