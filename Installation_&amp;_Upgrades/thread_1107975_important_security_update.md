---
title: "important security update"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by rdumas on 2009-03-27
I just got the red arrow for the update manager.  I was an important security update.  When I clicked on the install, I got a warning that the update was not certified.  Is this serious?  What should I do?
:confused:

---

### Post by wkulecz on 2009-03-27
I've had this problem recently.  I certainly wouldn't install it just in case the repo has been hacked.

In my case it seems to be a bug in Update manager.

I appear to have fixed it with:
sudo apt-get update
sudo apt-get upgrade

There was an update to Update Manager on 8.04 recently, so far the issue has not come back.

Here is the discussion where I found the apparent fix:
[http://ubuntuforums.org/showthread.php?t=1100456](http://ubuntuforums.org/showthread.php?t=1100456)

Here is where I fist reported the issue:
[http://ubuntuforums.org/showthread.php?t=973292](http://ubuntuforums.org/showthread.php?t=973292)

--wally.

---

