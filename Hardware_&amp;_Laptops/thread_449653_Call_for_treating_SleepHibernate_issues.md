---
title: "Call for treating Sleep/Hibernate issues"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by Pixie25 on 2007-05-20
Ok, So we want ubuntu to take over dominance in computer world. I agree, we have to solve bug #1, but I am a student and most of my colleagues have laptops. I can't even think to offer them to try linux - and especially ubuntu (even though it's my favourite distro). And here is why:
Since dapper drake, which convinced me to switch completely to ubuntu I have various issues with hibernation and suspent to RAM. I've submitted bugs, googled for solution but I can't find a solution. I just can't quickly suspend my laptop or hibernate it. I've gone through all the related bugs in launch pad. It seems most of them are in status unconfirmed, or not important. I don't really see why. 
If Canonical wants to dominant computer world it should especially aim toward superb laptop support ! MOST of the people purchase laptops and care and love them. Long battery life and quick access is really important for them. 
And if you think I am just crazy and suspend to ram doesn't work only on my laptop (HP compaq NX6110) check this list of bugs I've made through browsing launch pad: 

Here is what I've submited: [https://bugs.launchpad.net/bugs/63198](https://bugs.launchpad.net/bugs/63198) 
The work around I've submitted isn't working all the time, and it often fails to wake up the laptop. 
So now, sleep is ok - but not wake up ! :(

And other people's bug numbers: 46545,63198,63834,50031,68423,74980, 80459,89269,94133,45759,64646,66255,66337,75905, 96402,30124, 36553,63435, 64070,67534,81667,89141,93576,86099,61405, 62630, 64070, 67341, 92461, 114579, 34960
these are all ignored or not taken seriously and here is one in progress:
50031 in progress

It feel like this issue is not getting the attention it needs.

So, if you been patience enough to read my grievance and you use ubuntu on your laptop and  fill like me about that issue, please write it here, report bugs so the guys in canonical will take of it. lf you can  submit patches it's even better, sorry I can't..

Oz.

---

### Post by benanzo on 2007-05-20
I completely understand your grievance.  I also struggled with suspend/hibernate until I decided to bite the bullet and buy a machine with 100% compatible hardware.  That is really the only way to get proper support because it does two things:

1) It forces non-supported-hardware makers to take notice that few are buying their machines and possibly spur them to start committing some code into the kernel.  Some might say that those manufacturers simply don't care if no Linux user is buying their machines, but I think that is wrong.  Just look at AMD's [[COLOR="Green"]recent change of heart[/COLOR]]("http://linux.slashdot.org/article.pl?sid=07/05/13/1659245&from=rss") since ATI gained such a miserable reputation when compared to nVidia (only slightly better) or Intel (completely open-source) with their graphics drivers.  Linux users have bigger influence than I think we realize.

2) It furthers the prevalence of OSS compatible hardware in the whole ecosystem.  While this ties closely to the first point, it goes further by implying that if there is more Linux-friendly hardware being used that not, it furthers the opportunity for Linux adoption by non-Linux users.  In short, even if someone's not using Linux, there is a greater chance that you are still running OSS-compatible hardware, making the eventual transition easier.

Also, it does not seem to me that the Ubuntu developers are *ignoring* the power management problems currently existing.  These are long-standing issues that are being heavily worked on upstream by the kernel-acpi people.  Ultimately, the component manufacturers should be committing most of the code (in fact, Intel is committing a significant amount) but that doesn't mean no one else is working on it.  These are major issues that require quite a bit of work.  ACPI, Wireless etc are all being worked on heavily.  If you want a bird's-eye-view, subscribe to the linux-kernel-mailing-list and linux-acpi.  That's were the code is being written.

---

### Post by Sweet Mercury on 2007-05-21
> **benanzo said:**
> I completely understand your grievance.  I also struggled with suspend/hibernate until I decided to bite the bullet and buy a machine with 100% compatible hardware.  That is really the only way to get proper support because it does two things

That might help you, or I, but it certainly doesn't convince the friends and families to switch over.

OP: I have the same issue, though it's not an imperative for me. Hibernate works just fine (though when I come out it seems like the screen savers won't come on), but suspend, which I would prefer to use, doesn't. I don't know what exactly the problem is, but when I come out of suspend, all I get is a semi black screen.

---

### Post by H.E. Pennypacker on 2007-05-23
I completely agree with the OP.  Unlike most people, I have the patience to scour the Internet for solutions, and answers.

> 
I completely understand your grievance. I also struggled with suspend/hibernate until I decided to bite the bullet and buy a machine with 100% compatible hardware. 

I don't know what my hibernation/suspend problems have to do with hardware.  I don't recall hibernation/suspend issues with Dapper or Edgy.  How is it that my hardware has gone completely unsupported from Edgy to Feisty?  That can't be.  My hardware is used by many people (Broadcom wireless card, Intel graphics card, etc.).  

Besides, Feisty is a relatively minor upgrade.  Gnome was upgrade, and a few other things, but nothing that would destroy my laptop's ability to hibernate or suspend.  It doesn't make sense that a few software changes should so drastically impact hibernation/suspend.

> Also, it does not seem to me that the Ubuntu developers are *ignoring* the power management problems currently existing.

I am sure they are not ignoring the problems, but launchpad leaves some people hopeless when they see so many bugs open for one reason or another (e.g. unconfirmed).  

I am really disheartened by all the threads I have come across that do NOT provide a solution to this problem.  Most hibernation/suspend threads feature people TALKING about their problems,  and once in a blue moon, you'll find someone offering a possible solution, a solution that may not work at all.

---

