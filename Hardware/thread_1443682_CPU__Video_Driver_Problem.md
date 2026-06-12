---
title: "CPU / Video Driver Problem?"
date: 2010-03-31
forum: Hardware
---

### Post by dapaintballer331 on 2010-03-31
I have a TabletPC:
Came with 4gb of ram
Huge hd
128mb of video memory (intel built in)
Intel core 2 duo CPU (2.77ghz total) 64 bit.

With Jaunty, compiz worked GREAT and EVERYTHING went smoothly and worked fine.

Yesterday I upgraded to 9.10 64 bit from jaunty, 64 bit.
Here are the problems:
VERY slow.
CPU2 isn't being used.
CPU1 is being maxed out. I rarely ever used 30% of my cpus, it should not be maxed out.

What can I do to fix this? CPUs obviously aren't working right after the update. VIdeo may or may not be working correctly.

---

### Post by dapaintballer331 on 2010-03-31
I disabled compositing... problem fixed.
 gconftool-2 -s --type bool /apps/metacity/general/compositing_manager false

---

