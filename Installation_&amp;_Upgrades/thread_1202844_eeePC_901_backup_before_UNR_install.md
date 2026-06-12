---
title: "eeePC 901 backup before UNR install"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by lucast on 2009-07-02
Hi,

I have an eeePC 901 with the standard Xandros install (easy mode).  One feature I like about it, is the F9 option at boot time to restore to factory default.

I would like to experiment with UNR, but first I would like to backup Xandros  including the F9 feature.  I have found a page on the eee Forums on how to backup but it dosent mention if this feature will still be available when I restore it after messing around with UNR.  [http://wiki.eeeuser.com/backup_procedure_for_eee_with_xandros](http://wiki.eeeuser.com/backup_procedure_for_eee_with_xandros)

Also is it possible to have this feature with UNR installed?  F9 to resture UNR back to its default install.

Any advice would be much appreciated.

Tim

---

### Post by quixote on 2009-07-03
I can't answer your question about retaining the F9 restore functionality in ubuntu, but for a backup method there's an easy answer.  [Clonezilla]("http://clonezilla.org/") can mirror your drive to an attached USB drive, or over a network to a hard drive elsewhere.  It's just a complete copy.  You can browse directories normally and find single files if you want.  Or you can restore the whole thing back to your eee and it'll look like ubuntu had never been there.

(You'd lose any new stuff you'd put on while you were experimenting with Ubuntu, of course, if you mirrored the old drive contents back to your eee.)

---

### Post by lucast on 2009-07-06
Thanks for the advice.  Do you know if I clone the drive with clonezilla and restore the drive at a later date the F9 restore will still work with Xandros?

---

### Post by quixote on 2009-07-06
I've never done that exact procedure myself, so I can't guarantee that the F9 restore will work as it should.  But what you're doing is making an exact copy of your whole hard drive.  On the occasions when I've done that, the restored hard drive functions exactly as it did at the time when the clone was made.  So, the short answer is, Yes, F9 should work the same way it did when you cloned it.  But all I can say is "should."  It's necessarily one of these proceed-at-your-own-risk things.

One point: the F9 restore function may depend on a separate partition on the hard drive.  Make sure you clone the whole *disk*, if it has more than one partition.

---

