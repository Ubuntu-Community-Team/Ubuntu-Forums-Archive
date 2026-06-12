---
title: "NTFS drive locked, hidden from ubuntu"
date: 2008-04-23
forum: Hardware
---

### Post by jdabgotra on 2008-04-23
OK so I have three partitions, linux, windows xp, and my files on NTFS. Now, one day windows crashed, but it left the ntfs drive in use or locked or whatever. In ubuntu I neither see the windows nor the Files partitions, just the linux partition. Now, I tried reinstalling windows but its freezing during the setup; I need to try another installation CD. Even if I reinstall windows, I'm not sure I will be able to unlock the Files partition. I don't care for windows on that computer so just help me unlock this thing from linux - thank you!

---

### Post by lswest on 2008-04-23
you can run a chkdsk on it ```
sudo apt-get install ntfs-progs
``` and then do ```
ntfsfix /dev/sd??
``` where sd?? is the partition where windows is/was installed.  Otherwise you can force-mount it, but try the above first.

---

