---
title: "The reason Via C3-2 1GHz Nehemiahs dont work in Ubuntu 8.04+"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by NewJerseyNinja on 2009-03-23
Hello All,

I have spent the past 2 weeks trying to get Ubuntu 8.04,  8.10, 9.04A6 working on an all-in-one integrated motherboard+cpu with limited success.

Keep in mind that 7.10 works just fine.

The Trouble: 

[1] Ubuntu 8.04 & 8.10 Live CDs both freeze up, completely locking up the computer--not even the CAPS lock key responds.  This lock up ONLY OCCURS while using X--it does not occur if I bootup to a root terminal.


[2] Upgrading from 7.10 to 8.04 does exactly the same freeze up.


[3] 9.04A6 DOES WORK, no freezing etc.  However, if I run the upgrade manager or use Synaptic to perform a MARK ALL UPGRADES, I get stuck freezing up again.

After pouring through countless mailing lists it appeared at first that maybe it was the CMOV related instruction problems, however my CPU DOES HAVE the CMOV instruction.


My thoughts on this: The lockup is specifically related to the CLE266 video chip: VT8623 and its driver, in my case it was OpenChrome which I think came with 9.04A6.  I noticed that video playback was choppy, so I updated the driver to the lateast OpenChrome and after it installed, used dkpg-reconfigure xserver-xorg.  

Video playback was still choppy on any program other than Mplayer, so I thought, what the hell, I'll upgrade the 346 pending packages waiting to be upgraded.  This brought the lockup issues back.



Anyway, its a bug and a nasty one, the LiveCD doesn't even run and its video driver related.

---

### Post by NewJerseyNinja on 2009-04-13
After spending MANY hours on this I have narrowed my troubles down to the following package in 9.04A6:

initscripts



If I do not upgrade this package after installing my 9.04A6 liveCD, then I can upgrade every other package and have it run properly.

As long as initscripts is kept to its original 9.04A6 LiveCD version, my system will boot into Gnome and work properly, not locking up.


Not being a programmer, I have no idea what was changed between these revs and why initscripts causes a hard lockup on my system.


So to note:

7.10 works great

8.04 Locks up using the liveCD, after Gnome has started.

8.10 Locks up using the liveCD, after Gnome has started.

9.04A6: Works great (except xserver-xorg is missing display resolutions which get fixed when the openchrome package gets upgraded)

9.04A6: When initscripts package gets upgraded to latest, this causes the system to lock up after Gnome has started---The system DOES NOT lock up if I boot into a root terminal, but will lockup shortly after Gnome starts, every single time.

---

### Post by NewJerseyNinja on 2009-04-15
Any ideas on what changed in the initscripts package to make it lockup on Via C3-2 's?

---

### Post by lioncub33 on 2009-06-01
FIXED: OPENCHROME VIA & MOBILE BROADBAND ALL WORKING NICELY NOW :-)

After weeks of trial & error, I finally got my VIA C3 / CLE266 laptop (Hi-Tech Green320) past the Ubuntu 9.04 "Jaunty Jackalope" install GDM/KDM/Xfce/X.Org crash - by doing a "vesa" install from the Xubuntu Alternate CD & then updating the OpenChrome VIA driver from the ensuing command prompt, as per:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/367442](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/367442)
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Reason for the upgrade, was to get my shiny new Vodafone Top-Up & Go Mobile Broadband USB GSM Modem - Huawei K3565 (also referred to as an E160X, apparently..) - to work under Linux:

[http://ubuntuforums.org/showthread.php?p=7159131](http://ubuntuforums.org/showthread.php?p=7159131)

Once I was actually up & running with Xubuntu 9.04, the Mobile Broadband setup wizard ran automatically when the dongle was plugged in & connected it all up fine, no problem (OK, after another switch-off or two..) WITHOUT ANY CONSOLE/CONFIG-FILE-EDITING STUFF!! :-D

Well done again, all you Ubuntu & OpenChrome guys! :-D

Wasn't immediately obvious from the Vodafone website / documentation though, how to £top-up the account.. :-(

But eventually found out (not from Vodafone, of course..) how to link the GSM SIM to an online Vodafone account:

[http://ubuntuforums.org/showthread.php?t=1061368](http://ubuntuforums.org/showthread.php?t=1061368) :-)

But not before I'd wasted loads of time (& crashed Firefox - had to restore its settings from a (fortuitously made) backup copy of ~/.mozilla/firefox/..), trying & failing to get various versions of Betavine's Vodafone Mobile Connect (up to & including the latest .deb downloads) to work. :-(

I'd previously thought that Betavine's contribution would be necessary, in order to obtain the privilege of topping-up the account with fivers. So I've been pleased enough, to discover that the above has made that bit of "not officially supported" brokenware entirely redundant :-)

Looks like Jaunty would plug & play the other Mobile Broadband offerings (e.g. T-Mobile, O2, etc.) just as readily, too.. suppose if Vodafone (or any of them) had smelt the coffee & bothered to officially support Linux, I might feel inclined to show them a bit of brand loyalty, eh?

Anyway.

:-D happy now

---

