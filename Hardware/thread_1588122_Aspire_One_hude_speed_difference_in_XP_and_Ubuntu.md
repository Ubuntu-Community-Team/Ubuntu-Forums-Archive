---
title: "Aspire One: hude speed difference in XP and Ubuntu"
date: 2010-10-04
forum: Hardware
---

### Post by ctyt on 2010-10-04
I'm just wondering why my Acer Aspire One (1.6ghz, 1024MB) is so much quicker in XP than in Ubuntu. On my desktop (Athlon 64 3700+, 2048MB), Ubuntu is much faster than XP. I do have a swap file, so that's not it. Also, all the effects are disabled. 

My theory is that it may have something to do with CPU throttling for power-saving purposes. How do I check that the frequency does jump to 1.6ghz when I need it?

---

### Post by mikewhatever on 2010-10-04
You can check it with the following command:

cat /proc/cpuinfo | grep "cpu MHz"

The output should be different when idle or under load.

---

