---
title: "probably a dumb question but..."
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by tpl on 2008-12-18
This morning Ubuntu 8.10 informed me it had 51 updates. As usual I accepted these and they all appeared to install correctly.
After a reboot I notice that firefox will no longer play certain videos and work in some websites that have video content... not all... Youtube is fine. [www.bnn.ca](www.bnn.ca) is not.  I tried disabling the Ubuntu Firefox mods and so on.  I tried disabling Flash and then was asked by the BNN site to download it. I did so and the Gdebi installer refused to install it saying I had a more recent one.

So my question is.  How do I revert to a point just before installing the updates.   I'd like to try doing this and then try installing them in groups, CUPS for instance probably has no bearing on my problem.

---

### Post by Mark Phelps on 2008-12-18
As far as I know, there's no simple way to "rollback" a set of updates -- primarily because of the package interdependencies. Meaning, that if you rollback one package, you'll have to roll back some or all of the dependencies, and do the same for each of their dependencies, and so on, and so on. If someone else knows how to do this, I'd be GLAD to hear that as I've wanted to do this several times myself.  

My solution, is to use the PING (Partimage Is Not Ghost) product to image off my installation before making a big set of updates. That way, if something get's hosed big time, I can do a restore to get my prior version back.  The backoff, and subsequent restore, take less than 15 minutes each.

If you're interested, PING can be found at [www.windowsdream.com](www.windowsdream.com).  It's free (of course).

---

