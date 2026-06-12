---
title: "Unable to smartctl on external USB drive - &quot;Aborted by the host&quot;"
date: 2013-12-17
forum: Hardware
---

### Post by kgandhiok on 2013-12-17
Hi,

I'm running an hp laptop with windows 7 and Ubuntu 13.10 dual boot. I wanted to check the sectors of my Seagate external 1tb USB drive using smartctl. About 30 minutes after starting the test, I did command smartctl -c /dev/sdb to check the status of the test. I was given "Self-test status as - The self test routine was aborted by the host". I don't understand how the test was aborted because I didn't abort it. 

Is it possible that Seagate has some bug that does not allow smartmontools? Should I use some other method to check my external drive? Can I use fsck to check and repair external drives?

Any help regarding this would be much appreciated. Thanks!

---

