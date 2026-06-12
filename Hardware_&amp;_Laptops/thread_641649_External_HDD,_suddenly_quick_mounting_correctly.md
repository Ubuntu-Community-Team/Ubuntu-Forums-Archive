---
title: "External HDD, suddenly quick mounting correctly"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by shane2peru on 2007-12-15
Here is the situation.  I have 2 external hdd, one is a small one (laptop size), that I always use, I rsync my home directory to it.  It is great for mirroring my data to it.  No problems with it.  I have another large hdd, that I have always used to backup my data to.  I have automatic backup processes that zip my system to a tar file and then at my convenience I move it to my ext hdd (big IDE WD hdd).  I only turn it on about once or twice a month dump my data to it, umount it and turn it off.  Sooooo, I turned it on (like I have done since my Dapper days)  went to dump my data to it, and it took extremely long time, and ended in an error saying it was a write only system.  So being the slow stubborn learner that I am, I tried this about 3 more times, with Nautilus, Gnome Commander, and the Command Line, only to find the same types of errors.  I rebooted, and re-attempted and still get the same error.  Now I'm thinking I have a problem.  How can I check my external hdd to see if it is ok?  Or is this a Gutsy issue? (I'm using Gutsy up to date, also I have used this before in Gutsy without a problem.)  When I first turn it on, it seems to mount fine, and give me write permission, but trying to transfer a 1.5GB file to it, crashes things, and brings my system to an extremely slooooow crawling turtle state.  Any ideas would be greatly appreciated!  Thank you in advance!

Shane

---

### Post by shane2peru on 2007-12-15
SOLVED!  Ok, I started pooking around to see what was going on, and googling things.  After several failed attempts at using fsck on the command line with this drive, I opened up gparted (I love that program)  and low and behold there was the option to check the drive!  Wonderful, checked the drive, and it had errors, it fixed them, and now I copied my info over without a problem!  Sorry, I guess I'm getting too linux savvy (or google savvy) to be posting questions.  Hope this will help someone else.

Shane

---

