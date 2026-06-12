---
title: "Is it risky to deactivate disk checking at startup?"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by doncristobal on 2007-07-08
I have win/xubuntu7.04 dual boot. Following the explanations on [http://ubuntuforums.org/showthread.php?t=477592](http://ubuntuforums.org/showthread.php?t=477592) i deactivated the fsck for my fat32 data partition (on which both win and linux can access). I did this because the checking at _every_ startup was really annoying and - as far as i can judge - exaggerated. 

Question: Is this not risky? Should that file system not be checked from time to time? 

Thank you for any hint on where to find the answer to my question!

---

### Post by fredj on 2007-07-09
No its not that risky. You can always check this partition in Windows. I wonder why Ubuntu insists on 
checking it every time. I have dual boot Windows/Ubuntu systems with a Fat32 partition and Ubuntu never
shows any interest in the Fat32 partition.

---

