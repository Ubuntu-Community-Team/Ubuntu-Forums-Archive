---
title: "External hard drive for dual boot windows + ubuntu, how should I partition?"
date: 2011-05-11
forum: Hardware
---

### Post by mavve on 2011-05-11
I have bought an external hard drive (USB connected) to use for extra storage on my dual boot Windows and ubuntu machine. The disk comes preformatted with NTFS. 

I want to be able to use the disk for extra storage, so as a ubuntu/linux newbie I would be happy for some feedback on the following choices, or suggestions of alternatives.

[LIST=1]
[*]1. Leave the disk as is. (what would this imply for use in ubuntu?)

[*]2. Divide the disk into two partitions. (What file system should I use for the "ubuntu-partition", and what software should I use to do this?)
[/LIST]

I am new to ubuntu and all things linux, so please be gentle and descriptive with your feedback! Thank you!

---

### Post by grahammechanical on 2011-05-11
It is my understanding that if you want to access files on this external drive from both Windows and Ubuntu then you should leave it as NTFS. This is because Ubuntu can read NTFS drives/partitions but Microsoft Windows cannot read the ext3 or ext4 or other formats used by a Linux operating system.

Could you not just treat the drive as another kind of folder? 

Regards.

---

### Post by mavve on 2011-05-11
Yes, I think I will do just that, leave the disk as is since it will allow me to access the files from both OS. 

I was lead to believe that there was some kind of loss in performance involved in using NTFS while in Ubuntu, It seems, though, that this is not the case, or at least the loss in performance is not great enough to overshadow the inconvenience. 

Thanks for the help!

---

