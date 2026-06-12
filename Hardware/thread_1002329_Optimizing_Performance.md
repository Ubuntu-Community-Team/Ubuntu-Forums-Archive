---
title: "Optimizing Performance?"
date: 2008-12-04
forum: Hardware
---

### Post by Mewshi on 2008-12-04
Hello!

I have a Compaq CQ70-120US, with the following specs:

Processor      :  Intel Pentium Dual-Core 3200 (2 cores at 2GHz each)
Memory         :  3GB of RAM
Hard Drive     :  250GB Hard Drive
Video Processor:  Intel 3200HD
Wireless       :  Atheros 928X a/b/g/n


What I would like to know if there is anything useful I can do to optimize the performance of this?  Also, programs for better management of the dual-core system would be nice :)

Thanks!

---

### Post by mariner09 on 2008-12-04
I googled on speeding up ubuntu and found many options that seem to make things better.

Obviously, no compiz makes for great desktop performance, but no eye-candy.

Prelink and preload also help if you run a lot of apps.

There are other tips that make booting faster.

Try to stay away from the current fstab modifications because the newer settings in Intrepid use relatime which seems to be better.

Setting vm.swappiness to a lower value is also good.  I use 0, but 10 is recommended.  90 is the default.

---

### Post by benny bronx on 2008-12-04
I've disabled some services and startup programs that I obviously don't use or need, but I'm not sure I've actually noticed performance increase or faster boot times.  What I did notice was that setting the swappiness lower, as suggested by mariner09, did increase performance.  I set mine at 10.  I believe that the default is 60, however. See:

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by sdennie on 2008-12-04
Generally, if you are going to optimize something, you should understand if it's slow or not.  There is no silver bullet for making Ubuntu faster but, depending on your hardware, usage, etc. some things can make it more responsive in some cases.  What specifically are you finding slow?

---

