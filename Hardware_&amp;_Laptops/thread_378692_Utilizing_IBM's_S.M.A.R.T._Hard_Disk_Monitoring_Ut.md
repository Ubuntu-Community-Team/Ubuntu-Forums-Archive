---
title: "Utilizing IBM's S.M.A.R.T. Hard Disk Monitoring Utility"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by Megatog615 on 2007-03-07
How do you use the S.M.A.R.T. functions in a modern hard drive on Ubuntu? I'd like to monitor my drives, and I'd actually like to see if I need to purchase a new drive before my current drives fail. Are there any free utilities for Ubuntu that can allow me to monitor my drives?

---

### Post by wnelson on 2007-03-07
Just apt-get install smartmontools. You can then use smartctl to see what possible error codes there are. Do man smartctl to see what options are given.

Walt

---

### Post by SuSUntu on 2007-03-07
Just to follow up to Wnelson's post: smartmontools also contains the daemon smartd which is (if you desire) launched as a background process. It is highly configurable via text file and can be set to send notifications (via email, for example) of various test results, etc. The conf file has a scheduler functionality, so you can schedule various types of tests to run at certain times.

Just a word of caution: if you are using WD Raptor drives and happen to be at your computer when smartd launches one of the extensive tests in the background, you may think that something horribly wrong is happening to your hard disks. The sound is hard to describe other than to say that I didn't know hard drives were made to withstand that kind of spin-up rate (I guess low volume turbine comes to mind). Here's an example of a command for such a [noisy] test (using smartctl rather than the daemon):

sudo smartctl -t short -d ata /dev/sda

The above command was used on a WD Raptor (SATA), thus the requirement for the '-d ata' device type designation. The information about SATA testing may be difficult to find, so here is the link (it may be a little confusing, but the -d ata command is the one you want):

[http://smartmontools.sourceforge.net/#testinghelp](http://smartmontools.sourceforge.net/#testinghelp) 

To run the same test on a PATA drive, you would simply have to issue this command:

sudo smartctl -t short  /dev/hda

-------------
By the way, here's a sample of the smartd.conf from the smarttools website (its also the man page for smartd.conf):

[http://smartmontools.sourceforge.net/man/smartd.conf.5.html](http://smartmontools.sourceforge.net/man/smartd.conf.5.html)

---

