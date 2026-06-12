---
title: "Firefox 3.0.5 upgrade crashing"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by smotsie on 2008-12-18
Hi guys

I got an adept upgrade alert this morning for Firefox, which I allowed to go ahead. FF became very unstable, locking completely on many occasions - afaik it was whenever I typed stuff into the address field or the google search in the nav toolbar. The upgrade also installed a gross replacement icon for FF. I ended up removing it completely and installing a raw version straight from getfirefox.com so I could get on with my work.

Another weird symptom was that "Help About..." resulted in a tiny empty window, as did "Bookmarks | Organise...". Something seems seriously broken in this latest update.

Has anyone else found this yet? I tried apt-get install firefox=3.0.4 but the versioning only seems to go down to 3.0, not the sub-version... also 3.0.5 from Mozilla is running fine.

I hope this is fixed soon, I prefer to stay with repository versions wherever I can so I get the latest security fixes, but not when they stop productive work!

---

### Post by black3ug on 2008-12-18
Hi! Using Ubuntu Intrepid here and I experienced similar firefox "oddities" as you did right after I upgraded. What I did was do a "killall firefox" on a terminal because I thought the last firefox session may not have unloaded off RAM yet which led to weird firefox issues after update (was using firefox when I installed updates). I gave it a few minutes (around 10) and, when I started it again, it was doing great!

---

### Post by SuperSonic4 on 2008-12-18
My firefox is working perfectly after last night's upgrade

```
Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.0.5) Gecko/2008121622 Ubuntu/8.10 (intrepid) Firefox/3.0.5
```

---

### Post by fiskeben on 2008-12-18
I have the same problem. Firefox dies either instantaneously or after some period of time. I have not been able to test it enough to find a pattern og any pointers to what causes the crashing (for instance Flash or other plugins).

I tried to run firefox from a terminal to get some output, but all i get is "Aborted".

---

### Post by smotsie on 2008-12-18
> **black3ug said:**
> Hi! Using Ubuntu Intrepid here and I experienced similar firefox "oddities" as you did right after I upgraded. What I did was do a "killall firefox" on a terminal because I thought the last firefox session may not have unloaded off RAM yet which led to weird firefox issues after update (was using firefox when I installed updates). I gave it a few minutes (around 10) and, when I started it again, it was doing great!

Now that is weird. I did killall firefox then ps -ef | grep firefox and it showed a couple of firefox-bin processes running. I killed them too (killall firefox-bin) and re-installed the Kubuntu version. Icons back to normal and search and address bar working as expected.

When the upgrade occurred it prompted that I would need to restart Firefox, which I did using the normal top-right X to close and then start from K menu. It would seem that didn't purge all processes for the old FF and it was that which caused the instability. Ho hum. At least with Ubuntu I could get another copy of the browser and install in a different way. Try that when Windoze IE upgrade causes a problem! (oh, yeah... install FF on Windoze too!)

So upshot is if you get weirdness, try a cold boot or commands above before anything else.

---

### Post by Mark Phelps on 2008-12-18
I got error messages in FF as well last night.  I rebooted a couple of times, got an popup indicating that FF needed to be restarted.  Did that a couple of times -- and everything is OK now.

---

### Post by fiskeben on 2008-12-19
I just tried what is described here but it didn't help much. Firefox opens, runs for everything between a second and a few minutes, then dies.
I have tried to remove my profile to see if the problem is a misbehaving extension of some sort but that didn't help either.
Now I'm running the "standard" version from getfirefox.com (until I get to solve this one).

---

### Post by dBuster on 2008-12-19
Okay so far so good the killall worked for me.  FF seems for the moment to be stable.  No crashes now and I have been in it for about 45 minutes without a crash.  Thanks for the killall post and to check for the bins as well...

---

### Post by SteveDee on 2008-12-19
I don't appear to have any instability problems with FireFox 3.0.5. My problem is I keep getting the "Your browser has been updated and needs to be restarted" banner. Needless to say I've clicked the "Restart" button a few times but it keeps coming back.

Anyone had this problem and found a fix? (don't tell me to re-install!).

---

### Post by fiskeben on 2008-12-19
The solution in this thread worked for me (at least so far...): [http://ubuntuforums.org/showthread.php?t=1015598]("http://ubuntuforums.org/showthread.php?t=1015598").

---

### Post by fiskeben on 2008-12-19
> **fiskeben said:**
> The solution in this thread worked for me (at least so far...): [http://ubuntuforums.org/showthread.php?t=1015598]("http://ubuntuforums.org/showthread.php?t=1015598").

... not :-(

---

### Post by skeetre on 2008-12-19
The bottom 2 posts in this thread (at least as of this posting) have 2 possible solutions. One with reinstalling and one without reinstalling.

[https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/270303]("https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/270303")

I'm at work researching the same issue and found this, but I can't test to verify until I get off.

---

### Post by SteveDee on 2008-12-20
> **SteveDee said:**
> ...My problem is I keep getting the "Your browser has been updated and needs to be restarted" banner...

Well, I didn't get a chance to fix this. When I switched on this afternoon it had fixed its self.

From reading other posts it looks like people have suffered this problem from at least 3.0.2 onwards, but don't necessarily continue to have this problem with every release.

---

### Post by skeetre on 2008-12-21
On one install it fixed itself by the time I got home. When I ran the fix on my other box, it worked great.

---

