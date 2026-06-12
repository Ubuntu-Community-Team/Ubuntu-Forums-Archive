---
title: "Partioning and mounting point suggestions..."
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by GackY2K on 2009-04-28
This is a call out to all you Ubuntu pro's.  I've been playing with Ubuntu for a bit, off and on dual booting and am just about comfortable enough to make the complete break from MS and go only Ubuntu. I am preparing a new disk for just that purpose and want some expert/experienced suggestions on how to best partition/format and mount these partitions for optimal security, ease in restoration...etc.

HD:  250 gig SATA 

I have been reading and getting a widely varied opinion on various partition sizes and mounting points to use.  I was only using 10Gigs for "/" and setting the rest to "/home" and using ext3 format, and a 5 Gig Swap partition.  Should I continue with this or try something like:

5G- /var
5G- /usr
8G- /tmp
5G- Swap
1G- /
Remainging Gigs- /home

Keeping in mind, that I want to also develop an easy BACKUP routine to restore my OS in the event of some corruption.  That is my sole beef with Ubuntu so far...it gets corrupted easily and wont boot...at least not for a relative amateur such as myself and looking to move away from MS, does not make the process "comfortable" to explore.  For example...a few months ago I had a Power supply go bad and shut down mid boot.  Replaced it and all sorts of errors on next Ubuntu boot and could never get it to boot w/o hanging indefinately on a black screen, but my Windows (dual booting) worked fine when it would shut down during boot on it.  Things like that make me nervous when making this migration.  

I need to be able to restore from this sort of thing w/o having to reinstall the whole damn OS...hence why I am writing for suggestions on installing with possibly more partitions with the hopes that I can simply backup one or more of these partitions and restore easily with a LIVE CD or something like that.

So...with all that in mind...lend me your suggestions oh great Ubuntu gods!  :-)  

OH...by the way...please also recommend any format suggestions ie: ext3 vs ext4...etc.  I would think ext4 would be better than ext3 as logic to me would dictate that it is the next revision and newer/improved version...but...what do I know...I am a n00b.

After I have this information...I just need to find a fix to slow my dang mouse down...I have the WoW mouse and its a very high DPI mouse and even set to its lowest setting is too dang fast to comfortably use...


TIA for your help!

---

### Post by GackY2K on 2009-04-28
I've just ordered a UPS from Newegg, should be here in 3 days...hopefully that will safeguard against some power loss scenarios.  

Since I have the UPS on the way, I'm leaning towards going with ext4 format unless a good argument comes to stay with ext3.

Just please...any help on the # of partitions and any mounting points each should have and corresponding sizes.  Finally...tips on backup up OS.  I suppose I could go buy an external HD and just do a complete HD backup, but that seems unnecessary...surely someone has an "idiots" guide for backing up the OS and system preferences/settings...etc.

---

### Post by supererki on 2009-04-28
well it depends on what you wanna do.

what you are going to do with your computer. is it gonna be a server??

if its just simple desktop computer for browsing and mail etc then one part for root and other for /home should be fine.
Well you dont have to do it, but im going to put /boot to separate partition now if somebody doesnt help me with my grub recovery ([http://ubuntuforums.org/showthread.php?t=1141558](http://ubuntuforums.org/showthread.php?t=1141558))
... if you want you can but /srv and /var to different partitions as well... but this is a server solution. in srv services store like apache etc store their data. and var is used by processes that need to create files while working like printer spool files etc. 
anyhow.. make sure you set up lvm because otherwise 4 partitions is gonna be as much you are gonna get . lol  ;)

---

### Post by Niniel on 2009-04-28
The issue with ext3 is that it has a writeback cache where the "metadata" (which points to the actual data) gets updated first, and the actual data is written to disk afterwards, with a short delay. See this interesting discussion with Linus Torvalds: [http://thread.gmane.org/gmane.linux.kernel/811167/focus=811699](http://thread.gmane.org/gmane.linux.kernel/811167/focus=811699)
Ext4 is similar to ext3 in this regard, but it actually extends the delay for performance reasons (seems to work very well, too). However, there have been reports of major data loss on ext4 systems - when something happened during booting, all the files that had been read and were to be written back to disk, including many KDE/Gnome configuration files, ended up with 0 byte length. Linus Torvalds isn't a friend of this at all:
[http://thread.gmane.org/gmane.linux.kernel/811167/focus=811654](http://thread.gmane.org/gmane.linux.kernel/811167/focus=811654).

If you have time, read the whole discussion, it's quite interesting, even if one doesn't get all the technical details (I didn't :D )

If you don't want to read the whole thing, here are some other highlights (got this from an IT-oriented website):
[http://thread.gmane.org/gmane.linux.kernel/811167/focus=811679](http://thread.gmane.org/gmane.linux.kernel/811167/focus=811679)
[http://thread.gmane.org/gmane.linux.kernel/811167/focus=811700](http://thread.gmane.org/gmane.linux.kernel/811167/focus=811700)

So with your UPS, in light of the performance gains that ext4 seems to offer, it may actually make sense for you to use it. Otherwise, waiting might be better. Kernel 2.6.30 supposedly is going to include some improvements for this situation. But ext3 is also receiving updates to improve data security (some new "data=guarded" mode is being developed).

---

### Post by GackY2K on 2009-04-28
Well...the primary role for this system will be a typical home desktop PC, not a server.  So, looks like I really may actually only need 3 partitions:

1.)  Swap: 5 gigs (I have 3 gigs RAM, and I read 1-2 times your system RAM is recommended)

2.)  Root: "/"  How large would you say?  I've read as little as a single Gig is all I need up to many people saying 5 to 10 gigs.

3.)  Home: "/home"  The remainder of HD space here.


For backing up...I guess I'll just grab another HD (their cheap enough these days) and an enclosure to harness it and do full backups...hopefully there is a good program that can automate that for me, say knock it out while I am asleep  :-)  Maybe something that smart even that offers incremental backups and updating archive only with changes since last backup..etc?  Any suggestions there?

---

### Post by supererki on 2009-04-28
maybe you can boot /boot to one primary partition (because it is impossible to boot from logical partition at the moment) and then you set up LVM so it is really easy for you to resize the partition whenever you may feel like it. ok? :)
anyhow. you had 250gigs? 
1 say 20gb for root is probably more than enough. and leave the rest for your home i guess... well your computer, you decide.
good luck.

PS
[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)
perhaps you find it interesting
(i didnt really read it so google yourself for howto's) 
peace

---

### Post by rivera151 on 2009-04-28
> **GackY2K said:**
> Well...the primary role for this system will be a typical home desktop PC, not a server.  So, looks like I really may actually only need 3 partitions:

1.)  Swap: 5 gigs (I have 3 gigs RAM, and I read 1-2 times your system RAM is recommended)

2.)  Root: "/"  How large would you say?  I've read as little as a single Gig is all I need up to many people saying 5 to 10 gigs.

3.)  Home: "/home"  The remainder of HD space here.


For backing up...I guess I'll just grab another HD (their cheap enough these days) and an enclosure to harness it and do full backups...hopefully there is a good program that can automate that for me, say knock it out while I am asleep  :-)  Maybe something that smart even that offers incremental backups and updating archive only with changes since last backup..etc?  Any suggestions there?

That's how I have it on my system.  root has 10 G, swap is twice my ram and at the end of the disk, and home takes the rest.  After that, you can easily blow your OS, or reinstall, and your data is safe provided you dont erase the home partition.  It is quite useful.  Good luck.

---

