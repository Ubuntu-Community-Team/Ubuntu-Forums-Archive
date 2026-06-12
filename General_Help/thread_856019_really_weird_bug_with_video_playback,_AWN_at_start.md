---
title: "really weird bug with video playback, AWN at startup, and metacity compositing"
date: 2008-07-11
forum: General Help
---

### Post by kaitwospirit on 2008-07-11
I would love to file a bug report, but I don't even have a clue where to file the bug...

So: I just installed AWN last night. Great fun! Pretty shiny dock for everybody! 

Then I set AWN to run at startup using System>Preferences>Sessions. At the next reboot, I got some weird video playback issues when running mplayer or VLC: the video would not appear at first. If I forced it to redraw by dragging the window on the screen, it would appear, flickering. If I managed to stop the window while it was flickered on, it would play back just fine. I had this issue both with video files of various types and with mplayer's visualization feature, and it worked the same way in both players (except the "GOOM" visualization in mplayer just wouldn't work at all).

I can only get this to happen when AWN is set to run at startup. If I disable that and wait until everything else is loaded and then open AWN manually, it's fine. (This is what I'm doing for now.) Killing AWN will also solve the problem.

I have the Ubuntu repository version of AWN installed and not an unstable one from another repository, and metacity for compositing. I wanted to test and see if it would work with another compositing manager but I have never been able to get compiz-fusion to work and I don't know of anything else.

So, um... anyone have any ideas?

ETA: Just as a little side note, if I happen to want to keep my nice stable version of AWN instead of something unstable (even if it does have shiny new features), is there any way for me to get the applets package from a repository without problems, preferably in stable form? I've only found references to the applets package in unstable form, in repositories that seem to only carry an unstable version of AWN.

---

### Post by kaitwospirit on 2008-07-17
Bumping thread...

---

