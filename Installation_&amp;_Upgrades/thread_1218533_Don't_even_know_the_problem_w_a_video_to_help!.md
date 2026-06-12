---
title: "Don't even know the problem w/ a video to help!"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by 98xjdmb on 2009-07-20
Alright, well as you'll see in the video, i am trying to bring a computer back to life. Actually i didn't know it was dead, i mean it worked a couple of months ago aside from the dead power supply. And yes, it has worked with my hacked together supply too. So i went to do a full install and ran in to some issues with partitioning the disk. I just kept getting an error, which in retrospect would have been good to remember what it said, but i don't and now i have the issue you will see.... thanks for the help!

link to video: [http://www.youtube.com/watch?v=k-p-AOTNlPg](http://www.youtube.com/watch?v=k-p-AOTNlPg)

ps, sorry for the crap quality, i'm a bit rushed

---

### Post by 98xjdmb on 2009-07-21
anyone?

---

### Post by Mark Phelps on 2009-07-22
From my own experience, it's best NOT to partition the drive as part of the Ubuntu install, especially if you suspect drive problems.

Go to distrowatch.com, find the GParted LiveCD, download it, and burn it to a CD.  Then boot from that and see what it allows you to do. If it can't read the drive (as your video indicates), then basically, it looks like you have a bad drive.

In that case, check the drive manufacturer. They generally provide downloads of utilities you can use to check their drives (Seagate provides SeaTools, for example).  You would need to download and burn a CD from their utilities, boot from that, and run it to do diagnostics on your drive.

---

