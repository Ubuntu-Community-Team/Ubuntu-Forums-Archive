---
title: "Hard lockup when video file played in Totem"
date: 2008-07-16
forum: General Help
---

### Post by WrathofthePenguin on 2008-07-16
I have been seeing lockups when trying to play a slideshow video I made. I can reproduce the lockup 100% of the time playing this file with Totem. If I open the slideshow with VLC or with Mplayer, I get no lockup.

The logs give me no clue as to what's happening. I wait for a couple of minutes before I restart so I have a clear point at which I know the lockup occurred, but there's nothing that seems to point to a problem.

The lockup seems to occur right as the movie starts to play. The screen goes blank, and the laptop is completely unresponsive.

As I can reproduce this 100% of the time, this is an ideal troubleshooting environment. I'm going to file a bug report, but wanted to see if anybody had any other ideas to see if we can figure out what's happening.

---

### Post by alfalfa31 on 2008-07-16
What video chipset are you using?  It may be an active Xorg bug if it's an ATI...

---

### Post by WrathofthePenguin on 2008-07-16
Should have specified hardware in the original post - sorry.

I have a Dell 700m with integrated Intel 855 chipset for video. The audio controller is a SigmaTel STAC 9750.

---

### Post by WrathofthePenguin on 2008-07-16
For any with the same issue, I've submitted the following:

[https://bugs.launchpad.net/ubuntu/+bug/249189](https://bugs.launchpad.net/ubuntu/+bug/249189)

---

