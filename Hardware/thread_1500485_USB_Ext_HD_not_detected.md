---
title: "USB Ext HD not detected"
date: 2010-06-03
forum: Hardware
---

### Post by colintivy on 2010-06-03
I have three USB drives, one 16GB Pen drive and one 80GB HD in an enclosure. Both of these are happily detected and mount OK. The remaining is a 2 1/2" 20GB HD in a Integral caddy which seem not to be detected at all when plugged-in (its blue light shows that it is at least powered-up). This drive has been checked in a Windows machine and works OK. Its contents are an old Win 98 SE system which I want to clear out in order to reformat to ext3 or 4. Is there a known USB bug at the root of this problem?

colintivy :confused:

---

### Post by colintivy on 2010-06-06
Sorry!    BUMP

---

### Post by efflandt on 2010-06-06
After you connect it, does it show up in **sudo fdisk -l** (small L)?  Or if you have gparted installed, that will usually tell you if it thinks there is something wrong with a partition.

You might try running **chkdsk /f** on it from Windows just in case something is corrupted that is not apparent.

---

### Post by colintivy on 2010-06-07
fdisk -l shows nothing added at all, only my main HD in the laptop. I had heard that that there were bugs in USB that could cause this. I also dmesg'ed as well nothing there either. I do know that if I plug either of my other USB drives in they mount immediately. I am not dual booting with Windows so cannot explore that way. The drive was checked on a dealer's machine with Xp and Vista and all the files are on it. He had not ventured into 7 at that time. It is all very strange. Any other routes to try?

colintivy  :confused:

---

### Post by colintivy on 2010-07-15
Sorry....bump!!:(

---

