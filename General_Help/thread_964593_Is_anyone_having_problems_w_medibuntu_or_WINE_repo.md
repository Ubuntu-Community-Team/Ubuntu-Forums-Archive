---
title: "Is anyone having problems w/ medibuntu or WINE repos?"
date: 2008-10-31
forum: General Help
---

### Post by shaggy999 on 2008-10-31
I use apt-mirror on hardy and I'm trying to mirror both the hardy and intrepid dists of the medibuntu and WINE repos, but for some reason it just seems to stall on one of these guys when downloading the index files. I left my machine hanging for over 4 hours and nothing happens! Strange thing is I seem to be able to do a sudo apt-get update, which points to the exact same files (although I am only able to try this in hardy at the moment, I do not have an intrepid machine going).

---

### Post by Laibcoms on 2008-10-31
Under hardy, yes.  Under Intrepid all seems fine, except for medibuntu's key, it just won't get accepted by Intrepid for some reason.

---

### Post by lifestream on 2008-10-31
/me raises hand.
All day.
Got no answers for you thought, just wanted to tell you you're not alone.

---

### Post by shaggy999 on 2008-10-31
Ok, at least I know it's not me. I guess I'll just comment out those repos for now. Thx!

---

### Post by Relysis on 2008-10-31
Leave out those repositories in the installation.  You can just add them back after the restart.  The applications may not be installed properly upon restart, but your configurations (~/.whatever) should still be there.  Be sure to add the repos back after restart.  If anything is no longer installed or not installed properly, make a little trip to synaptic and intall/reinstall.  A little bit of a pain when trying to install, but a quick and easy one to fix.

Edit: I missed that you were not upgrading to Intrepid.  Medibuntu 'goes down' every once in a while.  Just comment it out for a bit when you do updates.  It should be back soon.

---

### Post by kostkon on 2008-10-31
The Wine repo is down for the last two days, indeed...

---

### Post by keep-on-smiling on 2008-10-31
hi

medibuntu cannot be verified atm here either...

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

you are not alone...

---

