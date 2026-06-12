---
title: "Need complete proof that Wubi is not dangerous, risk-free, etc."
date: 2008-11-25
forum: General Help
---

### Post by FaRReR on 2008-11-25
The other user of the computer needs Windows XP for her university work, etc...
I need absolute proof that Wubi will not harm the computer, so I can install Ubuntu on my external HDD. This proof has to be extremely seamless... thanks in advance! 

P.S. Wow, what a waste of a first post :P

---

### Post by doyouhas on 2008-11-25
...proof? You said you are install Ubuntu on an external HDD? So why would you need her consent? Tell her it´s not changing her system files in any way. There is no ¨proof¨ of this, just tell her not to be silly by thinking this would srew up her work.

---

### Post by sstusick on 2008-11-25
Wubi shouldn't harm her Windows install. Wubi will install under Windows like any other program and can be removed in the same way.

---

### Post by FaRReR on 2008-11-25
Well, the external HDD is quite important too, it holds about half of my programs and has ~50gb worth of stuff on it.

**Edit:** sorry (noob question) but can I use Wubi to install Xubuntu?

---

### Post by doyouhas on 2008-11-25
The external hard drive has nothing to do with an install of Wubi. As stated above, its like any other Windows program and can be removed like one as well.

---

### Post by tjko on 2008-11-26
I'm not sure what kind of "proof" you are looking for, but I have had Ubuntu 8.10 running for the past 4 days now after installing it through wubi.

The installation was very quick and simple (no need to burn the CD!). Have had no problems so far and yes, you can just remove the Ubuntu install through add/remove programs in windows control panel. 

There are only advantages to using wubi, as far as I know. What concerns you?

---

### Post by Zaraphrax on 2008-11-26
> **sstusick said:**
> Wubi shouldn't harm her Windows install. Wubi will install under Windows like any other program and can be removed in the same way.

+1. And, Wubi doesn't require a seperate bootloader (which is always something to worry about screwing up when it comes to running multiple operating systems), therefore you have a 1 in 1x10^75 chance of screwing something up.

If she still isn't comfortable, just use Virtualbox or VMWare.

---

### Post by Swagman on 2008-11-26
If she's that paranoid then show her this post (her paranoia) and then go buy a usb pendrive (8gb min) and install *AnyBuntu to the pendrive.

plugin your USB HD then boot the computer from the pendrive.

Another Job sorted.

Splendid

/rings bell

NEXT !!

---

### Post by Yownanymous on 2008-11-28
Well here's proof: I've been using Wubi without fail for 2 months. NOTHING has changed on my Windows filesystem in all the times I've uninstalled, reinstalled...

---

### Post by ago on 2008-12-01
If you do not pull the power cable or pull the hard disk while it is in USE then it is ok. If you do you need to run chkdsk /r from windows.

---

### Post by Jammanuser on 2008-12-02
> **ago said:**
> If you do not pull the power cable or pull the hard disk while it is in USE then it is ok. If you do you need to run chkdsk /r from windows.

true...but occasionally (if u have Vista, that is!) ur computer freezes up, and u absolutely HAVE to do an improper shutdown! i am having that problem with Vista quite a lot now, on a practically brand-new Dell laptop computer...its quite annoying!!! sometime there's no way around hard rebooting...

speaking about "chkdsk /r"...i had a problem with my wubi install recently! ubuntu 8.10 wouldn't boot...i installed it on top of my Vista OS, using wubi-installer, and for about oh-i-don't-know-a week-maybe.. it worked great (this is for all of u who were commenting on how "great" wubi is!), and then a couple days ago, when i tried to boot into ubuntu as before...what happens? i get a stupid error, saying: "crc error" and then on next line "system halted"!!! :mad: i asked around, including here, but no one had any **real** solutions...u r after all, Ago, the person who suggested that i run "chkdsk /r" (thanks by the way! :)), which i did, after which i almost lost access to my Vista OS...a BSOD came up, saying that a problem had been detected on my computer, and my computer had been "shutdown" to prevent damage from being done to it (although the damage had CLEARLY already taken place!)...well, after that, i booted into Vista once, but the computer froze at startup, after the Welcome screen, and when i hard rebooted AGAIN (i had no other choice!), i could no longer boot into Vista OR ubuntu anymore! :mad: i had to run Startup Repair in order just to get back into Vista again!

