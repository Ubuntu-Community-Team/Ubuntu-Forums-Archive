---
title: "Cannot get proper intall with liveCD or WUBI"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by phil7784 on 2009-05-29
I'm about ready to give up. Cannot get Ubuntu 9.04 installed properly on my PC. I have downloaded and burned the Live CD with which I can try ubuntu without problems. When I try to install it from that disk it insists on installing to a small partition of only 2.5GB which it makes on one of my disks where there is 35GB free. I can't adjust the size of the install or its location. My computer has an AMD 1.4GHz processor with 1GB RAM and a single HDD which is divided into primary partition of 35GB, and an extrended partition subdivided into 35GB, 5BG, and 2GB. The install into the 2.5GB area works, but there is no room for any downloads, updates or other data. If I use WUBI (including the newest one) I can specify the drive and the size - I have done this on my primary partition and tried the other 35GB one using 9GB space. When download is complete and I try to boot into ubuntu I get an error screen as follows: Try (Hd0): NTFS5 2  TRY(Hd0,1):extended  Try (hd0,2): invalid or null  Try(Hd0,3): invalid or null  Try(Hd0,4): NTFS5: no wubildr  Try(Hd0,5): extended  Try(Hd0,5) NTFS5 No wubildr Try(Hd0,6): extended Try(hd,0,6) NTFS5  Error while reading MBR of drive (Hd0,1) No wubildr  Try (Fd,0): invalid or null  Error: cannot find GRLDR in all devices. Press Ctl+Alt+Del to restart.
I have read extensively on many of the pertinent websites, but cannot figure it out. By the way, wubildr and wubildr.mbr are in my root directory of C: and the ubunutu folder is also on the C: drive (this is after the latest attempt with Wubi). Can anyone deciper this for me and help?

---

### Post by ajgreeny on 2009-05-29
Try using partition editor in the live CD to either resize your XP partition after defragging it a couple of times, or to delete the 35 GB partition in your extended partition,  Now make a new ext3 partition and try to install into that, using the manual partitioning when you get to that part of the install procedure.  It should work OK, unless I'm missing something or you have not told us the full story.

---

### Post by phil7784 on 2009-05-31
Thanks for your help. I was finally able to resize my partitions and install 9.04 from the Live CD.

---

