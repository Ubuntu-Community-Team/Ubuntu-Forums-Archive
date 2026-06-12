---
title: "[SOLVED] New install Ubuntu 8.04.1 + 8.10 Wubi"
date: 2008-10-28
forum: General Help
---

### Post by jmszr on 2008-10-28
I'm going to be installing 8.04.1 on a new 250GB Seagate/Maxtor SATA 7200 HD
My questions are: 1.) when I partition the HD if I give Wubi 8.10 a 15GB partition will it run properly? ( Any conflicts with 8.04.1?) 2.) Should I use ext4 for it or stick with ext3? - I guess I'll have to use ext3 for 8.04.1. Anything I need to watch out for?

---

### Post by s34nn4 on 2008-10-28
as the matter of fact i run 10GB on my HP pavillion using wubi installer for roughly 4mos. and never encounter any downside. 15 is enough since Linux is not resource hog. 

Wubi is the simpliest way to partition a Windows base OS with no hassles.Choose Ext3 for fast performance this is the journal file system for Linux. BTW welcome to our community... ubuntu is an awesome Distro compare to any other, it is  smooth and runs perfectly on any PC.

---

### Post by ago on 2008-10-28
You cannot install both wubi 8.04 and 8.10 unless one of the two is installed to a dedicated partition. 

You can upgrade 8.04 to 8.10.
If you installed 8.04 via wubi and run wubi again to install 8.10, it will ask first to uninstall your previous version. If so make sure you backup your data first.

---

### Post by jmszr on 2008-10-28
ago,
     I wasn't clear in my previous post,I guess. I want to do a full install of 8.04.1 and make a 15 GB partition for Wubi 8.10.  Absolutely no Windows (or any other OS). My thoughts were 15 GB /, 15 GB Wubi 8.10, 3 GB swap, and the rest /home. Would the order of the partitions need to be in a certain progression? I know that / should come first but I was wondering if it made a difference what order the rest of the partitions came in. Any information would be much appreciated.

                                                  Thank you, Jeff

P.S.: AMD Athlon64x2 5200+, 2GB RAM, GeForce6100PM-M2

---

### Post by ago on 2008-10-28
Any order will do, primary or logic also make no difference.

---

### Post by jmszr on 2008-10-28
ago,
     Thanks, very good to know.
                                Jeff

---

