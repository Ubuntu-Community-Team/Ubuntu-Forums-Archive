---
title: "Trouble installing Unbuntu Server on older PC"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by phenom5 on 2009-01-11
Hey all,

I'm at my wit's end here, so hopefully you guys can help me out.  Not sure if this is the correct forum, but...

To make a long story short, I want to turn an old PC (Compaq) into an HTTP server, and I figured I'd check out Ubuntu server while I was at it.  

Went through the install, and it seems like everything installed correctly.  But it won't boot.  It runs through 3 or 4 screens of text, and then it stops.  It doesn't hang, it keeps running on this one screen (I can get the exact text displayed later today).  There are a bunch of lines with [90.55002] followed by some text, and the last line has is [90.55002] ==========================.  If I leave it running the numbers in the brackets increase, but yesterday I left it running for ~20 hours, it was up to [3xxx.xxxxx](something, can't remember the exact number), but still hadn't made any progress.  

I have an Ubuntu live CD also, so I tried to boot from the CD, and install it, but neither worked.  It would get to the splash screen, the progress bar would stop. 

So then I tried to install a trial copy of Windows Server 2008.  Booted from the CD, Windows loaded the files, but then it was stuck on the gray background (not sure how familiar you guys are with Windows)with no prompt to change the admin password, and no prompt to install.

Then I thought that I'd give Xubuntu a shot, but got the same results as with Ubuntu, the progress bar stopped on the splash screen.  I left it running to see what would happen, and I eventually got this error message:

udevu-event [5510]:run_program: exec of program '/sbin/modprobe' failed 

Eventually, I threw in my XP disk, and it seemed to run that fine, I didn't complete the install of XP, but it seemed to work.

The computer is old, I can get a model number later today when I get home, but it's not *that* old.  2.7Ghz celeron chip, 1 gig RAM, 20 gig HD.  The only thing I can think of is it's a BIOS problem.

Thanks for any help that you can provide, and sorry I don't have more exact info available at the moment.

---

### Post by RomeReactor on 2009-01-11
Hi. Looking at the specs you posted, the machine should be more than adequate to install Ubuntu; it does sound more like a BIOS/hardware problem. Have you thoroughly checked that all the hardware is in working order, or clearing the BIOS? If you don't get more responses here, you can try searching or posting in the [Server]("http://ubuntuforums.org/forumdisplay.php?f=339") or [Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333") sections.

---

### Post by phenom5 on 2009-01-12
I posted this on the noob forum, and it was suggested I try posting here.

I want to setup a HTTP server using ubuntu server.  I have an old Compaq presario (S6020WM) with a 2.7 GHz Celeron, 1 gig RAM.  It has a hard drive that has XP on it, and I pulled a hard drive out of an even older machine that I have collecting dust to use as the HDD to run ubuntu.  It has an MSI MS-6577 mobo, and a Phoenix Award BIOS.  

I went through the install, and everything seemed okay, but when I tried to boot, it wouldn't.  It would run through a few screens of text, and ultimately stop at this point...

[img]http://i72.photobucket.com/albums/i174/freakshow_4198/IMG_0177.jpg[/img]

***Note-this is not my screenshot.***

The numbers on the left side [**.*****] increase.  It starts at [90.55022] and slowly, and seemingly randomly increases.  Ultimately I left it over night, and for most of the day while I was at work, just to see what happened.  When I got back to it, some 19 hours later, it was still at that point, up to [3xxx.xxxxx].

My first though was that the hard drive was bad, so then I started to try some other Linux builds.  I tried running ubuntu liveCD, and I tried booting from the CD.  I got to the splash screen, but the progress bar eventually stopped, and it ultimately led to this error message:

udevu-event [5510]: run_program: exec of program '/sbin/modprobe' failed

Tried Xubuntu with a similar result.

Then I tried Windows Server 2008.  I booted from the DVD, and it loaded the files, the background loaded, but the prompt to change the admin password never appeared, and the install prompt never appeared.

So then I loaded the XP disk, and it ran no problem.  

I had no problems running any of the Linux builds on my laptop, and I was able to install Server 2008 on a partition on my laptop without any problems.

I think that the BIOS only supports XP.  

Anybody know of any workarounds for this?  Or does anybody have any other suggestions?

Thanks.

---

### Post by damphoud on 2009-01-12
How old is this HD? Can you find the manufacture name and model number?

---

### Post by phenom5 on 2009-01-12
It' old...20Gig, Western Digital WD200.

I want to keep XP on this computer, just as an emergency backup, in case there's trouble with my laptop.  But I could install XP on the old WD HD, and try to install ubuntu on the HD that currently has XP...if you think that would make a difference.

---

### Post by phenom5 on 2009-01-12
Issue is resolved...sort of.

After trying ubuntu server, ubuntu 8.10, xubuntu, & vectorlinux...fedor 10 works.

Thanks.

---

