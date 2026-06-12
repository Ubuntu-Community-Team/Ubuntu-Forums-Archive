---
title: "Problems installing"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by Warren on 2005-12-31
The install from the CD went just fine until it had to restart and do some things with the files it put on the hard drive.  Unfortunately, I wasn't watching it constantly to find out precisely when it gave these errors.

While it still had a progress bar for something, it gave this error:

[4297379.5880000]hda: drive not ready for command

After that, though, it still kept going, but I don't know for how long.  Now there is no progress bar anymore, and it's been doing this:

/bin/sh: /usr/sbin/termwrap: Input/output error
/bin/sh: /usr/sbin/termwrap: Success

It does that ten times, then does this:

* Id "1" respawning too fast: disabled for 5 minutes

It's been doing this for a while now.  After one of those sequences, it gave this error:

[4299005.367000] EXT3-fs error (device hda2): ext3_get_inode_loc: unable to read inode block - inode=1128293, block=2260997

As far as I know, it only did that one once.  I also don't know if it has given any other errors while I wasn't watching it.

I use an HP pavilion ze4400 laptop with windows XP on the first partition and trying to install this on the second.  Does anyone know what the problem could be?

---

### Post by belikralj on 2006-04-02
I'm a newb my self and I'm not exactly sure what the problem is but in my experience input/output errors are usually due to hardware faults related to the drive the motherboard or the connection between the two. Though I'm not saying that that is the problem for sure it is defenitely a possibility, a very likely possibility. Having your data backed up may be a good idea right about now in case I am right and it is the hard drive. You may want to try some diagnostics software to test the partitions on that drive though I can't really reccomend any myself since I usually just ask my mates what to do in these situations. Therre are other threads on that last error you entered, I can't remember what thread it was but you may want to search for it. :-k 

Sorry I couldn't help, I hope some of the other smart guys here will give you more a more concrete solution and not just possible causes. :-| 

good luck!  :)

---

### Post by Sef on 2006-04-02
Try a Live CD and see if it boots up ok.  If it does then maybe u have a bad cd.  If not, likely to be a hardware problem.

---

