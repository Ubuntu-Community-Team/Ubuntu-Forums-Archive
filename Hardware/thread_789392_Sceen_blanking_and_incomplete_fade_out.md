---
title: "Sceen blanking and incomplete fade out"
date: 2008-05-10
forum: Hardware
---

### Post by unbutu on 2008-05-10
Other people seem to be having screen blanking and related issues, but it's not clear whether the underlying problem is the same as mine.  So I thought I'd post a description of my problem, since there is a little history to it. I'm using 64-bit ubuntu, with an Intel GM965/GL960 Graphics Controller.

Back when I used Gutsy, I had a problem getting a widescreen resolution, and I had accompanying screen-blanking problems, and an incomplete screen fade out (more on this below).  In order to solve it, I had to install 915resolution, even though, supposedly, it was obsolete.  Details can be found on this thread: 

[http://ubuntuforums.org/showthread.php?t=709508](http://ubuntuforums.org/showthread.php?t=709508)

This solution was adequate, but not great, since I was unable to use compiz fusion.  But it did give me the right resolution, and eliminated the screen blanking and funny fade out.

I did a clean install of Hardy, and the widescreen resolution problem was gone.  But, sadly, sometimes when I boot up, switch users, or log out, the screen still goes blank.  The frequency of the screen blanking is lower, so it's not impossible to use, but it's still frequent enough to be annoying.  And the other symptom of my previous problem, the incomplete fade out, persists: when I press the log-off/switch-user/shut-down button, for example, only the top-left 1024x640 pixels (of 1440x900) actually fade out.  I've attached a picture.  The incomplete fade out occurs even when I run Hardy from the live cd.

Has anyone had these problems?  I figure the incomplete fade out might distinguish my problem from similar ones.  Obviously, if anyone has figured out a way to get around it, I would much appreciate hearing about it.

---

### Post by unbutu on 2008-05-13
I installed today's updates, with some hope since xserver-xorg-video-intel was one of them.  Sadly, even after rebooting, the screen blanking and incomplete fade out problems remain.

Anybody have any idea what's going on?  I can't believe I'm the only one with this problem, especially since similar symptoms (at least) were present with Gutsy.  Should I try the 915resolution solution again?

---

### Post by robertyou on 2008-10-15
Similar problem has been bothering me too. When I click the Log off/Switch/Shutdown... button, the fade-out effect sometimes lags horribly, but I've never got a blank box as in your sceenshot..

I just assume it's a 2D performance issue of nvidia driver.

---

