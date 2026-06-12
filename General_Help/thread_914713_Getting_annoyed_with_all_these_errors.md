---
title: "Getting annoyed with all these errors"
date: 2008-09-09
forum: General Help
---

### Post by Milambar on 2008-09-09
First of all, it started off with a gvim problem, then the firewall went weird on me, I had to keep flushing it..

After a while, I decided to bite the bullet, and reinstall from scratch.

The reinstallation was no problem, but then it wanted to download all the security patches etc.

The system hung on installing an upgraded libpng... After freeing it from that hang, I did sudo apt-get update && sudo apt-get upgrade, to try and complete the updates.

I got told to run dpkg --configure -a, which I duly did

Now, its been sat, for 8hrs on "Setting up capplets-data..."

Doing nothing, just sat... On that.

No status report, no problems.. 

But.. I suspect there IS a problem, it shouldn't stick for 8hrs on "Setting up capplets-data", whatever that is. So basically, I have a feeling, I'm going to need to reinstall... yet again.

Or perhaps theres another solution?

-edit for update-

Ironically
I kept aborting it with ^C, and re-running dpkg....

After 10 attempts, it finally went through. Therefore - Solved

---

