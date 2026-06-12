---
title: "Gaming and mp3 issues?"
date: 2008-09-22
forum: General Help
---

### Post by SuccessfulTroll on 2008-09-22
Ok, heres my dilemma(s). First off, all my crap seems to have disappeared, but is still showing when I boot windows. Linux is on my secondary drive, while windows is on my first most. Any ideas on how I can get my music from one to the other?

Next, I'm trying to run Warcraft 3 TFT on ubuntu, and I dont quite understand the processes involved when working with wine. Anyone feel like helpin me out there...

---

### Post by Pro-reason on 2008-09-22
So your drive is not automatically mounting?  Let's see.  Type the following commands into a terminal, and post the output here.  Then we'll fix it.

```

sudo fdisk -l
sudo blkid
cat /etc/fstab

```

As for your second issue, please create a separate thread about it in the [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313") forum.

---

