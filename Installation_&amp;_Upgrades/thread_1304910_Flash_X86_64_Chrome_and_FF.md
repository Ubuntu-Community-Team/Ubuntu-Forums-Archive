---
title: "Flash X86_64 Chrome and FF"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by zalberico on 2009-10-29
Alright, for the first time ever I had flash working for everything using ubuntu 9.04(64 bit).  Now I've upgraded to 9.10 and flash is terrible. I heard they're using 32 bit flash in a wrapper?  Has anyone else had success getting 64 bit flash functioning in chrome and FF the way it used to in Jaunty.

I found this forum post:
[http://ubuntuforums.org/showthread.php?t=1241313](http://ubuntuforums.org/showthread.php?t=1241313)

Which succeeded in having flash crash ff instantly upon loading any flash page, while doing nothing for chrome.

If anyone has had any success getting flash back to the functionality it was in 9.04 or has any information of whatever was changed to break it that'd be great.  

Thanks.

---

### Post by zalberico on 2009-10-29
bump

---

### Post by sliketymo on 2009-10-29
> **zman14321 said:**
> Alright, for the first time ever I had flash working for everything using ubuntu 9.04(64 bit).  Now I've upgraded to 9.10 and flash is terrible. I heard they're using 32 bit flash in a wrapper?  Has anyone else had success getting 64 bit flash functioning in chrome and FF the way it used to in Jaunty.

I found this forum post:
[http://ubuntuforums.org/showthread.php?t=1241313](http://ubuntuforums.org/showthread.php?t=1241313)

Which succeeded in having flash crash ff instantly upon loading any flash page, while doing nothing for chrome.

If anyone has had any success getting flash back to the functionality it was in 9.04 or has any information of whatever was changed to break it that'd be great.  

Thanks.
Check out the thread for 64bit flash in this forum?

---

### Post by zalberico on 2009-10-29
I already did that (which is why I posted it and why I said that it didn't work).

---

### Post by zalberico on 2009-10-30
I went back to 64 bit jaunty where flash actually worked.  I checked the /usr/lib/mozilla/plugins folder here and see there is a 'flashplugin-alternative.so'.  If anyone tries copying that file into the directory in karmic and it works, let me know.

---

### Post by oldos2er on 2009-10-30
For flash in Chrome (browser), copy libflashplayer.so to /usr/lib/chromium-browser/plugins, then start Chrome with the command **chromium-browser --enable-plugins **

---

