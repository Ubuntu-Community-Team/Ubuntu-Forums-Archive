---
title: "I've Broken Firefox"
date: 2008-11-27
forum: General Help
---

### Post by Zaraphrax on 2008-11-27
This afternoon I tried (and failed) to compile a pre-release version of Firefox. Now, I can't get Firefox 3.0.3 to start. Here is a screenshot of what happens when I launch it from the terminal. Is there anyway to fix this? Good thing I backed up my bookmarks with Foxmarks.....

---

### Post by DJ_Peng on 2008-11-27
Is there a reason you're compiling it rather than using a precompiled build from Mozilla? They offer nightly, and I believe even hourly, builds that you can use if you want to be on the bleeding edge. I used to use the nightly builds with little to no problems other than the normal bugs you get using nightly builds.

---

### Post by linux_tech on 2008-11-27
It may be easiest to reinstall firefox

---

### Post by DJ_Peng on 2008-11-27
True, although I snag the .tar.gz from Mozilla and simply unextract it. Once that's done all you need to do is either make a launcher or edit an existing launcher to point to the ```
firefox
``` file in that folder. While that won't include the tight integration with Ubuntu it will give you the benefits of getting updates faster and being able to use the [Update Channel Selector]("http://www.oxymoronical.com/web/firefox/updatechannel") to snag nightly builds or even snag the Firefox 3.1 test builds. When I was a Firefox tester I always grabbed the nightly builds without any problems (unless the update servers had issues, which happens from time to time). I know there's a script or two around the web that will use Firefox's servers to install Firefox, but I dont use them myself.

---

### Post by Zaraphrax on 2008-11-27
> **linux_tech said:**
> It may be easiest to reinstall firefox

How would one go about doing that?

I went into Synaptic package manager and removed everything related to Firefox, then reinstalled all the packages. Same deal.

Also - Say I was wanting to try out Minefield, which package should I download?

---

### Post by DJ_Peng on 2008-11-27
I'm not sure what build Mozilla is calling Minefield now, but I saw recently that they are splitting a 3.1 branch off of the trunk soon (if it hasn't happened already). You can get more info in the Firefox Builds forum at Mozillazine (link in my sig).

---

