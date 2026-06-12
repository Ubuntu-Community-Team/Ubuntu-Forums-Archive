---
title: "Difficulty removing wubi"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by triplesick on 2009-08-12
Due to difficulties with the partitioner using the standard Ubuntu 9.04 CD, I chose to "install inside windows."  Later I was able to partition my drive manually and install Ubuntu properly, and wanted to remove the wubi installation, as I believe it is called.  I went to add/remove programs, and after 2-3 seconds, it said it was done, and indeed I had my hard drive space back.

But when I start up my computer, after the initial boot menu (Linux partition vs. Windows partition), if I choose to boot to Windows, I still get the wubi boot menu (windows vs. ubuntu).  How can I completely get rid of the wubi installation?  An automated process would be ideal, as I am an absolute beginner with Linux.

EDIT: I only have one hard drive.

---

### Post by raymondh on 2009-08-12
If you're running XP ... and from the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?") ... you'll have to manually delete the WUBI (_JUST THE WUBI!_) from the boot.ini file.

Remember, just the WUBI/UBUNTU related line.  Also, do back up your files :)

---

### Post by triplesick on 2009-08-12
So I deleted the boot.ini file like you told me to, but now I can't get Windows to boot at all.  No Windows, no nothing.  Just kidding.  Thanks, it worked great.

---

### Post by raymondh on 2009-08-12
> **triplesick said:**
> So I deleted the boot.ini file like you told me to, but now I can't get Windows to boot at all.  No Windows, no nothing.  Just kidding.  Thanks, it worked great.

Notice the underlined and double warnings?  (Just kidding as well .... )

Excellent news.  Happy Ubuntu-ing :)

---

