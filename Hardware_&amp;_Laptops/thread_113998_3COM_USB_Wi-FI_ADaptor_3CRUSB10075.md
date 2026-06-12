---
title: "3COM USB Wi-FI ADaptor 3CRUSB10075"
date: 2006-01-07
forum: Hardware &amp; Laptops
---

### Post by herra on 2006-01-07
Hi,
Total noob to Linux.
Can't get my Wi-Fi adptor recognised.
I've found a linux driver on the 3Com website but I've no idea what to do with it. I also read about using the Windows driver (I have it as a dual boot) with NDISWRAPPER but this always gives me errors.

Something about Make or something for the Linux Driver?.. sorry guys.. Can anyone walk me through step-by-step. I don't even know how to unZIP in Linux.



Cheers

---

### Post by Lambert on 2006-01-07
I show this using the zd1211 driver which comes in breezy but doesn't work. The link I'm about to give isn't the easiest for a newb to understand but you can ask for clarification there. 

[http://www.ubuntuforums.org/showthread.php?t=92327](http://www.ubuntuforums.org/showthread.php?t=92327)

It's also about adding in wpa but you can ignore the wpa and hostap steps. You basically need the source. unizip it and make && make install. Sound confusing, not really. Read through the thread and ask questions. You'll find plenty of help.

---

