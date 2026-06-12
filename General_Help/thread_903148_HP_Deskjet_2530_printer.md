---
title: "HP Deskjet 2530 printer"
date: 2008-08-28
forum: General Help
---

### Post by Andrew79 on 2008-08-28
just picked up this printer. got 8.04, it sees it, but when I hit print, nothing. called hp, said not compatable. anybody got anything on this? If not, what printers are good for printing photos, and compatable?
Thanks

---

### Post by Sef on 2008-08-28
It's [compatible]("http://hplip.sourceforge.net/models/deskjet/deskjet_d2500_series.html").   Download HPLIP from Add/Remove.   Applications > Add/Remove > Search: HPLIP  > Apply Changes > Apply > Close

After downloading, use it and find if it reports an error.  If so, then copy and paste it here.

---

### Post by Andrew79 on 2008-09-02
No device found or unsupported device

---

### Post by zachthejones on 2008-09-06
Make sure you have the [latest version]("http://hplip.sourceforge.net/downloads.html") of HPLIP installed - it's not in the repos. I had the same problem (I think).

make sure you check out the installer walkthrough (link is right above the download icon). The walkthrough didn't mention all the choices I had to make through the installation, but it wasn't hard. It should remove the older version of HPLIP for you. In the end, I didn't even have to restart my computer, I just used the "un-plut and re-plug" option and the hp-setup detected everything perfectly!

[here's]("http://ubuntuforums.org/showthread.php?p=5741233#post5741233") the thread where I posted what worked.

Good luck!

---

