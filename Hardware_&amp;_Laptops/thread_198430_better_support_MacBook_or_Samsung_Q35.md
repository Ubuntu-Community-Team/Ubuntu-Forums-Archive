---
title: "better support? MacBook or Samsung Q35"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by mwerlberger on 2006-06-17
Hi all! As i just switched from Gentoo to Ubuntu yesterday i have a question about my future laptop. I just decide to by a new MacBook or the Samsung Q35. Of course i don't want to hear oh thats the better one in hardware because i can read facts ;-). But indeed i need your help. Are there anyone out there that installed Drapper on either the Samsung or the Apple thing? I'm kind of sure that i have no hardware isues within the samsung part but there meight be problems with the Apple hardware? Are the iSight camera going to work nativly or maybe within paralles? Are there some restrictions with the Apple combined with Drapper in comparison with the Samsung?

Ah yes one general question. What about the heat-issue according the MacBook? True or just horror-stories? What about battery? Are the 6 hours on the Samsung homepage realistic or just myth?

I hope somebody can give some review and advice.

Rgds,
 Manuel

---

### Post by nolongerlivecd on 2006-06-17
Both are true.

---

### Post by rob martin on 2006-07-22
I've just bought a samsung q35 and after the obligatory removal of the Win XP Pro installation, I have installed Ubutu 6.06.  

I am please to say that everything works, if not out of the box, but with a few minor tweaks. Will get round to putting together a more detailed post later.  

One minor irritation, the samsung seems very reluctant to return from suspend, in truth it doesn't without a Fn Prt Sc which immediately returns you to a fresh logon window i.e. starts a new session. 

Other than that very pleased with batttery life and performance.

Rob

---

### Post by snowjunkie on 2006-07-22
I've seen kubuntu 6.0.6 installed on a standard mac book using Parellels virtualisation software.  I was quite impressed by the performance of it.

---

### Post by mwerlberger on 2006-07-25
> **rob martin said:**
> I've just bought a samsung q35 and after the obligatory removal of the Win XP Pro installation, I have installed Ubutu 6.06.  

I am please to say that everything works, if not out of the box, but with a few minor tweaks. Will get round to putting together a more detailed post later.

I also bought the samsung q35. But i have some Problems with the installation. Did you add some custom parameters when booting or just the standard things?

Rgds,
 Manuel

---

### Post by rob martin on 2006-07-25
Manuel

Nothing special, wnet into bios setup (F2 at boot) and under Advanced changed "Large Disk Access Mode" to Other.

Then booted with Gparted Live CD and removed the windows partitions, created three primary partions for / /home and swap.  

Then rebooted with ubuntu cd (in safe graphics mode or something, can't quite remember) then installed as usual.  

Sound was an issue, high pitched noise but adding 

options snd-hda-intel index=0 single_cmd=1 model=laptop-eapd

to /etc/modprobe.d/alsa-base as detailed here [http://www.puzzle.ch/samsung_q35.html](http://www.puzzle.ch/samsung_q35.html) (note with dapper you do _not_ have to  install alsa or ieee80211 as it advocates on this site) everything works --- well almost

Issues with suspend & resume, which I'm hoping someone can help with, the machine suspends ok and on pressing the power button comes back to life, however the screen, whilst on, refuses to display the desktop, just a cursor on the top left, Fn Prt Sc forces a new session, so all is not lost, I'd just like to suspend and resume with all applications open, like I can on my Dell Latitude X1, and given that machine is actually a rebadged Q30, there should be no problem with the Samsung. 

Hope this is of some help.

---

### Post by rob martin on 2006-07-25
Quick reply to my own post.  The problem with the suspend/resume is NOT an ubuntu one.  I've been using quinn's repos for aiglx and compiz.  Switching to metacity before suspend the Q35 resumes Ok. 

Will file a bug with the compiz people.

---

### Post by e1_ang on 2006-12-08
I've been using Q35 for 3 months now. 
Battery never last >4 hours. The 6+ hours is in optimised mode, which Samsung actually states. 

Ubuntu 6.10 cannot install. I got "Loading Linux Kernel" at 44% and it's always stuck there. 
I tried the CD on other machine and it's fine. 
I checked the entire CD and it's fine. 
I disable my wireless. Nope..
I tried different combination in the boot option. Nothing work.
I tried noacpi etc. Not working...
I tried modifying relevant BIOS setting. No luck...

Someone had the same problem, and got it solved via DVD. I cant find the DVD option in the download area....

I'm going to try Edubuntu, although technically it should be the same problem as it's the same kernel.

---

### Post by mwerlberger on 2006-12-09
I'm using XUbuntu with my Q35. Works without a problem. I used to use Dapper and now switchted to Edgy. Just try to use the alternate CD. Maybe that works better. At least i had no problems installing with the alternate one.

rgds,
 Manuel

---

