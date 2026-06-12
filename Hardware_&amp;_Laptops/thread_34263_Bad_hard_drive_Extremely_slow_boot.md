---
title: "Bad hard drive? Extremely slow boot"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by xingmu on 2005-05-14
My questions: Is there any software glitch that could cause my current problems? Is the problems solely in hardware?  Is it really the harddrive?  What test can I run to be certain that the harddrive is faulty? 

My history:
I have a Toshiba Tecra M2 and was running Ubuntu Hoary in the last month or so.  About 6 months ago I had problems with the CD-ROM writing/reading disks so I got that replaced under warranty.  A couple months later the display suddenly went black for good.  I was supposed to get the display and motherboard replaced...but I think in the end they just replaced the motherboard.  And then, in the last couple months I became aware that my harddrive (Hitachi Travelstare) was failing.  Originally I had been using WinXP and had some odd problems (long boots, Windows built-in CD-ROM writing suddenly stopped working again?!?!) and so I switched to Linux to see if the problems were in software or hardware (and I wanted to make the switch anyhow!).  Sure enough, the CD-ROM problems went away....but new ones popped up (like Firefox suddenly could only loaded half a webpage and then freezed, desktop image and icons sometimes wouldn't load on boot).  I ran a badblocks test and found many bad blocks (I just stopped running the test after I saw that many).  So I replaced the harddrive with a completely new one (under warranty).  

My current problem:
Yesterday I came home with my new harddrive and went to install Ubuntu again.  My first install was stupidly interrupted because I forgot to plug in my laptop and the battery died.  The second one (starting from scratch) crashed when trying to install and setup packages after the first boot.  I saw warnings of "DMA timeout" and just before it crashed there was Buffer I/O errors.  I tried to restart and salvage the installation...I did manage to finish installing packages and boot up into Gnome.  But the boot was about 5 minutes long (it was 1 min or less on my old harddrive).  In Gnome, loading programs was extremely slow.  So I decided to start from a clean install again and see if that could make the bad nightmare go away.  The second install went smooth.  But booting up still tok about 5 minutes and programs loaded very slow.  After going through a number of tasks on the Ubuntu Starter Guide and finding a suggestion that maybe I shouldn't use DMA, I booted up without DMA support for the hard drive.  The boot took about 25 minutes (no joke).  Programs were still slow. So I ran a badblocks test and went to sleep.  When I woke up about 8 hours later, my screen was filled with Buffer I/O read errors...and listing off every block on my drive.  Restarted again this time WITH DMA on, boot still took a half an hour...programs still load slow but I can still "use" the system (so to speak).

I assume that the harddrive is the problem.  But it's hard for me to accept this because it's BRAND NEW (and my last hard drive was bad...what's the chances of this?!).  And I have suffered so many hardware problems I can't handle it anymore.  The only announcement I have gotten from Toshiba about known hardware issues is the possibiltiy of bad memory.  I ran their test months ago under Windows and it said that my system did not have a problem and would not need to do the product recall.  Please, someone give me some reasonable advice....my laptop is critical to my work and I can't sleep anymore!

---

### Post by nad on 2005-05-14
You may download Hitachi's drive fitness test here:

[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

The drive test will run from its' own bootable floppy or cd.

---

### Post by xingmu on 2005-05-15
Thanks for the reply.  I will try it out tonight before I have to go back to the service center.  Hopefully I can get some irrefutable proof of what's wrong with my computer.   I am afraid the service center is going to give me a lot of hassles for replacing a brand new hard drive otherwise.

---

