---
title: "Partition questions for EEE 1000HA"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by arinlares on 2009-09-02
I just got my Asus EEE 1000HA from Newegg.com today, and hope to set up a windows/UNR dual boot.  I was looking in My Computer in XP, and I noticed that I have two partitions, C and D in Windows, that combined take up the whole harddrive.  My question is about when I set up the partitions in the Ubuntu install process, and what I should do as far as adjusting/removing/formatting partitions.

C: is 82.2GB, and D: is 61.2GB.  D, which I assume is a backup partition, has no files that I can see, but supposedly has 66.4MB on it.  So, is this the backup partition?  Can this be resized safely, and how small can it go safely?  I haven't gotten around to booting into Ubuntu on a USB yet, because I noticed this issue first.

---

### Post by modmadmike on 2009-09-02
> **arinlares said:**
> I just got my Asus EEE 1000HA from Newegg.com today, and hope to set up a windows/UNR dual boot.  I was looking in My Computer in XP, and I noticed that I have two partitions, C and D in Windows, that combined take up the whole harddrive.  My question is about when I set up the partitions in the Ubuntu install process, and what I should do as far as adjusting/removing/formatting partitions.

C: is 82.2GB, and D: is 61.2GB.  D, which I assume is a backup partition, has no files that I can see, but supposedly has 66.4MB on it.  So, is this the backup partition?  Can this be resized safely, and how small can it go safely?  I haven't gotten around to booting into Ubuntu on a USB yet, because I noticed this issue first.

Its a backup partition, but in place of the larger partition I would put a partition for /home and the other being / so if you accidentally mess up your install all of your user data is still there.

EDIT: nvm i misread your post, anyways that partition will not be touched by windows by default so therefore you can get rid of it and windows will be fine.

---

### Post by arinlares on 2009-09-02
Fixing this post...  It can also be resized safely, right?

---

### Post by modmadmike on 2009-09-02
> **arinlares said:**
> Fixing this post...  It can also be resized safely, right?

yes but resize it from windows not linux

---

### Post by arinlares on 2009-09-02
How can I do this?  And why not use GParted?  Sorry, I've got a lot to learn.

---

### Post by modmadmike on 2009-09-02
> **arinlares said:**
> How can I do this?  And why not use GParted?  Sorry, I've got a lot to learn.

if you use gparted many problems may occur (with windows that is) but in windows it should be fine 

how to do it in Windows XP: [http://support.microsoft.com/kb/309000]("http://support.microsoft.com/kb/309000")

Vista:
[http://windowshelp.microsoft.com/Windows/en-US/help/d9a4d35e-efdf-406c-a049-0860180129a71033.mspx]("http://windowshelp.microsoft.com/Windows/en-US/help/d9a4d35e-efdf-406c-a049-0860180129a71033.mspx")

---

### Post by arinlares on 2009-09-02
I don't have any unallocated space on the HD.  I have a screenshot of the disk manager showing the partitions,and the E drive which is my USB storage drive.

[IMG]http://i251.photobucket.com/albums/gg290/arinlares/hdprofilecompmngr.png[/IMG]

---

### Post by modmadmike on 2009-09-02
> **arinlares said:**
> I don't have any unallocated space on the HD.  I have a screenshot of the disk manager showing the partitions,and the E drive which is my USB storage drive.

[IMG]http://i251.photobucket.com/albums/gg290/arinlares/hdprofilecompmngr.png[/IMG]

you should be able to resize D from here

Also you can try Gparted because D isn't used as a system partiton

---

### Post by arinlares on 2009-09-02
A bit of research shows that it's possible to resize D: in Vista, but you need third party software for XP, which I have.  Thanks for your help, you helped me get where I needed to go.  I'll come back to this thread if I have a question about this issue again.

---

