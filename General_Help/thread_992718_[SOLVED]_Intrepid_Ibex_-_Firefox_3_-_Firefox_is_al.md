---
title: "[SOLVED] Intrepid Ibex - Firefox 3 - Firefox is already running error"
date: 2008-11-25
forum: General Help
---

### Post by siafulinux on 2008-11-25
Hi all

I came home from work tonight to find that Firefox would not load. I kept getting the error "Firefox is already running...". I checked, it wasn't! I also attempted a "killall firefox", "killall firefox-bin" and also a "ps aux | grep firefox" all to no avail.

I then logged into the other account (only other) to see if perhaps it was stuck there for some reason - nope. 

I navigated to /home/[username]/.mozilla/firefox and found out that if I edited profiles.ini and changed "IsRelative" to "0", firefox would load, but without my previous bookmarks or customisations - which is no biggie, but still. 

I also had changed to "StartWithLastProfile" to "0" as well, but that didn't really seem to be the problem as I did this a few times and IsRelative seemed to do it for me.

Does anyone perhaps have an explanation on what this is exactly or should I go ahead and submit a bug? 

Hopefully this work around will help someone. You can find your old bookmarks under the profile directory, which is listed in your profiles.ini under Path and, unless you have multiples, should be the only randomly(?) generated directory name.

Thanks everyone
JC

---

### Post by CatKiller on 2008-11-25
> **siafulinux said:**
> I came home from work tonight to find that Firefox would not load. I kept getting the error "Firefox is already running...". I checked, it wasn't! I also attempted a "killall firefox", "killall firefox-bin" and also a "ps aux | grep firefox" all to no avail.

This behaviour is controlled with a simple lock file. If Firefox really isn't running, and you seem to have ensured that it isn't, you can delete the ~/.mozilla/firefox/*profile*.default/lock file. Firefox should then start normally.

---

### Post by siafulinux on 2008-11-25
> **CatKiller said:**
> This behaviour is controlled with a simple lock file. If Firefox really isn't running, and you seem to have ensured that it isn't, you can delete the ~/.mozilla/firefox/*profile*.default/lock file. Firefox should then start normally.


Thanks CatKiller 

The thing is, is that I had in fact deleted that file as well as the .parentlock (or something along those lines) but Firefox was still not loading.

---

### Post by siafulinux on 2008-11-30
Okay so I forgot to mention that I had mounted my /home directory on a fileserver, but never did the /usr. This may have been my problem. I just did so and hope that this solves the issue.

It also, as recently noticed, would do the above mentioned problem when I say logged out of Gnome without closing Firefox first. 

For now I'm going to list this as solved as I think the /usr dir may have been the problem. 

JC

---

### Post by siafulinux on 2008-12-13
So, it's still happening. Seems to be a [bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/73457") though with NFS /home mounts.

**Edit:** Using Firefox 2 I don't seem to be having this problem. So this may have something to do with Firefox 3 and NFS?

**Edit 2:** Nevermind, it just happened again. Ugh! This is aggravating.

---

### Post by siafulinux on 2008-12-14
Okay so the problem is resolved. The issue was NFS but thanks to Matthias in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/73457"), using the "nolock" option to mount the remote /home directory resolves the issue!

Thanks to Matthias!
JC

---

### Post by CatKiller on 2008-12-14
Glad you got it fixed. I had been following your progress, but didn't really have anything to add other than what you'd discovered yourself. Sorry.

---

### Post by siafulinux on 2008-12-14
np, thanks for keeping tabs and offering assistance! 

It was highly frustrating though since browsing and web development are some of the things I do most often.

It was also affecting Transmission, giving the same error that it was already loaded. 

Thanks again
JC

---