### Post by NooneReally on 2007-05-23
this isn't really a solution as you've already gone too far in the upgrade process...but...what i've gotten into a habit of doing is backing up /etc, which is where the suspend scripts are located, so that as I've gone from dapper->edgey->feisty if suspend/hibernate ever stop working at least I can see if it was a simple script modification fix that I could work out. I did have to make a correction (can't remember what now) from dapper->edgey, but since I just wiped and put feisty on fresh I don't know if anything would've happened from edgey->feisty. 

A fresh install of feisty though has *everything* working 100% on my laptop, a dell 640m/e1405. Only regression I've noticed is a slight degredation of signal quality from  the ipw3945 wireless driver, but this barely affects me.

---

### Post by H.E. Pennypacker on 2007-05-24
> **NooneReally said:**
> this isn't really a solution as you've already gone too far in the upgrade process...but...what i've gotten into a habit of doing is backing up /etc, which is where the suspend scripts are located, so that as I've gone from dapper->edgey->feisty if suspend/hibernate ever stop working at least I can see if it was a simple script modification fix that I could work out. 

Oh God, why didn't I think of this!  The moron I am didn't tell me I should have backed up /etc and equally important directories.  Smart of me.

---

### Post by DavidFourer on 2007-05-26
My main gripe with Feisty is that suspend/resume only works for about a day of turning the computer off and on.  Then I loose wired internet connection and can't get it back till  I reboot.  It seems there are as many suspend problems as there are laptop hardware configurations.  Most of the forum stuff I've found is over my head in hacker depth.  Some rational method of tracking down problems, (error log files?) would be helpful.  I know the system is identifying some errors as they flash on the screen for a half-second during boot or resume.  I can't read any of it.  At least error messages can be googled!

The kernel 2.6.15.x was the one that worked perfect for me.  When 2.6.17.x came out I changed my grub menu.lst file after each upgrade to use the older working kernel.  Feisty brought 2.6.20 and I'm living with the bugs.  (Dell Inspiron 6000, Intel 915GM graphics, Broadband wireless never worked)

---

### Post by H.E. Pennypacker on 2007-05-28
> **DavidFourer said:**
> 
The kernel 2.6.15.x was the one that worked perfect for me.  When 2.6.17.x came out I changed my grub menu.lst file after each upgrade to use the older working kernel.  Feisty brought 2.6.20 and I'm living with the bugs.  (Dell Inspiron 6000, Intel 915GM graphics, Broadband wireless never worked)

Does the fact that we have the same graphics card explain our problem, possibly?  I too had luck with an older kernel, but it was 2.6.17 (Edgy).  I believe 2.6.15 was Dapper.  The upgrade to Feisty ruined my ability to hibernate/suspend (both).

Your Broadcom card should work.  It works for me.  By the way, if you don't mind spending about $20, buy an open source Intel wireless card.  You're probably not following the right guides.

---

### Post by DavidFourer on 2007-05-28
> **H.E. Pennypacker said:**
> Does the fact that we have the same graphics card explain our problem, possibly? A lot of the discussion about suspend leads to graphics cards, but I don't know what that has to do with losing Internet access or network access.  Seems to me my suspend/resume is pretty much working.  Internet goes to a cable modem and then to a 4-cable router in the house.  Sometimes after resume, Network Manager says I have connection but I get "can't locate [www.google.com--try](www.google.com--try) again?  I reboot and it's good.
> Your Broadcom card should work.  It works for me.  By the way, if you don't mind spending about $20, buy an open source Intel wireless card.  You're probably not following the right guides.I followed [http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+wireless+feisty](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+wireless+feisty) and tried the ndiswrapper method.  I have not gotten around to trying the open source driver described in same HOW TO.  Can I get just any Intel wireless card or do I have to get a certain one?

---

### Post by H.E. Pennypacker on 2007-05-29
> A lot of the discussion about suspend leads to graphics cards, but I don't know what that has to do with losing Internet access or network access. Seems to me my suspend/resume is pretty much working. Internet goes to a cable modem and then to a 4-cable router in the house. Sometimes after resume, Network Manager says I have connection but I get "can't locate [www.google.com--try](www.google.com--try) again? I reboot and it's good.

The graphics card has nothing to do with your connection problems.  You probably failed at one point or another when following a guide.  This probably is causing your Internet problems.  It's all a game of seeing what works and what doesn't.  You have to isolate the problem, and see what is causing it.

> 
I followed [http://ubuntuforums.org/showthread.p...eles](http://ubuntuforums.org/showthread.p...eles) s+feisty and tried the ndiswrapper method. I have not gotten around to trying the open source driver described in same HOW TO. Can I get just any Intel wireless card or do I have to get a certain one?

You've linked to the right guide.  That's the one that should work for most people.  Don't bother with the open source driver, because it may not work at all, and even if it does work, your speeds will not be the same as the proprietary driver.

You can't get just any Intel card.  Not all are open source.  There are some open source ones, and from what I have read, very easy to setup (not having to follow guides to connect to the Internet), and they work reliably.  See the following:

[http://ubuntuforums.org/showpost.php?p=2710450&postcount=8](http://ubuntuforums.org/showpost.php?p=2710450&postcount=8)

---

### Post by daschmidty on 2007-05-29
Everything worked OK for me for awhile, but then my laptop reached the point where it suspends great, but WILL not resume..not even if i press the power button, it goes totally dead unless i remove the battery and reboot. I tried installing uswsusp which made hibernate work but still no suspend. My desktop suspends fine w/ uswsusp and 2.6.20-15 but will not resume on 2.6.20-16. It's pretty irritating that hardware controllers get broken with every (even minor) upgrade.

---

