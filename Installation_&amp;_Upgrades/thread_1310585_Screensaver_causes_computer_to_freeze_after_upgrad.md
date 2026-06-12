---
title: "Screensaver causes computer to freeze after upgrading from Jaunty 9.04 to Karmic 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by lerasch on 2009-11-01
Upgraded from 9.04 to 9.10.  Everything works fine until the screen saver activates. Screen goes blank and system totally freezes. Have to manually turn the computer off.  

Went to "System / Preferences / Screensaver" and selected "Feedback" to see what it looked like and caused the system to totally freeze.  Now if I go to "System / Preferences / Screensaver" the computer immediately freezes and I have to press the power button to shut the computer down.  I can not change any screensaver preferences nor disable the screensaver.

I have a Gateway 500S desktop with a Pentium 4 CPU, 512MB of RAM and an Intel 82845G graphics controller with driver version 6.14.10.3722.

The system worked great with Jaunty Jackalope version 9.04.

I'm a newbie to Ubuntu.  Any suggestions for fixing my freezeup problem?

---

### Post by billrad1 on 2009-11-01
I have a similar problem. My computer freezes after a long while with the screensaver running. I have 8 gigs of memory, running the 64 pae kernel.

billad1

---

### Post by lerasch on 2009-11-03
Fixed the problem by reinstalling version 9.10 from a CD.  No more freezeups caused by the screensaver activating.

---

### Post by Topsiho on 2009-11-03
I guess the freeze is caused by the absence of a file after the upgrade. The screensaver needs the file but can not find it anymore. It should report this, but it doesn't. It just searches for something that's not there, but used to be. So two errors here: one in the upgrade process and one in the screensaver.

Personally I have become very wary of screensavers, as almost all freezes that I have experienced so far (in Linux) were caused by (some) screensavers.

Topsiho

---

### Post by kgarbutt on 2009-11-03
I have the same problem on my hp Compaq d530 CMT desktop with 32-bit karmic. The display turns black and freezes. This never happened in Jaunty. It just started do it since my upgrade to Karmic. I guess others are experiencing the same problem.

---

### Post by Le canard on 2009-11-05
I'm having the exact same problem. Everything was fine with Jaunty, now my computer freezes after the screensaver is up for some time.

---

### Post by Le canard on 2009-11-08
I "fixed" the problem. I changed the screensaver to blank screen (I was previously using the fiberlamp one) and now it doesn't freezes any more.

---

### Post by Edward The Bonobo on 2009-11-08
Same problem, and only with the Feedback screensaver.

***However***...I can't use the Screensaver dialog box to de-select Feedback.  It freezes as soon as I bring up the dialog box with Feedback selected.

What's the Terminal command for setting a screensaver?  (with an example of a screesave name, please.)

---

### Post by Edward The Bonobo on 2009-11-10
BUMP.

Sorry - this is poor netiquette.  I'm only doing it because I think this has a simple solution: Open Terminal and use CL to set the screensaver to something other than Fedback.

Can somebody tell me what command I need?

---

### Post by karlkuehn on 2009-11-10
> **Edward The Bonobo said:**
> BUMP.

Sorry - this is poor netiquette...

Can somebody tell me what command I need?

No worries, man. This needs to be bumped...a lot. I'm having the same issue with the screensaver. I would love to have a quick command-line fix to change the screensaver back to 'blank screen'. As it stands, every time I go to the GUI screensaver window, the OS hangs. 

It was on 'blank screen' since forever. After updating 9.04 to Karmic (Jaunty had upgraded seamlessly last spring from Intrepid, and that from Hardy, which I run as LTS server on 4 blades and boxes at work right now, after waving goodbye to Debian proper), everything was running fine (mostly...synergy gave me a couple fits), but then I was like..."hey...I wonder what screensavers they have..."

Whoops.

