---
title: "Strangely high unload load cycle count on harddrive?"
date: 2012-02-09
forum: Hardware
---

### Post by jonnyboysmithy on 2012-02-09
I noticed my harddrive was sounding like it was parking and unparking very often sometimes every 5seconds or so and keeps doing that for a while. Why could that be?

---

### Post by jonnyboysmithy on 2012-04-28
Turned out it was because it had some sort of 'eco' feature that turned the drive off after 8 seconds idling.
Thats a great way to put 77,000 cycles on the clock of a new harddrive in just 5months of use.
To stop it doing what it was doing ran this command at startup with a script ```
sudo hdparm -B 255 /dev/sda
```

Thank you western digital for your 'eco' feature (read "high wear") that would be sure to kill my disk prematurely.

---

### Post by ahallubuntu on 2012-04-28
I had one of my archive drives in an old Windows 2000 box for a while before I built a new Ubuntu server for it.  I had an identical drive (both WD green drives) that wasn't in the 2000 box at all.  The original drive has a huge load cycle count I guess because Windows 2000 had crappy support for it or something.  I've not had these kinds of issues in Ubuntu, fortunately.

If the drive is new enough to still be under warranty (sounds like it), just RMA it on WD's website and swap it for a new one, if you are able to, if the high load cycle count you've already got bothers you.  I RMA'd a WD drive a couple of months ago and the replacement drive arrived pretty quickly.

---

