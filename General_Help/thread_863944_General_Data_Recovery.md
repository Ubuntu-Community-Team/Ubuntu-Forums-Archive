---
title: "General Data Recovery"
date: 2008-07-19
forum: General Help
---

### Post by fixerdave on 2008-07-19
Okay, my drive came up fubarred the other day.  No big deal, I have a fairly recent backup.  Besides, it was time to upgrade to 8.04 anyway, and it was a good excuse to buy a bigger drive too.

But, being new to Linux, I thought I'd take the opportunity to learn some Linux data recovery techniques.  I'm old-school tech but a fairly recent convert to Linux.  Anyway, I'm interested in some recovery approaches for an ext3 formatted drive.  So, ignoring the fact that I have a backup and the only stuff I'm missing is a little non-essential MySQL data and a couple of Dilbert cartoons, where should I have started?

The scenario:  the system was up and running but just ground to a halt.  A reboot, well, didn't.  The boot-loader ran but it reported I/O errors when trying to load the Linux kernel.  Oh, BTW, this is on a PPC Mac-mini running 7.04 on a single drive with default partitions.

My actions:

1) boot with the Ubuntu 7.04 live CD I originally installed with and run testdisk.  It said it couldn't find any file system on the partition and ground to a halt when "digging deeper."

2) run dd_rescue to copy the entire partition to a file on an external drive.  Yes, I know I should have done this first, but, like I said, I'm just learning here.  It copied the entire 35G without reporting any errors.

3) ran sleuth-kit on the exported file but it showed nothing.

So, that's where I'm at so far (right now, I'm waiting for my backup files to copy over so I'm killing time).



I guess I have a few things I'd like to figure out:

1) if/how I can rebuild the format information on the drive so I can access the files.

2) how to recover MySQL data from the file structure, rather than an SQL dump.

3) a better automated backup of MySQL data so that I don't have to figure out #2 next time.

4) if it's possible to take a 7.04 full backup and selectively dump it on a 8.04 install to get things going without having to re-install all the details.  I don't really want to do this because the original 7.04 install wasn't exactly good - I have learned a few things along the way.  But, I am curious if it's possible.


Like I said, this is an educational exercise as I've not really lost much of anything data-wise.  But, someday I might, or someone might be begging me because they did.  Knowledge is power.

Any suggestions for where to proceed?

    David...

---

