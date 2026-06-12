---
title: "Main ext3 Partition &quot;Not Bootable&quot;?"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by Kartari on 2009-01-04
After three attempts, I finally got Ubuntu 8.10 installed without apparent error.  I received a display error each of the first two attempts, one was a blue screen with text saying something like my display package was botched (my wording, I don't recall exactly what it said), and that it would try again in two minutes, and did not retry until I hit ENTER (which repeated every time I hit ENTER to try again).  The second resulted in screen gibberish or artifacts.  Both cases required restart and redo from scratch (e.g. deleted the ext3 and swap partitions and remade them).  This third time seems to have succeeded (e.g. I could reboot after Ubuntu reported success).  However, my system does not recognize the main ext3 partition as bootable, which is my concern now (I mention the previous errors in case they may be related somehow).

I have an AMD Sempron 3000, with 2 GB DDR400 RAM and a 300 GB SATA hard drive.  I have five primary partitions (yes, five), managed by BootIT NG (which allows more than four primary partitions), as follows and in this order: two NTFS partitions (one 60 GB for Windows XP Pro SP3, one 208 GB for my documents), one 8 MB partition for the BootIT NG EMBR, one 30 GB ext3 partition for Ubuntu and one 3 GB swap partition for Ubuntu.  The first three partitions have been there, the last two obviously added for installing Ubuntu.

Is Ubuntu incompatible with BootIT NG (even though it recognizes Linux ext3 and swap partitions and is made for multiple OS systems)?  Does Ubuntu need to be the first partition to boot?  Or is there another reason why it won't boot from the hard drive after an apparently successful installation?

Thanks!  From a newbie to Ubuntu.

---

### Post by Kartari on 2009-01-05
Anyone?  I'd appreciate any help about possible causes from boot managers in general, or any other advice related to the problem.  Or even just tell me what boot manager you use for your Windows / Ubuntu dual boot system and maybe I'll switch and see if that solves the problem.  Would making a logical or extended partition help at all?  I noticed that Ubuntu does not recognize extended partitions, though... I made one to try and keep my primaries down to four, in case Ubuntu had a problem with more than four (in fact, I deleted my BootIT NG partition to keep the count down to four primaries and reactivated it later, just in case that was causing the installer issues), but Ubuntu didn't even recognize the extended partition.

---

### Post by jrusso2 on 2009-01-05
It will boot from any partition but it must be made active.

---

### Post by Kartari on 2009-01-05
> **jrusso2 said:**
> It will boot from any partition but it must be made active.

I tried setting the ext3 partition to active (my WinXP partition was active), but it made no difference; I still get a message stating the partition is not bootable, even after I restarted the pc.

If it helps, I noticed that there are three entries for each partition labeled C, H and S.  I don't know what they mean, but the H for my WinXP partition is set to 1, and all others are set to 0.

---

### Post by Kartari on 2009-01-06
I'm still open to suggestions.  But if I don't get Ubuntu up and running soon, I will need to abandon it and make alternate plans (which is unfortunate because I was looking forward to it).  Anyone know a good source of information or faq regarding dual boot systems?

---

### Post by Mark Phelps on 2009-01-06
If I understand what you've said, the problem is not with Ubuntu, the problem is with your using BootNG.  AFAIK, Ubuntu needs to use either GRUB or LILO as a boot loader.  I don't have experiences with BootNG; so, I can't help you figure out how to get it to work with Ubuntu.

---

### Post by Kartari on 2009-01-06
Thanks Mark, I'll search for those, give them a try and report back.  BootIT NG claims to work with many operating systems, including Linux distributions, and it does in fact recognize the ext3 and swap partitions.  But you never know, maybe there's a bug, or maybe they never tried it with Ubuntu specifically.

---

### Post by Kartari on 2009-01-06
Well, I realized after I posted that if I removed BootIt NG, I'd lose access to my drive image on DVDs.  So I managed to find an online help article that covered using BING with Ubuntu 7.04, requiring setting up the partitions in BING and reinstalling Ubuntu (for the fourth time now).  But of course it didn't work, I had the same exact problem, and almost had a heart attack as I thought I lost my documents partition (false alarm).  Right now, I'm ready to throw my computer out the window, so I'll try your boot manager suggestions tomorrow.  I can always reinstall BING if it doesn't work to regain access to my drive image DVDs again.

---