Let me say this: My transition to Linux for day to day operation has been joyful and with extreme prejudice. Canonical, in my opinion, is poised to slaughter Microsoft. If they keep up the good work, it will take time, but there are more and more of us every day, and the ranks are swelling with people who have no prior Linux experience. I currently have 4 machines running Ubuntu, 3 Jaunty's and a Karmic, all of which have become major tools in my box, at work, at home, and at our datacenter. I'm running dual 22" screens, 32 and 64 bits, development boxes and media machines.

I actually ran Windows-free in my home office for months prior to the upgrade. I spent two years as a dev at Microsoft and worked on the XP team, so Vista has been a nightmare. Ubuntu has changed my life and career. I bought the hat, the keyring, the stickers, I've been spamming like a fool singing praises and getting people moving in the correct direction. I have those stickers on my RC airplane, my car, my computer towers, my keyboards, one on my Casio Boulder (you wouldn't believe how many people ask me how I got Linux on my cell phone...heh). I'm sold on Canonical products and will continue to support them in their endeavors.

Last week I built a monstrous Windows 7 machine that I'm using at home with synergy to both XP and Jaunty, all three machines running over/under dual 22" monitors...yeah, I'm living the dream! :D So far, I'm sorta sideways-whelmed with win7. It does indeed, suck less than Vista, but I won't be writing any stunning reviews any time soon. My XP Pro machine has still remained my Redmond workhorse. We'll see what functionality the next Win7 'Security Updates' *snort* include for the new Far-East stepchild. 

That being said: I didn't intend for this new win machine to become my main, but it has, due to the Karmic hang problem. Somewhere, somebody screwed up big with Karmic. I gconf-edit'd my way to no screensaver on session timeout, but I'm still seeing random hangs and crashes in Karmic. I was actually working on it today when it just froze, and twice. (Both times while rdesktopped to a Windows server, if that's any help.)

Now, this great, steady gnome box that has been slowly taking over some seriously core functionality for me is hanging severely, requiring the old "push...wait 7 seconds...pray...let the hard drive spin down...push...pray" several times a day. Not good. Thank God for ext3...

I made the mistake of, after two amazing Ubuntu OS upgrade experiences, assuming that the third would go flawlessly. Now I have an almost unusable box that I can't downgrade without a wipe (yeah, this was the first one that I didn't ghost before the upgrade...), and I can't use it for critical jobs.

Please, someone do something with this. It's not a huge deal for me to nuke and pave the box again, but we're in the middle of a pretty big launch cycle, and this has crippled me.

Please don't let 9.04 become the Linux XP that we all end up having to downgrade to from a Karmic Vista over a silly screensaver issue. This kind of thing is one of the only paths to destruction for Canonical. No quick-patch and no graceful downgrade paradigm. If I set my mom up with this, it makes "Hi, I'm a PC" look like "...and I'm a MAC" to the non-sudo types...

I'd be happy to pay the $140 price that I paid for Win 7 pro if y'all can get this release nailed, even if it's only for 'support'. The hung machine still reboots faster than Windows, even running on a quad-core, 8-gig box. heh :P

I'd love to contribute, but I'm still a noob, so my fixes would have to be labeled "Security Update" before we sling them over the hedge. Gimme a couple years on the whole repo-contributor thing. :P

Karl

---

### Post by tenach on 2009-11-11
I am having the same issue with a computer I'm putting together for a friend to replace his old G3 Mac.  So far he is impressed with Ubuntu and Linux in general, and has claimed that he has been converted.  That is quite impressive considering he can't let his computer idle and go to screensaver.

This is how I made his computer somewhat usable for him, sans screensaver ability:

Go to System / Preferences / Startup Applications.  Scroll down to "Screensaver" and uncheck it.  I unchecked Bluetooth and some others he wouldn't need with this old machine too (no use in running stuff that isn't needed).  

He can now use his computer just fine for what he does.  This does not satisfy me however.  I am looking into how to manually change the screensaver to blank and see how to improve video performance.

---

### Post by Edward The Bonobo on 2009-11-14
Well...turning off the screensaver is one way of fixing a crappy screensaver.  All the same...noting the previous comment about not wanting to have to revert to 9.04...

BUMP.

---

