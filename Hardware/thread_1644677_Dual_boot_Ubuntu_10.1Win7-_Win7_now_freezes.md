---
title: "Dual boot Ubuntu 10.1/Win7- Win7 now freezes"
date: 2010-12-13
forum: Hardware
---

### Post by azhermit on 2010-12-13
Sony Vaio VPCEB33FM  came with Win 7 Home Premium. Worked fine. Installed Ubuntu 10.1 in a dual boot. Also worked fine. When running Win 7 since dual boot installed it freezes -- actually it slows to a crawl such that just closing a window takes 45 seconds and it will not shut down. Also, CTL-ALT-DLT will not stop offending program and freezes itself when attempting to force a shutdown of program or computer. A forced shutdown by holding the on/off button is required.

Anyone had this problem and fixed it? 

It ocurred to me to reinstall Win 7. But, I do not know how to reinstall Win 7 within its own partition (and possibly the hidden system backup file partition) -- that is without affecting the Linux partition. I ran the built in Windows repair program without success and if I run Windows recovery program to replace files with the original files from the hidden backup partion it will completelyreformat the entire hard drive including Linux and start over.](*,)

I could care less about Windows except I seem to be required to save it (or buy another laptop just to run it - that would suck) to view a security camera system remotely for my business whose viewer is written only for Windows.:sad:

---

### Post by wilee-nilee on 2010-12-13
It sounds like you have Ubuntu installed inside of W7=Wubi.

It sounds rather unusual, but not implausible, finding the exact reasons I couldn't do.

You might just burn a cd or load a thumb with a downloaded ISO and see how Ubuntu runs booted, thumb generally runs better.

If you have no real attachments and can back up the Ubuntu you can either migrate it to a real partitioned set up, or just remove it and see if this problem goes away in windows.

Are you using windows as a admin with no password or a limited account passwords on both? Do you also have some AV program id so which?

Edit: When you have W7 use a cpu, ram, process, monitor, the easiest is the task manager accessible by a right click on the bottom panel. You may have to many things starting up that are not needed, and just using up the cpu...etc

---

### Post by azhermit on 2010-12-14
I did burn an ISO to disk (from Ubuntu's web site) and ran Ubuntu as a test from CD before installing it for about a week. Then I followed directions on the disk to install it. It formatted its own partitions and I did not change its space allocation as it was being done on an almost new 360 gig drive and it divided it roughly in half for Linux and Windows.

Running W7 as admin, no password. U10.1 limited accounts. AV program id?: No
> When you have W7 use a cpu, ram, process, monitor
Did that. CPU not doing much: average 3%. Looked all over task manager for culprit (which took forever during problem). Cant find anything doing anything wrong or informational. It just won't do anything. Hard drive light on computer front does very little: just little blips periodically. Forced shutdown to get running. Restarted and restarted again to clear everything. Then went to remove startup programs (God, OEM's crap up their computers!). Started faster but still had problem when doing much of anything: starting Firefox, I.E., or just looking around within Win for problem, and locks up in the middle of looking around within 10 min or so - sometimes sooner.

I could just start over as you suggest, although I do not relish the file backup and restore & Firefox re-set up in Ubuntu with add ons. Ubuntu runs Soooo... well now. Just that W7 runs soooo. crappy.

I wrote Canonical to see if they have had any known issues of U 10.1 beside W7 64bit and haven't heard back yet. I wondered if there were any issues with Ubuntu's installer not recognizing W7's (actually Sony's incarnation of W7) hidden system file partition when Ubuntu pre-partitions the hard drive. I would  think this was so elementary to a programmer that I didn't ask that directly as it might be an insult to their intelligence.

---

### Post by azhermit on 2010-12-14
And...
> If you have no real attachments and can back up the Ubuntu you can  either migrate it to a real partitioned set up, or just remove it and  see if this problem goes away in windows.

Isn't Ubuntu already in a "real partitioned setup" if I did as I say and did the dual boot from the Ubuntu downloaded ISO then burned to CD and used its own self-install program to repartition the drive?

---

