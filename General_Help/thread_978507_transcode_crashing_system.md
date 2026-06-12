---
title: "transcode crashing system"
date: 2008-11-11
forum: General Help
---

### Post by Paulmoore on 2008-11-11
Once upon a time back in the Gutsy days I used to be able to rip a dvd. Upgrading to Hardy broke that and upgrading to Intrepid didn't fix it. When ever I try to rip a dvd with transcode/DVDRip (as well as DVD Decrypter in wine) the system hangs and I have to do a hard reboot.

I can play DVDs, and DVD rip can read the TOC, but when Transcode starts to strip data from the dvd, the system freezes. I can't figure out what's happening and it's starting to drive me crazy. Anyone have any ideas on what's going on?

---

### Post by nothingspecial on 2008-11-11
I don`t know what`s causing your problem but I use acidrip. It`s in the repos. You could try that.

---

### Post by Paulmoore on 2008-11-15
As it turns out... It wasn't transcode's fault at all. And I thought I had solved my DVD playing problems as well, which is why I said that I could play dvds. Turns out the problem is that my Secondary IDE controller isn't working like it should. Moved drive to primary as slave, and everything works now. I have no idea why that would happen. She's running on 6 years now, but I haven't seen a controller go bust like that before.

---

