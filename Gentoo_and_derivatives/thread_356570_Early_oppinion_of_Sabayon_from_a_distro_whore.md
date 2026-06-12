---
title: "Early oppinion of Sabayon from a distro whore"
date: 2007-02-08
forum: Gentoo and derivatives
---

### Post by Scheater5 on 2007-02-08
I know there's a section for Sabayon talk, but I made a thread on this for FC6 so I thought I'd do it again for Sabayon.

Took me a while to actually try Sabayon.  My "sandbox" desktop that I've mentioned so much lately has a crappy graphics card, and what's the use in using Berly's official distro if I can't use an accelerated desktop?  Plus I've been scared off by Gentoo before - a couple months ago I tried the latest Gentoo and didn't even get as far as getting it installed.  The only thing harder than that I've ever tried was FreeBSD, and at least I got it on the harddrive (I just couldn't get X to work!)
Plus I don't have a DVD burner, and the Sabayon website is not nearly as intuitively laid out as the Ubuntu site - and they don't exactly advertise very well that the mini edition is everything the full version is, minus some little details (like the pre optimized kernels and the SuSE-style kicker) and the server stuff.  
Alright, so I finally figure out I can use it, and decide - what the hell, it's about time for a reinstall anyway, I'll put it on my laptop and try and get it to play nice with Kubuntu.
Well, it didn't play nice.  At least not for me.  I tried to use the same /home partition I did for Kubuntu, and they tried to read each others config files and it ended up a big mess.  I still don't completly understand why it went so bad, but it was definitely bad.  So, put in a prayer of thanks that I backed up anything important, and said screw it, I'm gonna just do a fresh install.

And now, my friends, the story gets good.  Install goes flawlessly, and almost everything works out of the box (still trying to figure out why my multimedia keys, which are mapped correctly, do nothing and why it recognizes my entire touchpad as a pointer controller instead of the edges as scroll zones - but everything, and I mean everything, else works great).  XGL and Beryl get along better with my ATI card than they ever did with SuSE or even Kubuntu.  
But, damn it, I still can't stand the portage system.  And the way it didn't get along so much with Kubuntu makes me wonder just how stable it is.  After all, they advertise "cutting edge."  I'll still keep a computer with Edgy on it, just in case.  I love the community and the philosophies -and Apt - of Ubuntu too much to leave it behind.  But I'm gonna give Sabayon a whirl as my primary for a couple months and see if I can still be productive.  I've already had a couple issues (the first time I updated and then synced portage, knetworkmanager broke), but I had issues with Kubuntu when I was a newbie, too.  
Thus far, my personal experience with Sabayon leaves FC6 in the dust, and outpaced SuSE by a good distance, too.  My initial experience with it has been better than my initial experience with Ubuntu, but I was also much less knowledgeable about Linux then.  It's also miles and above better than my experience with regular Gentoo.  I'll probably come back to Kubuntu, or maybe dual boot, especially when Feisty comes out (already tried Herd 2 and 3 - looks awesome, and some of the stuff in the works on Launchpad looks even cooler).  But if nothing else learning Gentoo via Sabayon will hold me over until 7.04.

---

### Post by RAV TUX on 2007-02-08
> **Scheater5 said:**
> I know there's a section for Sabayon talk, but I made a thread on this for FC6 so I thought I'd do it again for Sabayon.

