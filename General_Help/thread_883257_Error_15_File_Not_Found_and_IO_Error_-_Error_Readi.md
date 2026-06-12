---
title: "Error 15: File Not Found and IO Error - Error Reading Boot CD"
date: 2008-08-07
forum: General Help
---

### Post by robnoyes on 2008-08-07
I'm trying to re-install Hardy because of the problems below, but I can't get anything to run, Live CD, Install, Check CD, Memtest, or Boot from 1st HD.

Without the Live CD, I can get past Grub to an error reading: Error 15 File Not Found
- forums said to ensure boot disk is hd(0,0), not hd(1,0). Checked...that wasn't the problem.

With the Live CD, I get to the menu choices, but as soon as any are chosen the following error occurs: I/O Error Error Reading Boot CD. 
- forums said to record CD at the slowest speed available. I did, no change.

Help...thanks in advance.

---

### Post by spiderbatdad on 2008-08-07
It may be the iso is corrupted. Have you verified the md5sums of the iso...and it is possible, though very uncommon, that even if the md5sums match, the iso is still bad.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the iso is bad try getting it from another source.
Also check the integrity of the cd after it is burned.

---

### Post by robnoyes on 2008-08-07
Well...comparing the MD5SUM to UbuntuHashes, the ISO is toast.

I'm downloading a new iso from the MIT Media Lab. Hope it's better.

I'll let you know what happens.

~RLN

---

### Post by robnoyes on 2008-08-08
That did it...I DLed the full release from the MIT server and I was able to install.

New problem now, but I'll post in a new topic.

Thanks, Rob

---

### Post by jack102 on 2008-12-06
hi guys i have compared the md5sums and they match. shall i reburn the disk at the slowest speed or try to install again?

---