Just a little word to the wise...

Cheers!n:)

---

### Post by Jammanuser on 2008-12-02
> **tjko said:**
> I'm not sure what kind of "proof" you are looking for, but I have had Ubuntu 8.10 running for the past 4 days now after installing it through wubi.

The installation was very quick and simple (no need to burn the CD!). Have had no problems so far and yes, you can just remove the Ubuntu install through add/remove programs in windows control panel. 

There are only advantages to using wubi, as far as I know. What concerns you?

4 days is hardly enough time to base ur assumption that Wubi is problem-free on!!! try a WEEK! my Wubi install failed after about that time, and i STILL haven't got it fixed! :mad:

---

### Post by Jammanuser on 2008-12-02
> **Yownanymous said:**
> Well here's proof: I've been using Wubi without fail for 2 months. NOTHING has changed on my Windows filesystem in all the times I've uninstalled, reinstalled...

well...lucky u! frankly i'm AMAZED that wubi lasted that long for u! mine only lasted about a week, before i could no longer boot into it, because a stupid "crc error"! :guitar:

u must not have Vista (as i do)...

word to the people who r thinking of GETTING Vista: DON'T!!! u will most CERTAINLY regret it! :)

---

### Post by Jammanuser on 2008-12-02
> **FaRReR said:**
> The other user of the computer needs Windows XP for her university work, etc...
I need absolute proof that Wubi will not harm the computer, so I can install Ubuntu on my external HDD. This proof has to be extremely seamless... thanks in advance! 

P.S. Wow, what a waste of a first post :P

there IS no absolute proof that Wubi will work for u, and not harm ur computer! TRUST me! :) if u like Ubuntu so much, then i suggest that u try installing it on a separate partition than XP...anything REMOTELY attached to anything made by Microsoft will CONSTANTLY be having problems! DON'T do it! don't install wubi...i'm STILL trying to figure out the problem that arose with it about the "crc error", after at least 3 days! already i'm beginning to regret not having installed ubuntu 8.10 on a completely separate partition, and having used wubi instead! now i have no way to recover my important work that i did in ubuntu...thanks to Wubi! :mad:

but who knows? could have been just STUPID Vista!!! :)

Cheers!

---

