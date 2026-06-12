---
title: "Firefox 3.0.10 Blank Screen after upgrade to Ubuntu 9.04"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by nm4m on 2009-05-01
Performed the upgrade tonight.  Everything else seems to have gone fine so far.  I am posting this via Opera that was installed before the upgrade.

When I open Firefox, I just get a blank screen.  I have rebooted, did a sudo chown -R user:user in the .mozilla directory, I removed my .mozilla directory, used synaptic to uninstall and install firefox, removed flashplugin.  No change.

I start firefox in a terminal, no errors

I start firefox -safe-mode, it starts in safe mode, but screen is still blank. Cannot make any changes.

I saw bug reports, but no fix that has worked for me.  Can't find the bug report now.  Just like I found a thread about this on these forums, and can no longer find that.  Out of ideas, so I'm posting.

Dave 
NM4M

---

### Post by nm4m on 2009-05-05
Have notes on a couple of other threads, but no luck so far.  Found this bug, but do not yet see any solutions that work for me.

[https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/360923](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/360923)

Dave 
NM4m

---

### Post by netwarriorwy on 2009-05-05
> **nm4m said:**
> Performed the upgrade tonight.  Everything else seems to have gone fine so far

I prefer to backup everything and perform a fresh install. Btw after I did a fresh install of Jaunty I updated and now I'm using firefox 3.0.10 with no problems.

---

### Post by nm4m on 2009-05-05
I agree, there is value to that.  I keep /home on a seperate drive, and then just mount it.  The last fresh install I did with Ubuntu, made the partitioning activity more complicated than I liked because of this.  That is looking like my only other option though.  But with my luck, I will go through that and still have the same problems.  Hopefully not.  Not looking forward to getting all the extra stuff working again, that I usually get going.

Dave
NM4M

---

