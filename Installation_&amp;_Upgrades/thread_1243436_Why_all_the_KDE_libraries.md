---
title: "Why all the KDE libraries?"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by ProfBib on 2009-08-18
I am not sure why there are so many KDE libraries included in todays (8/18/2009) Ubuntu (yes, I said Ubuntu, not Kubuntu) Jaunty updates/upgrades when I currently don't have any KDE apps or dependencies on my system?  What gives?

---

### Post by mcduck on 2009-08-18
Well, if you get updates for those libraries you must have installed them at some point, for some reason or other..

Perhaps you've tried some KDE app in the past, then removed it but left some of it's dependencies on your system?

(I didn't get any KDE library updates..)

---

### Post by Mighty_Joe on 2009-08-18
Mark the packages for removal in Synaptic and you'll get a list of dependencies.  You probably have a dependency you don't know about (K3B, for instance).

---

### Post by ProfBib on 2009-08-18
Thanks for the suggestions, but neither of these are true in my case.  I actually use apt-get autoremove on a regular basis from the command line to make sure that my system is as lean & mean as possible.

Furthermore, when I search for these same packages in Synaptic, they come up as not currently installed on my system.

Please note that, in the Update Manager, they are not marked as "updates" but instead appear under the header "Distribution Upgrades."

Any further thoughts anyone?

---

### Post by ProfBib on 2009-08-18
OK, so I don't get these impromptu "distribution upgrades" on my office machine.  I just ran in to check.  However, as I mentioned, my home machine currently does not have any of them installed (when searched in Synaptic), but the updated manager is trying to apply an upgrade.  Aaargh.  I don't understand...

Scooby Doo, where are you?

I'll let everyone know what I figure out later tonight...

[http://www.flickr.com/photos/bibbee/3835111459/](http://www.flickr.com/photos/bibbee/3835111459/)
[IMG]http://www.flickr.com/photos/bibbee/3835111459/[/IMG]

---

### Post by mcduck on 2009-08-19
The you must have some program installed that didn't depend on those packages at the time you installed it, but in the latest version started using them.

The update manager will only update package you have installed, but can also add new packages if updating some of your existing ones requires that.

---

### Post by ProfBib on 2009-08-19
Hmm.  Thanks - I didn't think about that possibility.  I'm going to have a go at removing some possible culprits now and I'll let you know how it goes.  Thanks for your help so far!

Best,
Evan

---

### Post by ProfBib on 2009-08-19
Got it!  The "culprit" is Autokey, and it's exactly as MCDUCK said: I can't believe that I didn't think about that myself.  It's just that, in the four years I've been using Linux, I've never had a simple package update add so many heretofore uninstalled programs.  I may just have to hold back and use the old version of the program, because it seems a bit outrageous to download an additional 60mb of dependencies for one little utility, albeit one that I find quite useful!

---

### Post by mcduck on 2009-08-19
> **ProfBib said:**
> Got it!  The "culprit" is Autokey, and it's exactly as MCDUCK said: I can't believe that I didn't think about that myself.  It's just that, in the four years I've been using Linux, I've never had a simple package update add so many heretofore uninstalled programs.  I may just have to hold back and use the old version of the program, because it seems a bit outrageous to download an additional 60mb of dependencies for one little utility, albeit one that I find quite useful!

great that you got it sorted out. And now I'll know to avoid that program as well.. :)

---

