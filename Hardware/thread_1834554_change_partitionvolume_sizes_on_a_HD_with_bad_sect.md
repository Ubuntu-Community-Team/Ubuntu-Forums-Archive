---
title: "change partition/volume sizes on a HD with bad sectors?"
date: 2011-08-27
forum: Hardware
---

### Post by NattyNoobCake on 2011-08-27
i'm dual booting windows and ubuntu currently and i want to shrink the volume size of the windows partition. Using windows 7, it lets me actually shrink the volume but only by like 400 mb. How can i change the volume size of the windows partition?

---

### Post by jerrrys on 2011-08-28
there are other partition utilities available, but is recommended that a windows utility be used.  at times linux partitioner will work, but will also fail at times.  i would try to find your answer in a windows forum and then come on back with any linux questions.

---

### Post by dabl on 2011-08-28
If the "bad sectors" thing is for real, you need to back up any and all important data as soon as possible, and then get a replacement hard drive.

---

### Post by agillator on 2011-08-28
First backup anything you wouldn't want to lose, regardless of what you do or how you do it.  Then, make sure you have everything backed up you can't replace.  Next, backup the stuff you forgot to backup.  Did I mention back everything up?  Then, to be on the safe side, get the instructions for reinstalling grub (or grub2, whichever you are using). [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) is the best I have found for my purposes. You may or may not have to reinstall. Finding out the hard way without having instructions is the pits! That is the voice of experience speaking.  Finally, I have had good success with gparted. Of course the partitions being resized cannot be mounted so I have found the best way is to load the Ubuntu live CD to 'try' Ubuntu and run gparted from the system menu there. Be patient. It can take some time. I have resized a windows partition a couple of times without problem. Doesn't guarantee your success, of course. It isn't as bad as it sounds. Once you do it successfully you will probably not be afraid to do it more often to adapt to current needs as they change, which may be dangerous.

---