### Post by magmon on 2008-12-02
[http://www.pcworld.com/downloads/file/fid,72716-page,1-c,downloads/description.html](http://www.pcworld.com/downloads/file/fid,72716-page,1-c,downloads/description.html)

As said in the review on the above page, wubi is safe and it works. I have had it running for about 3ish months now, with only one error after install that required a reinstall (No biggie, no damage to my vista or files therein). A warning though, "power killing" your computer may damage the ubuntu installation. I recommend using your external HD for backing up her windows, and simply install wubi as usual. So, if the rare (hehe, or not) case that wubi doesn't work is yours, simply back up from the HD and your good to go.


Btw Jamman, theres an edit button for a reason.

---

### Post by ago on 2008-12-02
> **Jammanuser said:**
> true...but occasionally (if u have Vista, that is!) ur computer freezes up, and u absolutely HAVE to do an improper shutdown! 

There are often workarounds, the first thing to try it to get to a console via:

ctrl + alt + f2 
alt + SysRQ + R + ctrl + alt + f2
via remote ssh

And if you need to reboot forcefully, usually the following command works well even when ctrl+alt+del fails:

Alt + SysRQ + R + S + U + B

---

### Post by Jammanuser on 2008-12-02
> **ago said:**
> There are often workarounds, the first thing to try it to get to a console via:

ctrl + alt + f2 
alt + SysRQ + R + ctrl + alt + f2
via remote ssh

And if you need to reboot forcefully, usually the following command works well even when ctrl+alt+del fails:

Alt + SysRQ + R + S + U + B

hmm...ok! i'll try that next time! but does that work on Vista, or just on ubuntu? and what is "SysRQ"??? do u simply mean those letters pushed in sequence, one after the other, or is there actually a button called that somewhere on my keyboard, and i'm just missing it???

Looking forward to ur reply... :guitar:

---

### Post by CTRLurself on 2008-12-02
> **Jammanuser said:**
> 
word to the people who r thinking of GETTING Vista: DON'T!!! u will most CERTAINLY regret it! :)

First off, this is ridiculous. I've been using Vista (premium and ultimate) on two computers, with two radically different hardware configurations since May 2007, and even through a dozen upgrades between the two of them, I've never ONCE gotten a BSOD, or even a total freeze. Learn to use and OS properly before you start bashing it.

As far as Wubi is concerned, I've used it, it works, it's a bit unstable, but as long as you know what you're doing in WINDOWS you shouldn't have any issue with it damaging WINDOWS, your Ubuntu install however may be a bit unstable.

I've been using VMWare fusion for a while now, and never had an issue with ubuntu/OSX/XP PRo/fedora booting in it (I VM a lot), Wubi however went down on me after about 2 weeks, but i just uninstalled/reinstalled it, and kept using it til I got my hands on better software (VMWare).

Honestly, if your THAT paranoid about damaging windows, buy an internal HDD, burn a live CD, install to that 2nd internal HDD, and use GRUB bootloader to choose which OS to use when you start up your computer. You can even set the default to windows if you want.

Or, buy a flash drive, and make it your ubuntu install, but you'll have to manually tell it to boot off of the flash drive everytime (or change your boot order in BIOS to default to USB and it will boot from the flash drive when it's present).

Using a virtual machine (such as Wubi or VM Ware or Parallels) is NEVER as good as a proper install, but it is a much easier way to get your feet wet with a new OS without having to re-partition your HDD. If you're paranoid then use a flash drive it'll boot kind-of slowly, but it'll work better than Wubi and still pose NO VIABLE THREAT TO WINDOWS UNLESS YOU DON"T KNOW WHAT YOU"RE DOING. If you're serious about Ubuntu, it is DEFINATELY worth getting another internal HDD and doing a proper install.

And I don't mean this to be insulting to Jammanuser, but if you're having that many issues with Vista, I can almost garuntee you that it's an EBUAK error. check you're services, boot processes, active processes -- strip out some of the junk (there's a lot preloaded on Vista when you get it with a computer preloaded), the MINIMUM number of processes on a CLEAN install is 35 if you're using 32-bit and 37 processes if you're using 64-bit Vista. If you look at Task manager and you have 70 processes, don't blame Vista for instability, clean off your computer.

---

### Post by Jammanuser on 2008-12-02
> **CTRLurself said:**
> First off, this is ridiculous. I've been using Vista (premium and ultimate) on two computers, with two radically different hardware configurations since May 2007, and even through a dozen upgrades between the two of them, I've never ONCE gotten a BSOD, or even a total freeze. Learn to use and OS properly before you start bashing it.

As far as Wubi is concerned, I've used it, it works, it's a bit unstable, but as long as you know what you're doing in WINDOWS you shouldn't have any issue with it damaging WINDOWS, your Ubuntu install however may be a bit unstable.

I've been using VMWare fusion for a while now, and never had an issue with ubuntu/OSX/XP PRo/fedora booting in it (I VM a lot), Wubi however went down on me after about 2 weeks, but i just uninstalled/reinstalled it, and kept using it til I got my hands on better software (VMWare).

Honestly, if your THAT paranoid about damaging windows, buy an internal HDD, burn a live CD, install to that 2nd internal HDD, and use GRUB bootloader to choose which OS to use when you start up your computer. You can even set the default to windows if you want.

Or, buy a flash drive, and make it your ubuntu install, but you'll have to manually tell it to boot off of the flash drive everytime (or change your boot order in BIOS to default to USB and it will boot from the flash drive when it's present).

