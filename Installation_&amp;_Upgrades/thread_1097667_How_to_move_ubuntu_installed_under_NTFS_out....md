---
title: "How to move ubuntu installed under NTFS out..."
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Sorrakritch on 2009-03-16
I've tried Kubuntu by installed it as an application in Windows System under a separated NTFS Partition.

After testing for a while, I 've loaded a lot of things into it and quite love it so much.
So, now I want to move it out to it's own partition.

I'm just thinking about making a clone image and restore it to another partition.
Is it possible to do so? How?

Please advise, thanks
SRK

---

### Post by theozzlives on 2009-03-16
> **Sorrakritch said:**
> I've tried Kubuntu by installed it as an application in Windows System under a separated NTFS Partition.

After testing for a while, I 've loaded a lot of things into it and quite love it so much.
So, now I want to move it out to it's own partition.

I'm just thinking about making a clone image and restore it to another partition.
Is it possible to do so? How?

Please advise, thanks
SRK

Seems plausible with clonezilla, you'll probably have to make the partition before doing it. You'll definitely  need to install GRUB.

---

### Post by Sorrakritch on 2009-03-16
Thank you so much, but...

Maybe I'm still not familiar with unix, the process was failed -_-!

I've tried to use the latest Clonezilla Boot CD with almost default options:

1. Creation of image was successful. But I think that it made a backup of entire NTFS partition instead of just a virtual disk under "ubuntu" folder.

**So is there any specific instruction to make a backup image of the content inside the file root.disk and swap.disk?**

2. Restoration was failed immediately even I've created the ext3 and swap partitions ready before doing it.

I have totally no idea about this...

Could you please give me more detail?
Thanks in advanced. :-)
SRK

---

### Post by Mark Phelps on 2009-03-17
To move a Wubi installation to its own partion, see the following:

[http://ubuntuforums.org/showthread.php?t=438591]("http://ubuntuforums.org/showthread.php?t=438591")

---

### Post by Sorrakritch on 2009-03-18
Thanks guys,

It closer match my situation, I'll try it out... 
:-)

SRK

---

