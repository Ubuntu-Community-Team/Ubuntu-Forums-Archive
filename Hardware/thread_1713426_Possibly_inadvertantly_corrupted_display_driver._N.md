---
title: "Possibly inadvertantly corrupted display driver. Now have no GUI."
date: 2011-03-24
forum: Hardware
---

### Post by jsw1984 on 2011-03-24
After updating my radeon hd 6310 driver I had an "AMD unsupported hardware" watermark appear in the bottom right hand corner of the screen. I did some research and found a suggestion to copy the control file from the older driver to the newer driver file. Once I rebooted, my GUI was gone and I can only log into the terminal. My question is, is it possible to reinstall the driver using only the terminal? I'm new to Linux so I would appreciate a simplistic answer. If at all possible I want to troubleshoot this without reinstalling the entire OS.. that would make me feel defeated!

---

### Post by cbowman57 on 2011-03-24
> **jsw1984 said:**
> After updating my radeon hd 6310 driver I had an "AMD unsupported hardware" watermark appear in the bottom right hand corner of the screen. I did some research and found a suggestion to copy the control file from the older driver to the newer driver file. Once I rebooted, my GUI was gone and I can only log into the terminal. My question is, is it possible to reinstall the driver using only the terminal? I'm new to Linux so I would appreciate a simplistic answer. If at all possible I want to troubleshoot this without reinstalling the entire OS.. that would make me feel defeated!

Try sudo apt-get install <filename> --reinstall

---

