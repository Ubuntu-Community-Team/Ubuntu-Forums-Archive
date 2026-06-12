---
title: "high frequency sound coming from the monitor"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by toxonics on 2005-08-09
It happened with Warty and I stoped using it, now it's happening with Hoary too. Some time after I installed it a high frequency sound started to be emited by the monitor, it's a Samsung SyncMaster 795DF. It's really anoying after a while. I searched the net but couldn't find anything similar happening to anyone, help me please before I go nuts  :)
Graphics card is a GeForce4 420. I tried nv and nvidia driver. Screen resolution is 1024x768 at 85Hz. The sound starts when GDM loads, and it seems to be higher when something white is one the screen comparing to something black or dark blue. It didn't happen when I used SuSE and it doesn't happen when I use Windows.

Thanks in advance for any kind of help
Milos

---

### Post by heimo on 2005-08-09
Check that horizsync and vertrefresh lines in /etc/X11/xorg.conf match specification of your monitor. h:30-96 v:50-160 You can try also a bit lower values (for higher limit).

Source of these numbers:
[http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=HQ&CttFileID=167129&CDCttType=UM&ModelType=N&ModelName=795DF&VPath=UM/200402/20040227071901437_BH59-00362A-00Eng.pdf]("http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=HQ&CttFileID=167129&CDCttType=UM&ModelType=N&ModelName=795DF&VPath=UM/200402/20040227071901437_BH59-00362A-00Eng.pdf")

How to edit xorg.conf:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

