---
title: "Problem while upgrading, need to recover files!"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by KFwLsKvVAs on 2009-11-03
Hello all,

So...I was upgrading my girlfriend's computer (hp dv2000) from 9.04 to 9.10.  Her computer has a tendency to arbitrarily shut down (not just power off and black screen instantly, it actually kills everything and shuts down).  So during the upgrade, it shut down (after all packages had downloaded, it was during the actual installation).  Now when I turn on her computer it says 

"One or more of the mounts listed in /etc/fstab cannot be mounted:
(ESC for recovery shell)

/: waiting for /dev/disk/by-uuid/5dcacd3e-206b-48a5-b173-50e0373d4cc8
/tmp: waiting for (null)
swap: waiting for UUID=a5d82d5b-a130-4811=a559-d17af98a2d5

mountall: cancelled
init: mountall main process (796) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@(none):~#"

So I dont know what to do from here.  If I can, I want to fix it so I can boot back up into 9.04 and finish the upgrade.  

If I can't fix it and I need to reinstall from scratch, there is a lot of data on the hard drive that I need to recover, and I also don't exactly know how to do that.  So...............

Please somebody help me with this, there's school work and things on that computer that I really need to save.

---

### Post by zika on 2009-11-03
> **murderape said:**
> Hello all,

So...I was upgrading my girlfriend's computer (hp dv2000) from 9.04 to 9.10.  Her computer has a tendency to arbitrarily shut down (not just power off and black screen instantly, it actually kills everything and shuts down).  So during the upgrade, it shut down (after all packages had downloaded, it was during the actual installation).  Now when I turn on her computer it says 

"One or more of the mounts listed in /etc/fstab cannot be mounted:
(ESC for recovery shell)

/: waiting for /dev/disk/by-uuid/5dcacd3e-206b-48a5-b173-50e0373d4cc8
/tmp: waiting for (null)
swap: waiting for UUID=a5d82d5b-a130-4811=a559-d17af98a2d5

mountall: cancelled
init: mountall main process (796) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@(none):~#"

So I dont know what to do from here.  If I can, I want to fix it so I can boot back up into 9.04 and finish the upgrade.  

If I can't fix it and I need to reinstall from scratch, there is a lot of data on the hard drive that I need to recover, and I also don't exactly know how to do that.  So...............

Please somebody help me with this, there's school work and things on that computer that I really need to save.Boot with LiveCd and, from there, copy all the important data to DVD or HDD and do reinstall. But, after getting all the data off that box, check what is the real reason for it to shut-down intermittently because that will ruin any data You put back on it. On ext4 specially.

---

### Post by mikewhatever on 2009-11-03
I think your best shot is to boot from the live cd and copy all the data to an external storage. Then reinstall.

---

### Post by akelsall on 2009-11-03
I agree with Zitka. Get all your important data backed up and figure out why the PC keeps shutting down before you even think about upgrading. 

Once that problem is resolved, try the upgrade again. If you still have issues, post your error messages here again.

The shutdown issue might be power-supply related. How old is the system?

---

### Post by KFwLsKvVAs on 2009-11-03
Alright I am trying to boot from a livecd now.  




Does anybody know why it would be shutting down like that?  I've taken it in to best buy (crummy geek squad didnt figure out a thing, I ended up finding out that this particular model had some problem in the bios that needed to be fixed by the manufacturer, but they still charged me $35), had it sent to hp, who flashed everything, fixed the bios and sent it back with vista on it.  I got rid of vista, installed 9.04, and it was all fine for a while but it started doing it again recently.  I'm honestly at a loss, it runs fine, gives no error messages, doesn't seem to heat up too much (and i have a cooling pad), but it still does it.  

@zika:
Why would ext4 screw up any more than ext3 when it shuts down?

anybody else have a hp dv2000 that shuts down like this?

---

### Post by KFwLsKvVAs on 2009-11-03
I'd say it's about 2 years old.  
I just had it sent to hp about...2 or 3 months ago.  they replaced some things, updated the bios (i dont recall what they replaced and i have long since lost the paper detailing everything).  When I've taken it apart in the past, there are no burns or anything on any of the cards (at least none that I have seen).  

See the thing is that whenever it's booted into windows, it doesnt experience this whole shut down problem.  Which is strange.  

I think I'm going to try to back up all the data and just reinstall from scratch.  Maybe a fresh install would fix this.

---

