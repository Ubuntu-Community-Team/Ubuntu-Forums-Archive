---
title: "Super slow USB speeds - Nautilus, not GVFS, is the culprit."
date: 2008-09-05
forum: General Help
---

### Post by detroit/zero on 2008-09-05
There's been some issue for the last month or two about [slow USB file transfer speeds]("http://ubuntuforums.org/showthread.php?t=793688"). I've [been affected by this]("http://ubuntuforums.org/showthread.php?t=895386"), and seen transfer speeds so low you could compare it to using a carrier pigeon. It's been largely believed that GVFS has been the problem. I just found out otherwise.

Not only had I been rather disgruntled with my USB write speed (mainly to an external hard disk, not flash memory) but I got stuck with some kind of login loop that I couldn't break without using Failsafe GNOME mode. Unable to track down this problem, and unable to downgrade my GVFS version, I decided to do a quick re-install. I backed up my saved documents, pics, videos, music to the external drive (which took hours when it should have been minutes), and even wiped and reformatted my home directory so I would be sure not to bring any messed up configuration files with me.

So, after my reinstall, and doing things like compiling compiz and customizing this, that, and the other, I went into Synaptic and locked my GVFS version to the one that came off the CD. Then I upgraded Nautilus.

Now I'm stuck with slow slow **slow** USB transfer speeds again. A 6.8GB transfer of a half-dozen or so movie files has been running almost as long as I've been writing this, and the ETA is still 20 minutes out. It'll probably end up taking 35 or 45 minutes from start to finish.

On to the questions:

[LIST=1]
[*]Is there going to be a patch or fix for this?
[*]Will it come before Ibex is released?
[*]If not, will it be backported to Hardy?
[*]Is it possible to re-install the nautilus version from the CD?
[*]Will that even fix the issue, since it may not be Nautilus itself, but some lib fle or something somewhere that nobody's looking at?
[*]Should I just re-install the whole OS again and lock the Nautilus version until a USB-functional update is issued?
[/LIST]
I guess that's it for now. I'd just do the re-install while I wait for answers, but man it's a lot of work compiling this and that, installing software, and dowloading updates.

---

### Post by detroit/zero on 2008-09-07
Just an update -
I went ahead and re-installed the OS. Before I even turned on my network access I went into synaptic and locked the version numbers for everything Nautilus and GVFS, then connected to the internets and went ahead with all other updates. I now enjoy USB transfer speeds approaching 30MB/s.

It's alot to go through for such a simple problem, but I download a lot of movies and music and spending hours and hours to move a couple GB worth of media files to an external hard disk is just too much to bear.

---

### Post by Hiperi0n on 2008-09-07
So you mean that reinstalling ubuntu from scratch corrected your problem? And that the cause is a newer version of nautilus?

pci=routeirq in menu.lst seems to correct the problem...

---

### Post by detroit/zero on 2008-09-07
> **Hiperi0n said:**
> So you mean that reinstalling ubuntu from scratch corrected your problem? And that the cause is a newer version of nautilus?

pci=routeirq in menu.lst seems to correct the problem...
I didn't even have to add pci=routeirq; it was automatically included in the boot option string after, I believe, 2.6.24-19 (though I could be wrong..)

Sure, it made an improvement: I went from transfer speeds between 300 and 800 **K**B/s, to between 2.5 and 15**M**B/s (starting at the high end and getting progressively slower as time passed). I have a read/write monitor in my conky and I could see that there was hardly any disk write activity while file transfers were happening.

Like I said, I locked my Nautilus and GVFS versions as soon as I installed from a 8.04 CD, and I'm rocking and rolling with USB transfers close to 30MB/s.

To put it another way - in the last few days of having a fresh OS, I've moved about 30GB or so of videos to and from my USB hard disk and I've never seen it dip below 24MB/s.

Like I also said, everyone thought GVFS was the culprit, but after one re-install I had my GVFS version locked but updated Nautilus (and I believe send-to and cdburner packages as well) and I was stuck with the slow transfers again.

Seems pretty clear to me where the problem lies.

---

### Post by Hiperi0n on 2008-09-07
You are right, my transfer speed is quite the same as before, with or without pci=routeirq.

Have you filed the bug? I guess there are many filings regarding this issue...

Do you know the exact version of nautilus is the one in the fresh install and that works fine in transfers?

---

### Post by detroit/zero on 2008-09-08
No, I didn't file any bug report. I'm not signed up at launchpad or anything, and don't really know the procedure and all that. I guess I figured someone would see it here eventually and do all the work..

At any rate, in Synaptic, I see that my nautilus versions are locked at:

