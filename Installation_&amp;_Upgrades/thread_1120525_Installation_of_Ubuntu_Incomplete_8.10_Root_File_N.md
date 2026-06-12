---
title: "Installation of Ubuntu Incomplete 8.10 Root File Not Defined"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by Max Avion on 2009-04-09
Hello,

I have installed Ubuntu 8.10 on my laptop along side windows and am trying to do the same on someone elses laptop. The only thing is that he has 4 partitions 2 which are local disks. I booted normally with Windows XP and began the installation of Ubunutu once installed I booted with Ubuntu from the OS choice menu but before showing the desktop a "verifying installation" screen poped up and showed the following message right at the end. 

&#8220;No root file system defined. Please correct this from the partitioning menu.&#8221;

I am not too sure where to correct this error and would really appreciate some advice. Many thanks in advnace.

Max

---

### Post by Partyboi2 on 2009-04-09
If you are using wubi to install (installing inside windows) try running a 
```
chkdsk /r
``` first before installing.

---

### Post by Max Avion on 2009-04-09
Thank you for the reply but how is chkdsk going to specify a root directory?

Thanks,
Max

---

