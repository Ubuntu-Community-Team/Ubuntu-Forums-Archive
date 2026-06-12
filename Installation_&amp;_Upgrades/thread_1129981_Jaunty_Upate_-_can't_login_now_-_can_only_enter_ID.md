---
title: "Jaunty Upate - can't login now - can only enter ID"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by doofusoftheday on 2009-04-19
Have been using Jaunty for months now.  No problems.  I update applications every couple of weeks I guess.  Logged on last night and went into update manager and there was a lot of updates available.  I started the update and walked away.  A little while later went into office to check on the update and there was a black screen, and my daughter said "I think I broke the computer."  I am not sure what she did, she couldn't explain.  

Anyhoo, I reboot and get to graphical login screen (I love that pretty 3D ubuntu graphic at the lower right of login screen!) and can enter my ID.  Then it asks for password, I enter it, but the screen for password just stays there and computer does nothing.  Still stuck on that screen an hour later.

I am guessing the update didn't complete or it did complete and broke something.  How do I boot to a command line and re-run update like "sudo apt-get -u dist-upgrade" or something like that to fix this?

---

### Post by doofusoftheday on 2009-04-19
Okay, now remember about grub menu on bootup.  The current kernel that won't work is 9.04 kernel 2.6.28-11-generic  I selected the 2.6.28-9 in recovery mode and selected option to fix software package installs, or clean up SW installs, or whatever it said.  Then booted to 2.6.28-9 normal and it worked fine.  I tried again to go to 2.6.28-11, and both recovery mode and normal mode from grub and it dies.  At least in recovery mode it gives a clue when I took option to fix SW packages.  It said:

Gave up waiting for root device
ALERT!  /dev/disk/by-uuid/xxxxxxxxxxxxxxxxxxxxxxxxxx does not exist

I added the xxxxx as I didn't want to write down a few dozen characters.  Any idea on how to fix?  Some kind of disk cleanup?

---