[LIST]
[*]nautilus 1:2.22.2-0ubuntu4
[*]nautilus-cd-burner 2.22.1-0ubuntu1
[*]nautilus-data 1:2.22.2-0ubuntu4
[*]nautilus-sendto 0.13.2-0ubuntu1
[/LIST]
and GVFS:

[LIST]
[*]gvfs 0.2.3-0ubuntu4
[*]gvfs-backends 0.2.3-0ubuntu4
[*]gvfs-fuse 0.2.3-0ubuntu4
[*]libgvfs-common0 0.2.3-0ubuntu4
[/LIST]
Everything is kept up-to-date - just those packages are locked. After my last experience, I almost want to run the risk of letting GVFS update just to further narrow it down, but I'd really hate to have to re-install again.

---

### Post by detroit/zero on 2008-09-08
Well, I guess I was wrong.

I went ahead and unlocked GVFS and let all the aforementioned packages update. 
Slowville, here I am. Again.

It was strange, though. I had one .avi file 1.4GB in size, and I cut & pasted it to my external disk - the speed varied, but averaged 24MB/s. For the first time since re-installing ubuntu and locking those versions, it dipped as low as 18MB/s. I knew something bad was about to happen.

I then cut & pasted two more .avi files, totalling 1.4GB (700.x MB each) and I'm holding a strong and steady 4.1MB/s transfer speed. My GUI is sluggish and unresponsive, even though conky says my processors are only running at around 18% each.

Well, I guess the problem lies between the two - nautilus *and* gvfs.

I think I'll download and try Ibex - from what I've read, it doesn't have these problems. I hope not, anyways.. re-installing OS's just for the comfort of decently-speeded file transfer speeds is becoming a tedious hobby.

---

### Post by detroit/zero on 2008-09-08
Ibex is just as bad, if not worse.

Going back to Gutsy.

kthxbai

---

### Post by detroit/zero on 2008-09-09
Well, I've got some definite answers that lead to a million more questions.

I've been fighting this problem tooth and nail for over a week now. I've done multiple reinstalls of Hardy, Gutsy, Kubuntu Hardy,  Xubuntu Hardy **and** an upgrade to Intrepid Ibex - all of them end up with the same problem.

I'm running now on a less than 24-hour-old fresh install of Hardy Heron. Before I connected to my network and did all the requisite post-install updates, I went in through synaptic and locked my Nautilus and GVFS versions (and their dependencies). Even after the updates, I was cruising along with almost 30MB/s read speeds and write speeds that never dipped below 24.5MB/s. 

Not even one full day - and not one update - later, I'm back to my super slow (4.5MB/s max) USB file transfer speeds.

I thought I was on to something there.

I've been Googling for some time now and one thing I've found is that this problem isn't distro-specific and it's not dependant on any window manager. I've seen this problem reported in Debian, Ubuntu, Mint, Arch, and Suse forums (along with some generic Linux forums) and it's reported by people using GNOME, KDE, busybox, and XFCE.

A [Google.Linux]("http://www.google.com/linux") search of "[linux slow usb speeds]("http://www.google.com/linux?num=20&hl=en&safe=off&q=linux+slow+usb+speeds&btnG=Search")" or "[hardy slow usb speeds]("http://www.google.com/linux?num=20&hl=en&safe=off&q=hardy+slow+usb+speeds&btnG=Search")" will turn up page after page after page of people reporting the same problem.

From all my reading, the problem lies either in the kernel, a conflict between the ehci and uhci modules, synchronous/asynchronous auto-mount options, or as one user suggests, it's possibly [a hardware issue with a particular chipset]("http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17032.html").

I've got a lot of investigating to do to figure out where I fit into this grand scheme of things, along with what can be done about it, and I'm not the most knowledgable linux user in the world.

I guess that's where it stands now.

---

### Post by Hiperi0n on 2008-09-12
It seems that the problem is only with large files. I have copied a large number of photos to the external drive and the speed is above 30 MB/s

---

### Post by detroit/zero on 2008-09-13
> **Hiperi0n said:**
> It seems that the problem is only with large files. I have copied a large number of photos to the external drive and the speed is above 30 MB/s
I have problems with files of all sizes. Read speeds are fine - 25MB/s and higher. Write speeds (to both flash mem and an external hard disk) are what drags forever, with speeds never even breaking 5MB/s.

---