Took me a while to actually try Sabayon.  My "sandbox" desktop that I've mentioned so much lately has a crappy graphics card, and what's the use in using Berly's official distro if I can't use an accelerated desktop?  Plus I've been scared off by Gentoo before - a couple months ago I tried the latest Gentoo and didn't even get as far as getting it installed.  The only thing harder than that I've ever tried was FreeBSD, and at least I got it on the harddrive (I just couldn't get X to work!)
Plus I don't have a DVD burner, and the Sabayon website is not nearly as intuitively laid out as the Ubuntu site - and they don't exactly advertise very well that the mini edition is everything the full version is, minus some little details (like the pre optimized kernels and the SuSE-style kicker) and the server stuff.  
Alright, so I finally figure out I can use it, and decide - what the hell, it's about time for a reinstall anyway, I'll put it on my laptop and try and get it to play nice with Kubuntu.
Well, it didn't play nice.  At least not for me.  I tried to use the same /home partition I did for Kubuntu, and they tried to read each others config files and it ended up a big mess.  I still don't completly understand why it went so bad, but it was definitely bad.  So, put in a prayer of thanks that I backed up anything important, and said screw it, I'm gonna just do a fresh install.

And now, my friends, the story gets good.  Install goes flawlessly, and almost everything works out of the box (still trying to figure out why my multimedia keys, which are mapped correctly, do nothing and why it recognizes my entire touchpad as a pointer controller instead of the edges as scroll zones - but everything, and I mean everything, else works great).  XGL and Beryl get along better with my ATI card than they ever did with SuSE or even Kubuntu.  
But, damn it, I still can't stand the portage system.  And the way it didn't get along so much with Kubuntu makes me wonder just how stable it is.  After all, they advertise "cutting edge."  I'll still keep a computer with Edgy on it, just in case.  I love the community and the philosophies -and Apt - of Ubuntu too much to leave it behind.  But I'm gonna give Sabayon a whirl as my primary for a couple months and see if I can still be productive.  I've already had a couple issues (the first time I updated and then synced portage, knetworkmanager broke), but I had issues with Kubuntu when I was a newbie, too.  
Thus far, my personal experience with Sabayon leaves FC6 in the dust, and outpaced SuSE by a good distance, too.  My initial experience with it has been better than my initial experience with Ubuntu, but I was also much less knowledgeable about Linux then.  It's also miles and above better than my experience with regular Gentoo.  I'll probably come back to Kubuntu, or maybe dual boot, especially when Feisty comes out (already tried Herd 2 and 3 - looks awesome, and some of the stuff in the works on Launchpad looks even cooler).  But if nothing else learning Gentoo via Sabayon will hold me over until 7.04.

I am glad to here you have had such great success...keep in mind that 3.0 will be released soon and Knetworkmanager is being worked on...

welcome to the small and growing family of Ubuntu/Sabayon users:popcorn:

---

### Post by Scheater5 on 2007-02-08
Thanx for the welcome - and the info - RavTux.  I knew neither of those things - that 3.0 was coming out soon or that knetworkmanager was being worked on.  What do I use to sign on the internet, then?  Or do I just not update portage until 3.0 comes out?

---

### Post by RAV TUX on 2007-02-08
> **Scheater5 said:**
>  do I just not update portage until 3.0 comes out?

yes

> emerge --sync> emerge portageI also routinely update indivdual packages....for example do

> emerge -s media-gfx/gimpto see if you have the latest gimp installed

if not simply:

> emerge media-gfx/gimpto update.....you can do most programs this way; Firefox, Beryl, KDE, etc, etc:popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by Scheater5 on 2007-02-09
But I can't just update portage - I've tried a fresh install from my mini edition cd three times now, and no matter what I do, when I update portage knetworkmanager breaks and I'm left unable to connect to the internet, either ethernet or wifi.  I'm going to try again today, emerge kwifi first and then "emerge portage" and at least then I should be able to connect to the internet, maybe get help from the their forums - but if that doesn't work I'm left with the option of reinstalling and then leaving portage alone until the next version comes out.  
BTW, in case anyone on this board knows the answer before I post this on the Sabayon forums - I've tried to install the SuSE-like kicker from the DVD version as per the instructions on the "Forum Usage" post stickied in General on the Sabayon forum to no avail.  Does anyone here know how to do that before I go off trying to figure out how the Gentoo and Sabayon documentation is organized??  Yea, I know, do your research before posting on a forum, but I don't know my way around the distro yet.

---

