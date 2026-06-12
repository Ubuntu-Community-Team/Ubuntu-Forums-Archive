---
title: "Help me find my missing GBs"
date: 2010-10-13
forum: Hardware
---

### Post by rodolphoarruda on 2010-10-13
Hello all,

It's been a while that I've noticed a significant drop in available space in my system.

The HD analyser tells me that I'm using 63.4GB, but the actual figure is 96.7GB (see the picture). This is so annoying.

I want those 33.3GB back! I paid for them! :)

Any clues on what's going on?
Thanks in advance

---

### Post by drs305 on 2010-10-13
This may help out:
[ HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by rodolphoarruda on 2010-10-13
> **drs305 said:**
> This may help out:
[ HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

thanks! great reference and lots of points to check.

---

### Post by rodolphoarruda on 2010-10-13
Solved.

This is what I did.

```
gksudo baobab
```

So I could see files that were hidden to my user. And I found this little fellow here: a 33.2GB backup file under var/backup

I moved it to my external drive and got my space back. Thanks again.

---

