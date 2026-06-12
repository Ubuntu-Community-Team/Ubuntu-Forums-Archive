---
title: "SSD and TRIM (discard)"
date: 2012-02-15
forum: Hardware
---

### Post by jeremija on 2012-02-15
I realize that I must add the discard option to the ext4 partition on the SSD disk /etc/fstab file to make it use TRIM. 

However, I tend to dual boot with Windows and use a partition for multimedia which is shared between the two operating systems for. 

Because I'm on laptop an I have only one disk to use, I'd like to know if the 'discard' option is only for ext4 or it works on other partitions like NTFS or FAT32? If it does not, is there any other way to enable TRIM on non-ext4 partitions?

---

### Post by oldfred on 2012-02-15
It is my understanding that is is not required anymore.

Not required with newer kernels
[http://disktrim.sourceforge.net/](http://disktrim.sourceforge.net/)

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by jeremija on 2012-02-15
oldfred, thank you for you reply!

You mean that the 'discard' option is not required anymore? If so, could you please explain, because everywhere I read about TRIM support it was said that the discard parameter should be used (and optionally noatime).

But my question was is it possible to enable TRIM support on other types of partitions (NTFS, FAT32, any which is readable under both Ubuntu and Win7). Do you think that the only solution for those partitions is to use DiskTRIM?

---

### Post by oldfred on 2012-02-15
I may have confused it. The diskTrim was only required with old kernels. You can set noatime & diskcard as a boot parameter. You do need ACHI mode in BIOS. See Arch site linked above for best info.

Not sure about NTFS partitions.

---

### Post by jeremija on 2012-02-16
Thanks, now I understand what you wanted to say!

So the question is still open: how to enable trim when mounting a ntfs partition? Does the discard option work?

I checked this page: [https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking) and I can see that TRIM is working on my ext4 partition, but dd command won't start when I start in folder on ntfs partition.

---