### Post by RAV TUX on 2007-02-10
> **Scheater5 said:**
> But I can't just update portage - I've tried a fresh install from my mini edition cd three times now, and no matter what I do, when I update portage knetworkmanager breaks and I'm left unable to connect to the internet, either ethernet or wifi.  I'm going to try again today, emerge kwifi first and then "emerge portage" and at least then I should be able to connect to the internet, maybe get help from the their forums - but if that doesn't work I'm left with the option of reinstalling and then leaving portage alone until the next version comes out.  
BTW, in case anyone on this board knows the answer before I post this on the Sabayon forums - I've tried to install the SuSE-like kicker from the DVD version as per the instructions on the "Forum Usage" post stickied in General on the Sabayon forum to no avail.  Does anyone here know how to do that before I go off trying to figure out how the Gentoo and Sabayon documentation is organized??  Yea, I know, do your research before posting on a forum, but I don't know my way around the distro yet.

I suggest instead of the forums go to:

irc.oftc.net #sabayon

to ask your question.

---

### Post by Scheater5 on 2007-02-10
Thanx again Rav Tux.  If I can't solve this problem that'll be the next place I go.

---

### Post by Nomearod on 2007-02-10
I formated my HD and installed Sabayon. So far, everything is working very well and I haven't found any major problem. Actually, the only thing that is not working is Democracy Player. Don't know why, but it doens't even start.

---

### Post by Rodneyck on 2007-02-10
> **Nomearod said:**
> I formated my HD and installed Sabayon. So far, everything is working very well and I haven't found any major problem. Actually, the only thing that is not working is Democracy Player. Don't know why, but it doens't even start.

Maybe a codec issue?  Look on the forum or as RAV suggested, try the IRC.

---

### Post by Scheater5 on 2007-02-12
Update:
I manager to get everything properly up to date and still working by following the instructions on the Sabayon wiki under tips-and-tricks.  There are apparently a few additional steps to properly update portage and your config files with Sabayon than with Gentoo - somehow related to the use of layman.  As I never used "regular" Gentoo, I can't say for certain what the exact differences are, but nonetheless, there are more steps than I was using.  Updated portage, and knetworkmanager still worked.  But, fed up with trying to get the mini to look and act like the full version, I broke down and decided to just use the full version.  
I borrowed my girlfriend's laptop for her DVD burner and torrented the full DVD iso.  This morning, burned a DVD and threw it in my laptop.  
Booted up great, except that it didn't recognize my touchpad correctly again - only this case was even worse than with the mini.  When I kept contact with the touchpad without moving the cursor would begin moving up of it's own accord.  Hoping that an install would work some magic and fix this, decided to go ahead and do a full install.  
Install went fine - after all the problems Anaconda was by now an old friend - and I booted into my new, full Sabayon.  But still the crazy cursor.  Luckily I managed to open the KDE control center and change my touchpad to an ALPS touchpad - now no more crazy pointer, plus the scroll edges work perfectly - it's a little touchy, but I suppose I'll get used to it.  I like the SuSE kicker (I've liked it since I started using SuSE on my sandbox computer) and Beryl still works great.:popcorn:  

 Now if only I could get the multimedia buttons to work...

---

### Post by rai4shu2 on 2007-02-12
That reminds me. I have a perfectly normal USB mouse and in Sabayon it behaved a bit wildly. Didn't think anything of it at the time because it was subtle and I could easily tweak it in kcontrol.

---

### Post by Scheater5 on 2007-02-13
Well, the multimedia keys aren't mapped correctly on the dvd version - and I've tried a couple of different methods of setting up scripts to get them to work with no success.  I can map them with xmodmap and they will work until I reboot...it's not that big a deal and I've had bad luck with scripting before (I'm definitely no programmer), so I think I'm just gonna let it be for a while.  Maybe come back to it closer to Feisty coming out since I'll have to do some work on the comp then anyway.  Until then, Sabayon is my primary.

---

