---
title: "RAID controller card install"
date: 2013-07-31
forum: Hardware
---

### Post by HMxn6Te on 2013-07-31
I'm VERY new to linux/Ubunutu. This is actually my first install & exposure to it.

I'm switching to Ubuntu Server from Windows XP.

The issue is that I have a 4 bay RAID enclosure managed by a RAID controller card both sold by Cavalry Storage. The RAID controller uses a Sil3132 chip. I have the RAID system working in windows (RAID5 formatted to 2 partitions so Windows can see the >2GB disks) but it's not seeing any disks under the Ubuntu file manager.

Does anyone know if the driver for the Sil3132 chip is included in Ubuntu? There is VERY scant info on this chip when I did a search on it.

I have no idea how to even go about troubleshooting this problem. 


Thanks in advance...

---

### Post by Vladlenin5000 on 2013-08-01
I would be surprised if such chip wasn't supported but it's not impossible, just highly implausible. What probably happened is you configured you RAID by software under Windows. If so, no surprise Linux won't see it.

---

