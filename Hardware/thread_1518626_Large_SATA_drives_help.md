---
title: "Large SATA drives help"
date: 2010-06-26
forum: Hardware
---

### Post by ags40 on 2010-06-26
Do you have suggestions to partition large or very large capacity SATA hard drives? If yes, would you please suggest a brand? Any info in excess of this is very welcomed. Thanks you all.

---

### Post by atomizer on 2010-06-26
30 GB / (root)
2 times your memory for swap
rest /home 

When you share all your data with Windows I would take about 30 Gb as /home and the rest /data or whatever you wat to call it and format it as fat32 or ntfs (if ntfs, format it in Windows)

---

### Post by neovandeen on 2010-06-27
I think, if you're using it singe boot, you don't have to bother about partitions.

If you don't you'd create the basic stuff eg. / and /home .. and  a big /data partition with NTFS or so. You can create some folders on it, like music and video and link them to your /home directory. So you can access the same data from windows.

---

### Post by cascade9 on 2010-06-27
Depends on if yuo want dual-boot with windows or not. If you want to dual-boot, then a big NTFS data partition (like neovandeen said) is probably a good idea. 

BTW, I'd NEVER use a single partition. EVER. I didnt do it with windows, for the same reason as why I wouldnt do it with linux distros- what if you want to format and reinstall fo some reason? The /root and /home standard partitioning scheme is part of what attracted me to linux distros in the 1st place. 

Anyway, I'd break it up like this- 

/root (20GB max, and I'd probably settle for 15GB).
swap (probably x2 the RAM, depending on the amount of RAM in the system)
/home (100-200GB)
the rest as a data parttion (EXT3 if for linux only use, probably NTFS (yuck!) for dual-booting. 

As for brands- personally, I like WD, but the new 'advanced format' drives are a PITA. As far as I know, he caviar 'black' models are still only avaible in the normal format, not the 'advanced format', so that is what I would probably get (fast, 5 year warranty). Samsung makes some good drives these days, so that would be my 2nd choice, and hitachi/seagate are just 'if I have to or if the customer requests them' drives for me.

---

### Post by ags40 on 2010-06-28
Thank you all very much!!!

---

### Post by cascade9 on 2010-06-29
No problem ;)

---

