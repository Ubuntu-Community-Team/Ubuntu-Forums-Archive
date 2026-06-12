---
title: "Dell XPS M1330 display/monitor EDID problem"
date: 2011-06-02
forum: Hardware
---

### Post by dop3 on 2011-06-02
Hi all,
I've a problem with my laptop (dell xps m1330) and its internal monitor!

Something like 6 months ago I had problem after an ubuntu upgrade. After this upgrade on boot I had blank monitor with vertical lines starting to appear on it!
I could hear ubuntu sounds so I knew the OS was starting good... but, obviously, not the monitor.
I could use my laptop only via an external monitor!

After a lot of search I found a solution. Using, via xorg.conf configuration, the edid file that I could extract from windowz I could go back in business with my ubuntu and the monitor ([http://ubuntuforums.org/showthread.php?t=316985]("http://ubuntuforums.org/showthread.php?t=316985"))!

1 week ago I switched to Windowz 7 and I had to format and re-partition my entire Hard Disk.

I installed Ubuntu 11.04 and I had the same problem (black screen with vertical lines).
Then I tried to do the same operations (extract edid via windowz) but I coudn't extract the edid no more. With Phoenix Edid Designer I could just extract the Edid for my external monitor.. not the internal!

I tried a lot of things before giving up and write this post.

Cannot start with nouveau nor with nvidia proprietary drivers (from package manager or downloaded from nvidia site and then installed via source)...

I could start Ubuntu fine in failsafemofe or with the "ubuntu native" nvidia module (but no 3d acceleration and so on).

Now, I'm asking if you know some alternative solution or, maybe, if you can give me an edid file for my monitor (if possible) or the value to set in xorg.conf to re-start usign ubuntu!

Thanks and forgive me for my english

---

### Post by dop3 on 2012-07-06
I'm still stuck at this!

If someone could give me a xps m1330 raw edid file or a xorg.conf file for my laptop i will really appreciate!

Thanks

---

