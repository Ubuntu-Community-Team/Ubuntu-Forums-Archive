---
title: "hd partition question"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by chris2510 on 2009-07-25
Hi all,

I just got my Ubuntu 9.04 CD yesterday.
When I went to install it on my system I noticed that my 500 gig. hd is partitioned with 497 gig. for Windows XP.
My question is this...
When I install Ubuntu can I simply edit the NTFS partition with out causing problems with Windows or will it cause XP some issues.
I did get to the partitioner and started to edit the NTFS partition but backed out because I was not sure if I could safely do this. I don't want to go through all the crap of re-installing XP.
By the way, of the 497 gig on the xp partition I am currently using about 60 gig. and probably will never reach 100 gig. used. Thus, I can use 400 gig for Linux.

Thanks

Chris

---

### Post by merlinus on 2009-07-25
Defrag xp several times beforehand.  Then you can shrink it during installation of ubuntu.

You might consider creating a separate /home partition as well as / and /swap, and even one for /data that, if formatted as ntfs, can be shared by both oses.

In that case, leave xp on a primary partition, and create the others within an extended one.

---

### Post by lisati on 2009-07-25
I concur with melinus's suggestion to defrag the xp partition before resizing it. Some people also find it useful to (temporarily) turn off XP's paging and a few other bits and pieces before defragging - see [here]("http://ubuntuforums.org/showthread.php?t=497482") for one example. I also like to clean out the %temp% folder as well, which isn't always cleaned up particularly well with the Windows "Delete temporary files" utility.

---

### Post by raymondh on 2009-07-25
+1 on creating a separate /home partition.

Back-up your files first.  Then defrag.  Then boot into the liveCD to check for defects and [md5]("https://help.ubuntu.com/community/HowToMD5SUM").  Then try out a live session to see how it interacts with your system.  Then install.

If you decide not to create a separate /home ..... when you get to the installer, you can choose GUIDED RESIZE and use the slider to allocate partition sizes between XP and Ubuntu.  

**Remember to grab the slider and allocate**.  If not, you'll be left with the classic 2.3GB-sized Ubuntu install and will wonder why you don't have enough space to make the first updates :)

Some links as reference/guides:

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Good luck.  Oh, and welcome!

---

### Post by chris2510 on 2009-07-25
Thank you all,

On your advice I did as you said and my XP is safe, just wish I didn't need it for school.

I also made the /, /home and /windows (data) partitions, the /swap was added automatically.

I have not used Linux since before Red Hats IPO and at that I was just getting started so I'm sure you will see me asking hundreds more questions, but will try to do my part and first scan the man pages.

Again, thanks that really helped!!!

Chris

---

