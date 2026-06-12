---
title: "Gparted - Formatting my MP3 Player"
date: 2008-11-10
forum: General Help
---

### Post by c0da on 2008-11-10
Hi guys,

I have some problems with formatting my MP3 Player.

Laptop: Acer Aspire One
Ubuntu 8.10
MP3 Player: Zen Stone Plus 2gb

When I start gparted it shows me the player (/dev/sdb/ 470.65MB) but I'm not be able to format/create a new partition.

After clicking the NEW Button I have to set a Disklabel. When I select the format *msdos* I got following error message in my console and gparted abruptly closed.

> Device /dev/sdb has a logical sector size of 2048.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Unable to open /dev/sdb - unrecognised disk label.
Segmentation fault

What am I doing wrong?

---

### Post by Pro-reason on 2008-11-10
Are you using the latest GParted available in the repos?

---

### Post by c0da on 2008-11-10
I'm using the version 0.3.5-1ubuntu3. (sudo apt-get install gparted)

---

### Post by Pro-reason on 2008-11-10
Try [searching for the text of the error]("http://www.google.com.au/search?num=50&hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-GB%3Aunofficial&hs=flP&q=Not+all+parts+of+GNU+Parted+support+this+at+the+moment%2C+and+the+working+code+is+HIGHLY+EXPERIMENTAL&btnG=Search&meta=").

---