### Post by iaculallad on 2008-07-19
Try the [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") Utility.

---

### Post by fixerdave on 2008-07-19
> **iaculallad said:**
> Try the [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") Utility.

Well, that's the first thing I did.  Like I said, it didn't help and ground to a halt while "digging deeper."

Anything else that can sort out a corrupt partition?  What about MySQL data?  Still curious,

    David...

---

### Post by spoketire on 2008-07-22
I've had results with Foremost and Scalpel (scalpel is the faster of the two).  By results, I mean that I was able to carve files off my unusable disk, and they won't have a problem with the corruption. They can work on your image file too, but they wouldn't help you in restoring the filesystem so that you can look at the folder structure. You just get numbered files out of them. Another difficulty with these programs is that they only support a limited number of file types by default, so I don't know about your MySQL stuff.  Anyway, just something you could try.

---

### Post by fixerdave on 2008-07-29
Well, good news and bad news:

The good news is that I didn't need to resort to file carving.  I just took the dd_rescue image, dumped it back down to a spare USB drive, and then ran fsck on it.  Well, I aborted the first run and then set it to automaticall fix on the second try.  Hitting "okay" to "do you want to fix?" after the 50th or so error that came up got a bit too repetative.  Anyway, despite the errors, the drive seems pretty readable and I've managed to recover my 2 dilbert cartoons that weren't in my backup.

I've also copied off my MySQL data folder.  From what I've read, all I need to do is copy that folder back into my new install, after I re-install MySQL, and the data should just pop up.  So I've read, anyway.  I've managed to get a little distracted on my system re-install, which brings me to the bad news.

The bad news... remember when I said this was just a learning exercise as I had a decent backup?  Well, a friend of a friend brought his computer over because Win2k broke.  He didn't have a backup.  No problem, I say, as I whip out my Ubuntu live CD.  There's the data on his 60Gb fat32 drive.  Okay, I say, lets copy this off to a spare 40Gb USB drive... but wait, the USB drive is formatted ext3, and it's for Windows so I figured on reformatting it to fat32.  No problem, gparted does it no problem, except... wait... there's a problem.  It would seem that I pulled a seriously-stupid move and reformatted his internal 60Gb drive.  I have no idea how I did that, I've been formatting USB drives quite a bit the last while and, well, I guess that's the problem.  I was on automatic, talking to this guy, and not paying attention to what I should have been doing.  So, long story short, now the data recovery is for semi-real.

He doesn't really care about what's on the drive.  So, all I really have to do is install WinXP (he has a Windows tax program he uses) and he'll be happy. I'll rebuild his system such that it dual-boots to Ubuntu (so he'll have a backup OS after XP dies)... But, as a matter of pride, I'd like to get back his old tax data from the drive I mucked.

Not having a large enough spare USB drive to take a full 60Gb image of the mucked drive, I took a chance and ran testdisk on it.  Nada, it just reported the perfectly fine, but empty, fat32 partition on the drive.  Though, this may be not using testdisk properly yet.  I'm still learning here.  Anyway, I finally dug up an 80Gb drive and threw it in my USB drive enclosure and I'm running dd_rescue right now to make an image before I do anything else.

So, this is turing out to be a pretty comprehensive one-man data destruction thread.  Anyone have any ideas about what I should try for unformatting fat32 via an Ubuntu Live CD.  I have a few DOS-level tools I'm thinking of trying, but I'm still trying to walk the Linux path here.

Any suggestions appreciated,

    David...

---

### Post by spoketire on 2008-08-09
You could try these:
[http://matt.matzi.org.uk/2008/07/03/...d-hard-drives/]("http://matt.matzi.org.uk/2008/07/03/...d-hard-drives/")
[http://forums.gentoo.org/viewtopic-t-365703.html]("http://forums.gentoo.org/viewtopic-t-365703.html")
I think these scripts reconstruct the file/folder structure if you have a damaged filesystem, but I haven't tried them. I'm not sure if they would work on a completely reformatted drive, although the data is still there.

---

### Post by fixerdave on 2008-08-09
Hi, thanks for the reply, and I'll check out the scripts you mentioned.  However, I did manage to recover the data, including the file structure, with TestDisk.  It took a bit of futzing around, mostly following the TestDisk recommendations to change the drive geometry (oddly enough), but it eventually found the old partition and restored it.  I managed to copy off all the data intact.  I learned a lot and am most pleased with the results.

The system in question is still sitting on my desk, still not working properly, but at least I'm still learning.  I dumped XP on it and, of course, ran into difficulty finding video and sound drivers.  I hate that "guess the motherboard" game.  Anyway, after some frustration, I figured I'd just dump Ubuntu in the second half of the drive and tell him to use that for everything except his stupid tax program.  I'm really, really sick of the XP driver hunt.  Anyway, the Ubuntu install bombed on the file copy - stuck at 17%.  I rebooted, and tried again, stuck at 5%.  So I started the next phase of my Linux education.

I hunted around, trying to find the Linux equivalent of checkdisk for doing a surface scan.  I figured the original problem was a failing HD and a good scan was in order.  I eventually found that the smartmontools package contains smartctl, which is suppose to do the scan, but I couldn't install it after booting to the Ubuntu liveCD.  It said there wasn't enough space - this is an old machine without a whole lot of memory - ARG!  So, at this point, I gave up, booted to XP, formatted the second half of the drive (that I had left for Ubuntu) as NTFS and ran checkdisk on it.  After that, I blew the partition away and now I'm currently installing Ubuntu - it's at 56%, and still counting.

I'd really like to get my Linux skills up to where I'm at with Windows but it can be an intensely aggravating process.  I'm getting there, and I know it's worth the effort, and I'm really grateful for forums like this and people that are willing to help a guy over the hump.  So, thank you, and everyone, for the responses.

Once I get this %$@%! machine off my bench I'll summarise my notes, here, for the next person that's following in this path.

Thanks again, and keep the suggestions coming, we might as well have a single thread that outlines all the options,

   David...

P.S.  Yeah, 100% complete Ubuntu install :)

---

### Post by Bruce M. on 2008-08-09
> **fixerdave said:**
> 4) if it's possible to take a 7.04 full backup and selectively dump it on a 8.04 install to get things going without having to re-install all the details.  I don't really want to do this because the original 7.04 install wasn't exactly good - I have learned a few things along the way.  But, I am curious if it's possible.

Any suggestions for where to proceed?

    David...

Hi Dave ... OK, educational exercise, I like that.

As to putting 7.04 stuff on 8.04 the answer is: Yes, in part.

For example:

**[SIZE="2"]/[/SIZE]** - contains the program files, OO, GIMP, FireFox, etc. etc.

/home contains the "config files" and data files for these programs, plus your personal stuff if you kept them in a sub-directory under /home.

So if you install 8.04 and then restore 7.04's [SIZE="2"]**/**[/SIZE] you'll be overwriting newer versions of programs with older.

However /home is a GEM to have. Here's why:

Backup your 7.04 /home directory.

Install 8.04 and before "anything else" restore your 7.04 /home over 8.04's freshly created basically blank /home directory and you'll have:

Firefox with all your settings and bookmarks.
Your "Dilbert" cartoons if you kept them in a sub-directory in /home
Thunderbird - all your email if you used it previously (I imagine this is good for Evolution as well, but I don't use that so can't say 100%)

Now get any udates that 8.04.1 wants to get and your ready to open programs like Firefox to see your bookmarks and added what ever other files you had in 7.04 that were not loaded by default.

**NOTE:** It is important to restore your /home directory **before** you open any programs, as running a program will create hidden files to use when you do, but if those files exist (from the restored /home) they will default to using them instead.

I have about 12-15 cases of doing this in the past month as I built a new machine, and because of hardware problems had to rebuild my old machine at times to get answers. Also note I use Quickstart (see my signature) for backups and it's really saved my bacon. Never lost a single byte of info.

So all you really "need" to do is restore your /home directory if you install 8.04.1 fresh.

Have a nice day.
Bruce

---