Using a virtual machine (such as Wubi or VM Ware or Parallels) is NEVER as good as a proper install, but it is a much easier way to get your feet wet with a new OS without having to re-partition your HDD. If you're paranoid then use a flash drive it'll boot kind-of slowly, but it'll work better than Wubi and still pose NO VIABLE THREAT TO WINDOWS UNLESS YOU DON"T KNOW WHAT YOU"RE DOING. If you're serious about Ubuntu, it is DEFINATELY worth getting another internal HDD and doing a proper install.

And I don't mean this to be insulting to Jammanuser, but if you're having that many issues with Vista, I can almost garuntee you that it's an EBUAK error. check you're services, boot processes, active processes -- strip out some of the junk (there's a lot preloaded on Vista when you get it with a computer preloaded), the MINIMUM number of processes on a CLEAN install is 35 if you're using 32-bit and 37 processes if you're using 64-bit Vista. If you look at Task manager and you have 70 processes, don't blame Vista for instability, clean off your computer.

ok...first off, i NEVER said that wubi had damaged or possibly WOULD damage Windows!!! u misunderstood me!!! what i said was simply that i thought perhaps that the issue i had with wubi was Vista-related...which i'm almost 100% sure that it was/is!!! ur probably right about the processes though...i have been meaning to clear some of the unwanted processes off my system for a while now, but never got around to actually doing it!!! granted that that could be **part** of the problem/problems that i've been having with Vista, but i'm quite certain that its not all of it! Vista sucks...period, and anyone who has actually tried another OS (as i have!), even XP, ought to agree with me that Vista currently has WAY too many bugs in the system...and anyone with any SENSE would want to switch OS's PERMANENTLY, if possible, to something like ubuntu or Mac OS X! as for me, that's not possible right now, because i've been using Windows for so long, and so have got accustomed to certain programs that only work in Windows...not to mention all the games that r made SPECIFICALLY for Windows!

actually, i've already made up my mind that the next computer that i'm going to buy will be a Mac...the beauty with them is, that u can always dual boot with OS X and Windows, so u'll have the best of BOTH worlds! ;)

incidentally, what ever gave u the idea that i was paranoid about wubi damaging Windows, anyway? maybe u should actually try reading the comments before opening ur pie hole! :mad:

and on another note...if u like Vista so much, what r u doing here at the ubuntu forums, anyway????

):P

---

### Post by magmon on 2008-12-02
Dude, I read the first sentance of your post and didnt need to see more. Vista simply cannot dammage something because it feels like it. If you do something wrong, it will effect everything on the computer. And, if your booting into ubuntu, how is vista doing ANYTHING while your there?? I too use vista (home basic), and with the proper anti malware programs and firewall, you wont have any problems.

And is the rudeness really necessary?! These are other people and their opinions, nothing to get worked up about.

---

### Post by Jammanuser on 2008-12-02
> **magmon said:**
> Dude, I read the first sentance of your post and didnt need to see more. Vista simply cannot dammage something because it feels like it. If you do something wrong, it will effect everything on the computer. And, if your booting into ubuntu, how is vista doing ANYTHING while your there?? I too use vista (home basic), and with the proper anti malware programs and firewall, you wont have any problems.

And is the rudeness really necessary?! These are other people and their opinions, nothing to get worked up about.

Dude, that is YOUR opinion, but not a correct one, in my view... ;)

Vista has a tendency, for me at least, to freeze up at startup, i.e. after the Welcome page, and before the computer has finished starting up its startup programs!!! 

now HOW is that MY fault??? and if i have to hard reboot because of it, and that's what screwed up my wubi install (which i think it was!), then Vista DID indeed damage something without me "doing anything wrong"!!! and i never said that Vista was doing anything while i was booted into ubuntu!!! u have read wrong my posts also!!! **obviously** Vista didn't screw it up while i was in ubuntu...rather it screwed it up while i was in Vista!!! :mad:

