---
title: "&quot;Transmission&quot; restart torrents to 0.0% after every reboot"
date: 2008-10-27
forum: General Help
---

### Post by TheSixthPandava on 2008-10-27
This is major problem for me, since I don't just leave my computer with power on all time long.

I started to use Transmission to download some torrents only few days ago, and I really like it, and I am keen to stay with Transmission, but if I can't solve this problem I have, I will definitely need to change bittorrent client again [and I don't what that...].

This is the problem: every time I reboot my computer, Transmission restart all torrents and start to download from the beginning [for example, I am downloading some Japanese film, and when I rebooted computer it was around 50% finished, and now it started again from 0.0%). I have one 21,1 GB file that I download from Mininova with a very slow DL rate, and I can't have this problem when I have some 2 weeks in prospect of this download.

Does anybody know why is this happening and how can I solve this problem?

---

### Post by sethvath on 2008-10-27
Which version of ubuntu is this? 32bit/64bit hardy/intrepid?

Version of tranmission and have you made any changes to the preferences tab in transmission.

---

### Post by TheSixthPandava on 2008-10-27
Gutsy 32bit.
Transmission is 0.91 (3628)

I changed upload limit to 30 KB/s, default download directory, and "For torrents added normally" and "For torrents added from command-line" I changed from "Keep a copy of a torrent file" to "Use torrent file where it is". Nothing else. Maybe this last thing I mentioned, maybe that is creating the problem.

---

### Post by ChildOfMana on 2008-10-27
Did you change the default download directory *after* you started downloading the torrents?

---

### Post by TheSixthPandava on 2008-10-27
No, I changed it immediately after I installed Transmission [on Gutsy it is not official torrent client]. 

Strange thing, I changed "For torrents added normally" and "For torrents added from command-line" from "Keep a copy of a torrent file" back to "Use torrent file where it is", rebooted computer and it seemed that it is working properly. But then, when I tried to "Verify local files" it was back on 0.0% again.

---

### Post by sdennie on 2008-10-27
Where are you saving the files?  Specifically, are you saving them to somewhere that is mounted as tmpfs or something of that nature?  That would delete the files on reboot and cause the kind of behavior you are describing.

---

### Post by TheSixthPandava on 2008-10-27
Vor, I have 'BitTorrentDownload' folder on my Desktop, so it can't be that.

---

### Post by TheSixthPandava on 2008-10-27
Well, this is how it is. After change I mentioned, I deleted all torrents from within Transmission and all folders it downloaded previously, and started it all again, and now it is working properly.

Thanks for suggestions.

---

### Post by TheSixthPandava on 2008-10-29
Strange, it seems that it still isn't working all properly. I wanted to check to see what happens if computer is rebooted while Transmission is working, and Transmission didn't saved the files between regular program shutdowns, and it started from the previous stage [for example, for one film it get back from 77,1% to 18,7%]. Maybe I want to much, I don't know, but I do know that that terrible original Ubuntu BitTorrent was memorizing everything with no problem.

---

