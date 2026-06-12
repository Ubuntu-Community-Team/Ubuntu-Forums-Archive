---
title: "External Hard Drive - ext3? ntfs? fat32?"
date: 2009-01-22
forum: Hardware
---

### Post by slapstik007 on 2009-01-22
I recently started running ubuntu on my Dell Vostro 1500 laptop. I recently purchased a new 1TB hard drive to store all music, movie and other media. I am wanting this drive to be very compatible with my friends Windows XP machine as well as my Ubuntu machine. What file system would be the smartest to go with. I am worried about using FAT32 because of the Hi-definition content I will have and limiting my file size to 4 gigs. How compatible would ext2 or ext3 be with Windows? Would I really have to worry about using NTFS and its compatibility with ubuntu?

---

### Post by Crafty Kisses on 2009-01-22
To be honest, you should probably format it as NTFS, if you want it to work with both Windows and Linux, that's just my opinion though.

---

### Post by Yashiro on 2009-01-23
Split it into 3?

```

[FAT32 for small files/PS3,Xbox]	100
[NTFS]					600
[EXT3 protected from Windows snoopers]	300

```

---

### Post by bgerlich on 2009-01-23
Install Ubuntu on it :). Seriously, it will take only few gigs and you will have your system to work with your files. If, for some reason you'll need access the data from Windows, create a small, 20 meg fat partition with the ext2/3 driver for Windows and Mac, for that occasion.

---

### Post by pmooney78 on 2009-01-23
Where can I find the ext2/ext3 drivers for Windows?

---

### Post by slapstik007 on 2009-01-23
Thanks for the suggestions. I think that I will format it into 2 partitions. One small one that is NTFS that will contain the [drivers for windows to access ext2]("http://sourceforge.net/projects/ext2fsd"). The remainder of the drive will be formatted ext3.

---

### Post by JuanC on 2009-01-23
> **pmooney78 said:**
> Where can I find the ext2/ext3 drivers for Windows?

You could try Virtual Volumes : 
[http://www.chrysocome.net/virtualvolumes](http://www.chrysocome.net/virtualvolumes)

---