as for the rudeness...i was simply responding in kind to the guy's post! :guitar:

---

### Post by CTRLurself on 2008-12-02
> **Jammanuser said:**
> Vista sucks...period, and anyone who has actually tried another OS (as i have!), even XP, ought to agree with me that Vista currently has WAY too many bugs in the system...and anyone with any SENSE would want to switch OS's PERMANENTLY, if possible, to something like ubuntu or Mac OS X! 
Admittedly, Vista is not God's gift to mankind, but it's doesn't suck. It's pretty convenient to use (indexed searches, the new start bar, better use of default active fields, etc) but it does take some setup to get it to a point where its running optimally. And you're talking to a guy who still uses command prompt in windows regularly to compile archives because that's how I used to have to do it in the days of DOS and 5.25" floppies. Saying/implying I've never used another OS is foolish.

> **Jammanuser said:**
> incidentally, what ever gave u the idea that i was paranoid about wubi damaging Windows, anyway? maybe u should actually try reading the comments before opening ur pie hole! :mad:
you're not the one who started this thread. The OP stated that (and I quote) "I need absolute proof that Wubi will not harm the computer, so I can install Ubuntu on my external HDD. This proof has to be extremely seamless" that sounds a bit like the other person is paranoid - as i would be if somebody else was doing an OS install on my computer. This thread is not all about you nomatter how indignant you get about it, I was addressing the OP and his issue.

> **Jammanuser said:**
> and on another note...if u like Vista so much, what r u doing here at the ubuntu forums, anyway????
Apparently it's your turn to read. I use ubuntu, fedora, vista ultimate 64-bit, xp pro 32-bit and OSX on my desktop with Vista being my host environment, and all others as VM's. I use everything because I do programming, web design and a few other things where I need to be able to test them cross-platform, and offer support cross platform. I also have 3 email clients, and 7 homepages in Firefox, I run a company off of my desktop, so I use it to do EVERYTHING. Ubuntu specifically is currently being used for Octave (MATLAB equivalent) and I'm learning C programming, and it's much easier to use build essentials in terminal than setting up the free C compiler available in Windows.

> **Jammanuser said:**
> 
Vista has a tendency, for me at least, to freeze up at startup, i.e. after the Welcome page, and before the computer has finished starting up its startup programs!!! 

as for the rudeness...i was simply responding in kind to the guy's post!
Freezing at start-up (at/after the welcome screen especially) is a sure sign that your personal account on the computer has too many icons, too many start-up programs, too many processes, spyware, and it may be all or only a few of the above.

As for the rudeness, I apologize, I did not intend for it to come out that way, I was merely attempting to point out that you are most-likely blaming the wrong thing for your problems. And just so you know. My next laptop is also gong to be a macbook. They are great for a mobile platform (and handles VM's well), but my desktops are always custom built.

---

### Post by Virtua-Touch on 2008-12-02
Wubi is ABSOLUTELY safe. It uses virtual disks to manage the partitions. (SO, there are virtual partitions, no partition is actually involved)

---

### Post by Jammanuser on 2008-12-02
> **CTRLurself said:**
> Admittedly, Vista is not God's gift to mankind, but it's doesn't suck. It's pretty convenient to use (indexed searches, the new start bar, better use of default active fields, etc) but it does take some setup to get it to a point where its running optimally. And you're talking to a guy who still uses command prompt in windows regularly to compile archives because that's how I used to have to do it in the days of DOS and 5.25" floppies. Saying/implying I've never used another OS is foolish.


yeah...i'm accustomed with Vista's cool features, lol! that's **one** of the reasons why i'm not planning on doing away with Vista completely...that, and also (besides of course the reason/reasons that i already mentioned!) because i'm hoping/thinking that Vista might get better later on down the road...possibly becoming the NEW XP, and XP would go the way of Windows 2000! that's why i'm not going to do away completely with Vista...admittedly suggesting that u hadn't used any other OS, or did not perhaps have any experience with them was stupid of me, i know! but i HAD to have something to shoot back at u in return, lol! ;) 

