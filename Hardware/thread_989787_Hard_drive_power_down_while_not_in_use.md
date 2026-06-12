---
title: "Hard drive power down while not in use"
date: 2008-11-22
forum: Hardware
---

### Post by RFXCasey on 2008-11-22
Hey all,

I have an extra hard drive in my PC that I only use for making image backups. I was wondering if there was any other way besides unplugging it to keep it off or spun down while not being used and then activate it only when I want to make an image backup. The two main reasons are for drive life and power consumption. Will simply unmounting it in Ubuntu do this or is there some other way I can do it through the OS. Thnanks.

---

### Post by IcarusR on 2008-11-23
Hi,
You can use hdparm, for ata drives & sdparm for sata drives, to set spindown timeout. 
See man pages for details & do a google search for more info.

---

