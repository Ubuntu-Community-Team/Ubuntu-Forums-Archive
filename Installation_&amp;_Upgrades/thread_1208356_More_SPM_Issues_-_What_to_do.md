---
title: "More SPM Issues - What to do?"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by Bill Zimmerly on 2009-07-09
(SPM = "Synaptic Package Manager")

I just don't understand what the creators / maintainers want us to do when they post error messages in a dialog like this...

/---
| An error occurred
| The following details are provided:
| E: /var/cache/apt/archives/mono-devel_2.0.1-4_all.deb: trying 
| to overwrite `/usr/bin/csc', which is also in package chicken-bin
\---

What next? I tried to "Completely Remove" mono-devel, chicken, etc. but they all persist in staying and giving me this inane error message! What should I do to fix this situation?

---

### Post by Bill Zimmerly on 2009-07-09
Well, as usual I stumbled onto the solution.

When starting SPM, it always gives me a dialog box asking me to fix "Broken" packages with the "broken filter". I always did this, and it always would say that the fixes worked.

Ha!

This time, I ignored the broken filter fix and just removed the "chicken-bin" package and it worked! Then, I "fixed" the Broken package.

That solved the dependency problem and now SPM runs just fine with no subsequent error messages. :guitar:

---

### Post by directhex on 2009-07-09
There's an open bug on the chicken-bin thing, but it's unlikely to be fixed in time for Karmic

---