> **CTRLurself said:**
> 
you're not the one who started this thread. The OP stated that (and I quote) "I need absolute proof that Wubi will not harm the computer, so I can install Ubuntu on my external HDD. This proof has to be extremely seamless" that sounds a bit like the other person is paranoid - as i would be if somebody else was doing an OS install on my computer. This thread is not all about you no matter how indignant you get about it, I was addressing the OP and his issue.


ok...sorry then! i had the mistaken impression that u directed the comment at me! i apologize, lol! 

> **CTRLurself said:**
> 
Apparently it's your turn to read. I use ubuntu, fedora, vista ultimate 64-bit, xp pro 32-bit and OSX on my desktop with Vista being my host environment, and all others as VM's. I use everything because I do programming, web design and a few other things where I need to be able to test them cross-platform, and offer support cross platform. I also have 3 email clients, and 7 homepages in Firefox, I run a company off of my desktop, so I use it to do EVERYTHING. Ubuntu specifically is currently being used for Octave (MATLAB equivalent) and I'm learning C programming, and it's much easier to use build essentials in terminal than setting up the free C compiler available in Windows.


WOW!!! knowing how to run and maintain all those OS must be tough! i'm surprised that u or anybody else can do it! lol 

as for it being my time to read...actually, i already read that bit about the operating systems u use, even before making that comment! :D however, i chose that as the thing to jump on, simply because i suspected that u might not have had much experience with Vista, and were defending it without any basis of fact! and of course i had to have something to arm my cannon with... ;)

anyway, i apologize for making that comment, and anything else that might have upset u! lol obviously, someone who has all that stuff u mentioned, knows his stuff with computers!

Cheers! :guitar:

> **CTRLurself said:**
> 
Freezing at start-up (at/after the welcome screen especially) is a sure sign that your personal account on the computer has too many icons, too many start-up programs, too many processes, spyware, and it may be all or only a few of the above.


good points, and some of which i will be sure to check out...i already know that i have way too many processes and startup programs running, and have been meaning to fix it, but for some reason, have never got around to actually doing it yet! ;)
as for it possibly being spyware...i'll veto **that** one immediately, as i have already **recently** run scans with anti-spyware programs (namely CounterSpy, and a few free ones), and have removed all the spyware found...so i'm pretty sure that that's not the problem at the moment!

Cheers! 

> **CTRLurself said:**
> 
As for the rudeness, I apologize, I did not intend for it to come out that way, I was merely attempting to point out that you are most-likely blaming the wrong thing for your problems. And just so you know. My next laptop is also gong to be a macbook. They are great for a mobile platform (and handles VM's well), but my desktops are always custom built.

no harm done! :D i apologize for **my** rudeness as well...perhaps i said (i mean typed!) things a **little** too hastily! i know this isn't much of an exuse, but i've had a lot on my mind lately, mainly working on the crc error (which **continues** to piss me off, by the way!), and doing other things as well...sometimes i don't think before opening **my** pie hole! :D  i didn't/don't mean to offend anyone on this forum with all the negative stuff that i've posted about Vista here...its just that i've been having a lot of problems with Vista lately (mainly the one that i've already mentioned, i.e. the freeze-up at startup), after only having it for a few months...at least on the laptop computer that i'm using right now to type this comment with! i'm glad ur planning to get a Macbook, lol! i've heard they're really nice...that's what i'm planning to get as well...once i have the money! 

Cheers! :D

---

### Post by Jammanuser on 2008-12-02
> **Virtua-Touch said:**
> Wubi is ABSOLUTELY safe. It uses virtual disks to manage the partitions. (SO, there are virtual partitions, no partition is actually involved)

yeah...i agree that wubi is probably safe enough...i never said anything to the contrary! i simply said that Vista was most probably the original cause of my crc error, that is, Vista freezing up on me, forcing me to hard reboot, was most likely what caused the crc error! i'm sorry if people took it the wrong way!

Cheers! :guitar:

---