### Post by Hiperi0n on 2008-09-14
-duplicated (can't I erase posts?)

---

### Post by Hiperi0n on 2008-09-14
What the hell is going on? I have just copied 3 large .tar.gz files to my external drive (totalling 612mb) and it took a very short time (>30mb/s). Is the problem only with video files? I don't think so but this is getting weird...

---

### Post by Hiperi0n on 2008-09-16
Bump. The transfer speeds seem to vary depending on I don't know what weird factor...

---

### Post by Namain on 2008-09-18
I have the same problem.  I noticed it happening while trying to transfer mp3s/oggs to my media player.  

I'm not sure why, but my player seems to be mounted as USB 2.0, but again, write speeds are around USB 1.1 speeds.

---

### Post by dimeotane on 2008-09-21
I upgraded to hardy and tried to backup a 4 GB file today to USB flash drive.  Seemed really slow. A 4Gb file drops to 11Mb/s.
 My 1gb transfer rate tests confirm it. I used this command:

dimeo@dell-laptop:/media$ sudo time dd if=/dev/zero bs=1024 count=1000000 of=/media/XPORTER/1Gb.file

on my old Gutsy a test I did 6 months ago:
1000000+0 records out
1024000000 bytes (1.0 GB) copied, 58.1425 seconds, 17.6 MB/s
0.41user 5.87system 0:58.26elapsed 10%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (1major+256minor)pagefaults 0swaps

on the same system 'upgraded' to Hardy:
1000000+0 records out
1024000000 bytes (1.0 GB) copied, 81.4425 s, 12.6 MB/s
0.28user 5.81system 1:21.86elapsed 7%CPU (0avgtext+0avgdata 0maxresident)k
2017inputs+2003928outputs (2major+254minor)pagefaults 0swaps

---

### Post by detroit/zero on 2008-10-19
Since the slow USB write problems aren't limited to Ubuntu, and seem to apply to various distros and kernel versions over the last few years, I started [a thread over at Linuxquestions.org]("http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/")
 
 Maybe the people who are having this problem can all get together and find a fix, rather than wait to see what trickles down from on high.
 
 Come over there and chime in with your experiences with the slow USB write speeds.

---

### Post by Maharifu on 2008-10-25
Hi
I'm using Ubuntu Intrepid, and I am experiencing the same slow usb speed problem (~1,5MB/s). I read something about mounting with async option and tried remounting with it (sudo mount remount,async /dev/sdb) after the drive being mounted, only to get the same results.
Then I tried forcing the sync option (sudo mount remount,sync /dev/sdb) and the speed dropped even further (~500kB/s). So I think this speed problem isn't related to sync or async issues...

Just to drop my thoughts.. :P I'm a noob in linux, so I  might be doing something else wrong...

---

### Post by taecha on 2008-11-05
> **detroit/zero said:**
> From all my reading, the problem lies either in the kernel, a conflict between the ehci and uhci modules, synchronous/asynchronous auto-mount options, or as one user suggests, it's possibly [a hardware issue with a particular chipset]("http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17032.html").

I have experienced rather slow transfer speeds myself. After the recent kernel update I *perceive* transfer speeds to have dropped even further. It is actually so bad that when copying 8 files totalling 4.3G to my USB HD recently the entire Ubuntu system was unresponsive most of the 30 or so minutes it took to copy those files although CPU load was around 10% only. This did not happen to that extend with the old kernel.

Maybe this supports the notion that it has something to do with the kernel.

---

### Post by vivichrist on 2008-11-26
> CPU load was around 10% only.
yes but massive IOWait times

I'm having same problem I wish someone more tech-savy would do something about it.... I really need to have decent throughput with usb. I have no clue

---

### Post by mister_p_1998 on 2009-03-11
Im getting this after I upgraded my 3 year old Dapper install to Hardy, as Dapper expires in June. I use GRSync and Im getting 2-6 mb per sec, mainly 3 MB per sec though. it used to sync up my sandisk in 30 seconds, it now takes 3 minutes plus! Roll on the patch!
Steve

---

### Post by Pokey_blue32 on 2011-12-28
NO...try looking @ the MOUNT options...notice the drive is SYNC not ASYNC...the problem is a MIX of issues.

1) Large page in use
2) on the fly defrag
3) SYNC xfer(which FAILS to respond to the FLYING defrag and.or large page )

This is posted on Linux Mint forums...not sure how to avoid SYNC mounts unless fstab has manual mount command in it. I use Thumbs and the internal postage stamp with my Gateway LT21. Sometimes i use external HD, so the mount point changes...this PERTURBS me..

This is the case when /dev/sdb[x] is not ALWAYS /dev/sdb[x] or even /dev/sdb at all.
A Manual entry in fstab has been known to fix this issue, which apparently is at the kernel level. Most of us are running 2.6+ these days, some of us 3.0+. This is unfixed issue for some time affecting multiple distros.

---

