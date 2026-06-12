---
title: "Sound issues after install"
date: 2011-12-05
forum: Hardware
---

### Post by ccwillrun on 2011-12-05
I recently installed Ubuntu 11.10 on an old laptop of mine, an emachines W4605. Other than a minor firmware issue with my wireless card the install went fairly smooth. The one problem that I have is that I cannot get any sound.I can move the volume up and down but there's nothing happening...

I've searched to forums and haven't really found any posts that are similar to my scenario. Has anyone else had this problem and found a solution? I really think it's simply a driver issue, but I'm new to Linux and at a loss on where to even begin.

Update: I can actually hear very faint sound if I plug the headphones in and turn the volume all the way past 100% in the sound settings.

---

### Post by ccwillrun on 2011-12-17
After some searching, I found this thread, which solved my problem. 

[http://ubuntuforums.org/showthread.php?t=1583078](http://ubuntuforums.org/showthread.php?t=1583078)

The post by lidex on October 8 was what I used. I just added the 4 lines to the end of alsa-base.conf as instructed and now my sound is working. Genius.

---

