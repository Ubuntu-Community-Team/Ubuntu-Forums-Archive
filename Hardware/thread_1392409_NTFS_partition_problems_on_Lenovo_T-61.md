---
title: "NTFS partition problems on Lenovo T-61"
date: 2010-01-28
forum: Hardware
---

### Post by mataug on 2010-01-28
I am not sure if this is the correct sub-forum to ask about this, so moderators please move it to the correct sub-forum if I'm wrong

here goes my problem -
I have a dual boot system with Windows Vista and Ubuntu 8.04.3

I had two NTFS partitions on my windows and when I checked my laptop after more than 24 hours today, something's gone wrong with the second partition. Windows complains the drive needs to be formatted before use. I thought I should check it in linux and linux was also unable to mount that partition.

My knowledge wrt this is zilch but I had bookmarked a link for reference when I started using Ubuntu -
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

I have tried some of the stuff mentioned there -
[http://i789.photobucket.com/albums/yy172/mataug/screenshot-1.png](http://i789.photobucket.com/albums/yy172/mataug/screenshot-1.png)
[http://i789.photobucket.com/albums/yy172/mataug/screenshot-3.png](http://i789.photobucket.com/albums/yy172/mataug/screenshot-3.png)
[http://i789.photobucket.com/albums/yy172/mataug/screenshot-2.png](http://i789.photobucket.com/albums/yy172/mataug/screenshot-2.png)
[http://i789.photobucket.com/albums/yy172/mataug/windows_compmgmt_msc.jpg](http://i789.photobucket.com/albums/yy172/mataug/windows_compmgmt_msc.jpg)

/media/sda3 used to be the partition that I used to access whenever I had to use something from that partition

I tried some trial software in windows which does manage to show that the files are still there. I'm able to open files using that but then have to copy-paste to save them or decide to pay a $79 fee for the whole thing :o

I have been able to get a lot of help from these forums without even asking about it in the past just by searching but I couldn't find an answer about it this time. I would be grateful if somebody could provide any pointers to what might be the issue here.

I have a hunch that this is an issue of Windows screwing it up wrt hdd & cylinders but I was hoping if ubuntu could help determine & solve the exact issue since Windows isn't exactly helpful
+ I last took the backup only around Dec-end and some of my research code will be lost :-(

A friend has suggested using the dd command to make a bit-by-bit copy and then mount the image created. However I'm a bit unclear on that method.

Thanks

EDIT:
the post above says "today" because I had saved this post on Jan-21 but had been unable to post this on the Ubuntu forums via my net in India

also I don't remember seeing the *Partition so and so does not end on cylinder boundary* message before this problem came up

forgot to post about this information that I got from testdisk -
[http://i789.photobucket.com/albums/yy172/mataug/testdisk.jpg](http://i789.photobucket.com/albums/yy172/mataug/testdisk.jpg)

---

### Post by mataug on 2010-01-28
can this be moved to the General Help section ?

thanks

---

### Post by mataug on 2010-01-28
not sure how I change the thread status from ubuntu to solved
but I believe I have solved the problem by repairing the boot sector using TestDisk

thanks

---

