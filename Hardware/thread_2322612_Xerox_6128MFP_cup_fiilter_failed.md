---
title: "Xerox 6128MFP cup fiilter failed"
date: 2016-04-29
forum: Hardware
---

### Post by srfrnk on 2016-04-29
Ubuntu 16.04 encountered the same issue as in:
[http://ubuntuforums.org/showthread.php?t=1604572](http://ubuntuforums.org/showthread.php?t=1604572)

Since ia32-libs isn't supported I finally found this helps:
sudo apt-get install lib32stdc++6 libcupsimage2:i386

Hope to save you a few hours of mucking about :)

---

### Post by srfrnk on 2016-04-29
PROGRESS:
Checked another machine and the above step wasn't enough so I decided to record everything and publish as a script.
Can be found here:
[https://github.com/srfrnk/contribute/blob/master/XeroxUbuntuInstall/install.sh](https://github.com/srfrnk/contribute/blob/master/XeroxUbuntuInstall/install.sh)

---

