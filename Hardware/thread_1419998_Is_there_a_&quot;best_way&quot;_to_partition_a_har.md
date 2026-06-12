---
title: "Is there a &quot;best way&quot; to partition a hard drive?"
date: 2010-03-02
forum: Hardware
---

### Post by GARoss on 2010-03-02
I have Ubuntu 9.10 installed on a 300Gb HDD & would like to partition it from 100% ext4 to 30% & the remaining 70% to NTFS. 

1st can this be done? 
Can I use Gparted software from the desktop or is Gparted live CD advised? 
Is other software advised over Gparted?

All suggestions are appreciated.

---

### Post by oldfred on 2010-03-02
Yes you can do this if your ext4 partition is not using more than about 25% of the space. You have to leave some space for growth and use.

If this is a separate drive and not mounted or umounted you can do it from your install. It is usually best to do from a liveCD.

Make sure you have backed up any important data, just incase.

You may have to download ntfstools(?) for gparted to format it. Some versions include that, others do not. I like to download the gparted liveCD as it is the newest and is a smaller download ~100MB.

---

### Post by GARoss on 2010-03-02
Thanks. I planned on formatting 210Gb of the 279Gb (actually reads 279Gb but sold as 300Gb) to NTFS.
I have Ubuntu installed on this drive. It is a new install so if something happens not too much harm is done. 
On a different HDD is XP & another that is all NTFS (3 HDDs total).
I have installed Gparted & also a number of required support files. I'll check for ntfstools. Also, I have downloaded the Gparted.iso & could use that if it is advised.

---

### Post by GARoss on 2010-03-02
I used the Live CD & resized ext4 from 279GB to 100Gb & converted the remaining unused 200Gb to NTFS. This software is very fast! I tested it in WinXP & it works great. Ubuntu also recognizes everything okay, too, & I could reads a folder I recorded in it while I was in XP.

One question I have is Gparted has a yellow triangle with an exclamation point inside it next to the new NTFS section. All seems to work okay. Just wondering what that means.:?

---

### Post by oldfred on 2010-03-03
On my portable I also have a small space that did not get included in my partitions and that has the yellow triangle. When I click on it and look under properties it tells me more about it. In my case is says it is not formated and not set up correctly which it is not.

---

### Post by amrypma on 2010-03-03
I usually have my linux installed on 2 partitions. 
one for the root file system about 20 G
one for /home.

Optional I have a /incoming partition where I dump just about everything I download and have a script trash old files in case I need more space.

---

