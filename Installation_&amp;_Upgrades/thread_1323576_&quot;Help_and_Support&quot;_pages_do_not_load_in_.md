---
title: "&quot;Help and Support&quot; pages do not load in 9.10"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Kirk M on 2009-11-11
The "Help and Support" app does not load any help file at all. Upon initially bringing up "Help and Support" or clicking the "Home" button brings up this alert box:

 [INDENT]**Unable to load page**

The requested URI "file:///fakefile#index" is invalid[/INDENT]

If I enter a search term I get this:

         [INDENT]**Unable to load page**

The requested URI "file:///fakefile#results" is invalid[/INDENT]

I don't use help and support that often so it may have had a problem previous to today's update 11/11/09.

I installed 9.10 the day of it's release and have been updating regularly since. I do not have Karmic backports or Karmic proposed checked. I have added the repositories for Mozilla, Gnome Shell and ClamAV.

Is there anyway I can fix "Help and Support" so it loads properly again?

---

### Post by matthewn on 2009-11-25
Do you happen to have Firefox 3.6 installed? I'm having the same problem, and [this thread]("http://ubuntuforums.org/showthread.php?t=1337616") indicates that xulrunner 1.9.2 is the problem. When I removed it (along with Firefox 3.6), "Help and Support" returned to normal. There's gotta be a way to get these packages to coexist, though...

---

### Post by Kirk M on 2009-11-25
> **matthewn said:**
> Do you happen to have Firefox 3.6 installed? I'm having the same problem, and [this thread]("http://ubuntuforums.org/showthread.php?t=1337616") indicates that xulrunner 1.9.2 is the problem. When I removed it (along with Firefox 3.6), "Help and Support" returned to normal. There's gotta be a way to get these packages to coexist, though...

Thanks for the reply and yes, I was testing the Firefox 3.6 nightly builds at the time. I removed Firefox 3.6 and XULrunner 1.9.2 and Help and Support started working again. For what it's worth I did two things today and now "Help and Support" is working again with XULrunner 1.9.2 installed. 

I reinstalled Firefox 3.6, Firefox 3.6 Branding, Firefox 3.6 Gnome support and XULrunner 1.9.2 (I had already added the respective repository previously so I could get regular updates to Thunderbird 3.0 builds) and then used the Update Manager to bring everything up to date. Then, using the Firefox 3.6 Preferences/Advanced tab, I set it to be the default browser (it wasn't). Now "Help and Support' is working correctly. 

I don't know the exact reason why this solved the problem yet except that there may have been a bug in the previous builds of XULrunner 1.9.2 that was fixed in today's update. Either way, I have Help and Support back. :cool:

---

