---
title: "unable to install ubuntu on a ext hard drive,"
date: 2011-08-02
forum: Hardware
---

### Post by thegt1 on 2011-08-02
hi everyone, i just got an external hard drive to install ubuntu on but it doesn't recognise it, first i tried the latest ubuntu distro and than i tried kubuntu, both couldn't recognise the drive.
I'm booting both distro from usb flash drive and when launching gparted and disk utility neither can report a size. Btw i format the drive using fat 32, right now i'm running out of ideas, any help will be greatly appreciated, ANY HELP, thanks in advance.

---

### Post by oldfred on 2011-08-02
Ubuntu does not install to a FAT32 partition (except as an installer). It requires its own formats ext3 or ext4 (or many others) that support ownership & permissions which windows formats do not support.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by thegt1 on 2011-08-02
thanks oldfred for the assistance, i went ahead and use " EaseUs" program within windows and reformat it using ext3. Put it back in the laptop and still not detecting the external hd. Any other ideas ( i did tried both gparted and disk utility, and again not detection of this drive) fdisk -l didn't work either

---

### Post by thegt1 on 2011-08-02
Found part of the problem, i tried an old 2,5 hd and plug it into ubuntu and recognise that one right away (even with ntfs ) at least i can have a beer now, time to return this one, thanks again.

---

