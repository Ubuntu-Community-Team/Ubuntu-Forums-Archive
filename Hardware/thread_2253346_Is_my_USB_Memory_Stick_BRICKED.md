---
title: "Is my USB Memory Stick BRICKED"
date: 2014-11-19
forum: Hardware
---

### Post by Dyffo on 2014-11-19
This issue, although not important has become a challenge for me to resolve.

My computer is Dual Boot with Vista and Ubuntu.
I have a USB memory stick which is identified and seen by both systems, the contents of the drive open up, however I cannot write or delete any files off the stick. Properties show that the disk is working normally, and also that it is full, which it is not.
I have tried every way to reformat, but nothing changes.
In Windows Disk Mgt,SD Format, HP Usb Disk and more, in Ubuntu I have tried GParted, Disk util and more.
Is my stick bricked ?? or is there a solution ??

---

### Post by stalkingwolf on 2014-11-19
I would download Hirens utility disk and run the HDD regenerator tool on it.  might just have a bad sector that can be repaired.

---

### Post by yancek on 2014-11-19
If you can see it from both vista and Ubuntu then you must have a windows filesystem on it, FAT32, ntfs?  What's on it,  just data you have copied there?  How do you access it from Ubuntu?  Does it show up under /media/username?  If it is FAT32 you should have r/w access.  Could be a lot of things, like has it worked before?  You are a little short on details.

---

### Post by oldfred on 2014-11-19
If a Windows format or file system, the Linux driver will not let you write if chkdsk flag is set to prevent damage that writing may cause that chkdsk then could not fix.

Have you tried chkdsk? That can only be run from Windows.

---

### Post by Dyffo on 2014-11-20
Thanks guys for your comments. I have tried every solution possible - and have been advised that the device is "busted".

---

### Post by sudodus on 2014-11-20
Often when pendrives are failing, the first symptom is that they are read-only.

---

### Post by Dyffo on 2014-11-20
That's exactly what happened - became read only, no matter what I did, I could not remove this to make a read write.

---