### Post by tenach on 2009-11-14
It is a good temporary fix until the underlying issue is resolved.

---

### Post by karlkuehn on 2009-11-30
FYI, never saw a fix for this, so I ended up reformatting and going back to 9.04.

Solid as a rock again. ;)

I think, in the future I'll just let this machine alone and build another one to dog food the new versions.

---

### Post by dazza5000 on 2009-12-05
having this same problem after upgrade.

When I try to use computer after screensaver has been running it locks up and I have to hard restart. I am on dell inspiron 640m with intel graphics.

---

### Post by DeathRabbit on 2009-12-22
I can also confirm this issue. After a protracted period of running the screensaver in Karmic, it will eventually freeze and I have REISUB the thing in order to get it to reboot. Really annoying b/c Ubuntu has so many screensavers and flashy stuff like that is really key to attracting new users. I really hope Canonical knuckles down on compiz and gnome-screensaver for Lucid; these two only kinda work in Karmic from what I've seen.

---

### Post by paul_da_programmer on 2010-01-14
Just want to keep this thread alive as well. I have a fresh install of 9.10 on a new dell i7 laptop and I have the same issue. I'm running the 64 bit version of Karmic.

Blank SS -> no worries
Matrix GL screensaver -> locks up all of the time. I didn't exhaustively test all of the screensavers, but it seems unnecessary

Just a general statement. 9.10 in my first months of usage seems alot less stable than 9.04 was. I've lived with 9.04 as my main OS on my old computer for years and never had to investigate the RSEIUB magic keys (even though I'm a veteran Linix users)

I hope Ubuntu isn't getting cocky and taking a page from Microblast :( I agree with the poster - I've converted many users by bringing in a laptop with Compiz and showing the 'trinkets' and some apps - but if it crashes every day might was well stay with Windows

---

### Post by sacredfaith on 2010-01-14
Just thought I'd join the ranks and collective sigh of slight frustration. Same problem on my machine with the "skyrocket" screensaver. Switched to "blank screen" and the problem resolved itself. 

I was noticing that if I hovered my mouse approximately where the text box of the login screen (when skyrocket is active) I could click and "blindly" input my password -> this worked quite a few times, I just had to time the first click (to wake it), and then the second click (to select the text box), and then type in my password...and pray. 

So it's like the box is 'there', just not displayed. Might help zero in on the issue. 

-sf

---

### Post by oreomike on 2010-01-14
Have any of you with the 9.10 screensaver freeze problem tried the new 10.04 development branch?  I'm thinking I may this weekend.  Unfortunately for me, my freeze happens within 30 seconds of gnome finishing its boot, and this is a brand new computer (Core i5-661 and DH55TC)

My problem is I've also heard of problems with Intel's ACPI, and the Linksys WMP110 Wireless card.  So until I figure this all out, I'm frustrated.

---

### Post by j22 on 2010-01-19
I am also having the same problem along with other problems.  Started dual booting in December with WinXP.  After a month of bad experience with Ubuntu 9.10 (my first Linux experience) I don't think Linux is on Microsoft's radar as a competitor.  I am terribly disappointed in Ubuntu.  But I digress --

Building on Tenach above, I found that this worked for me -- I unchecked Screensaver in Startup Applications.  Rebooted then started Screensaver again under System>Preferences>Screensaver.  Blank Screen was already highlighted but I clicked on it anyway, then closed Screensaver.  Went back to Startup Applications and checked Screensaver. Rebooted again.   Screensaver functionality is now working again with the blank screen and thus far no hangs/freezes.

Hope this helps others.

---

### Post by Trapper on 2010-05-15
Well, here we are with 10.04 now and I am having the same screensaver issues addressed in this thread. I guess we have not progressed. Changing the screensaver to a blank screen seems to eliminate the problem but it also eliminates usage of an eye candy screensaver so I consider this a workaround rather than a fix.

It's disappointing that these screensaver issues continue release after release. It makes a reasonable OS look and act like junk. It's so sad that Ubuntu has taken on Windows 95/98/ME likeness in regards to screen locks.

---

