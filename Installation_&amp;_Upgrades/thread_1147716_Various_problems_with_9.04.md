---
title: "Various problems with 9.04"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by _Smiler_ on 2009-05-03
Hey, ever since installing 9.04 I have experienced some problems. Mostly in firefox -  when I start it up with addons enabled, it brings up tabs for each one (the website of each) The addons are: Google reader, Easy Youtube Video Downloader, Google toolbar, RSE tools, Stumbleupon toolbar, Ubiquity and NoScript. The back button is also disabled. It is not logging any history, despite the option being enabled in preferences. Checkgmail isn't working - whenever I click it from my menu, nothing happens. I've tried using the executable directly, still nothing. Please help!

I'm not sure how to get logs of the problem.

---

### Post by _Smiler_ on 2009-05-03
Oh and I forgot - Google toolbar doesn't work. It literally does nothing, doesn't search, doesn'T sign in, nothing. I've tried to reinstall it.

---

### Post by _Smiler_ on 2009-05-03
I fixed it by creating a new profile - close firefox completely, and run```
firefox -Profilemanager
``` in terminal. I think this was a problem with the new Firefox, not Jaunty.

---

