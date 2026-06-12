---
title: "Printer support"
date: 2013-07-31
forum: Hardware
---

### Post by jmdlcar on 2013-07-31
Hi all,

Can anyone tell me if the Desktop 1000 and 1000c the same printer? Wal-Mart has the Deskjet 1000 and OpenPrinting.org support desktop 1000c.

Thanks
Jack

---

### Post by flipper88 on 2013-07-31
Useralu with hp printers a c at any position in the name stands for folor at lease that was the case in the 1990s with the Deskjet 540 and 540c.

---

### Post by oldfred on 2013-07-31
HP supports its printers very well with its HPLIP, but the version installed from the repository is old and it is best to download the newest version directly from HP.

I have a HP Deskjet 3520
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

---

### Post by jmdlcar on 2013-08-01
> **oldfred said:**
> HP supports its printers very well with its HPLIP, but the version installed from the repository is old and it is best to download the newest version directly from HP.

I have a HP Deskjet 3520
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

Hi,

I see there is a new version out now 3.13.7 now. I work at Wal-Mart I'm going to check want HP Printer they have before I buy any. I know LUbuntu or Ubuntu  will not support WiFi or LaserJet printer I don't think so maybe someone can help on this. I'm going get a list from Wal-Mart and ask.

Thanks
Jack

---

### Post by oldfred on 2013-08-01
My HP Deskjet 3520 printer has wi-fi and I originally tried to do it from commands, but that was not easy. It created a new wifi network.  But once I downloaded HPLIP it was easy to set up to my existing wifi and my wife printed directly from her iPad.

---

