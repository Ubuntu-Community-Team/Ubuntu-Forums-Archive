---
title: "time and date"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by davidmaxwaterman on 2009-09-29
Hi,

I recently installed 9.04, and updated/graded seemingly successfully.

However, it seems I got the wrong timezone, and I can't seem to be able to change it.

I use the 'time and date settings' tool from the 'system' menu. I 'unlock' it, and then select the correct zone. When I do so, the selected zone is changed, but when I close the tool and launch it again, it still says the wrong one.

I've tried rebooting, but it makes no difference.

Note also that the 'configuration' is in manual, so there's no confusion from ntp or anything.

Any ideas?

Max.

---

### Post by MelDJ on 2009-09-29
> **davidmaxwaterman said:**
> Hi,

I recently installed 9.04, and updated/graded seemingly successfully.

However, it seems I got the wrong timezone, and I can't seem to be able to change it.

I use the 'time and date settings' tool from the 'system' menu. I 'unlock' it, and then select the correct zone. When I do so, the selected zone is changed, but when I close the tool and launch it again, it still says the wrong one.

I've tried rebooting, but it makes no difference.

Note also that the 'configuration' is in manual, so there's no confusion from ntp or anything.

Any ideas?

Max.

did you synch the time before exiting?

---

### Post by davidmaxwaterman on 2009-09-29
> **MelDJ said:**
> did you synch the time before exiting?

I'm not sure what you mean by 'sync the time', but I pressed the little 'sync' button...though, again, I'm not sure what it's supposed to be syncing with, since it's set to 'manual'.

Anyway, I did it again, after changing the time zone, and relaunching it shows the same wrong time zone.

Any other ideas?

---

### Post by davidmaxwaterman on 2009-10-02
> **MelDJ said:**
> did you synch the time before exiting?

Did you have any other ideas?

I'm getting this again, even after another complete reinstall (for other reasons).

Max.

---

### Post by slakkie on 2009-10-02
Hi,

[http://www.ubuntuforums.org/showthread.php?t=1277559](http://www.ubuntuforums.org/showthread.php?t=1277559)

---

### Post by davidmaxwaterman on 2009-10-03
> **slakkie said:**
> Hi,

[http://www.ubuntuforums.org/showthread.php?t=1277559](http://www.ubuntuforums.org/showthread.php?t=1277559)

Thanks. I'll see how that goes.

FWIW, I found [some other post]("http://ubuntuforums.org/showthread.php?t=935507") that made me look in /etc/timezone, where the time zone was indeed correct. So it was just the GUI tool that was wrong and making me think the time zone wasn't correct.

However, I've made the changes suggested in the thread you listed, and I hope that'll be the end of it :)

I wonder what'll happen in 9.10 - I hope it's fixed :/

---

