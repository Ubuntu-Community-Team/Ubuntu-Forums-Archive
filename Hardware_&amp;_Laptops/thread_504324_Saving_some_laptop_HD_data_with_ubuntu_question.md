---
title: "Saving some laptop HD data with ubuntu question"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by intransit on 2007-07-19
Hi All,

So i've recently started to mess around with ubuntu, and I downloaded 7.04 and Virtual PC 2007 and with a bit of messing around have got it installed and working on a virtual pc. This is on my desktop computer.

Now, recently i've been having trouble with my laptops HD (long story short, my laptop is using XP and somethings corrupted so that I can't boot windows in any mode -safe/normal/last good settings/etc ... haven't tried going into recovery console yet. im pretty sure some of the hd has become corrupt or soemthing so my main concern is getting some files back, then i'll reformat and reinstall OS & this time ubuntu too.. etc)

Basically my question is, as someone posted in this thread I made (url down page a bit) suggesting: knoppix live cd, to boot with the knoppix cd start it in that like live/test mode before its installed and copy the files to a thumbdrive. Would this work? And more specifically, would I be able to do this with my ubuntu desktop 7.04? It's just an .iso sitting on my desktop but i could burn it and use it on the laptop

my last question (and im sorry for this involving windows!! feel free to ignore this part!) is would this likely be a better method to go for or should i go for what the guy posted in the thread i made at techguy, i.e:



```
Boot into recovery console . At the prompt type :

attrib -r -s -h c:\boot.ini
del c:\boot.ini
bootcfg /rebuild
-at the first prompt press "y" enter
-at the second prompt type what you want to name your windows installation (anything you want)
-at the third prompt type /fastdetect
chkdsk /r
fixboot
-at the prompt press y
fixmbr
-at the prompt press y
```











I've got the specifics of my HD posten in another thread at [http://forums.techguy.org/windows-nt-2000-xp/596801-slaps-head-laptop-booting-harddrive.html](http://forums.techguy.org/windows-nt-2000-xp/596801-slaps-head-laptop-booting-harddrive.html) explaining exactly). Just thought I better post it here incase that needs registration to see the post:

-------------------------------------------
**ORIGINAL THREAD**
--
intransit  intransit is online now
Junior Member
		
Posts: 10
Join Date: Mar 2007
Experience: Advanced
Hi All, yes i'm sure you know the horrible feeling!

I've always worried about this happening to me and its finally happened. The hard drive on my laptop appears to have slowly corrupted, and now i'm in the unfortunate position of not being unable to boot.

Firstly i'll just explain the background: I noticed one day that after waking my laptop up from hibernation that it was running a bit stranger than before; a bit slower and laggier - this was very noticeable because I just upgraded from 512 to 1024 ram and was loving the increased performance after this change and it seemed like it was running similarly to under the old 512. More alarmingly, random mp3s I tried playing which were stored all over the HD played very poorly; would cut out and fizzle and make slight random static noises, as if the files had become/were corrupt.

So I became quite worried, updated the virus scanners pattern file, virus scanned, and rebooted. On reboot I was worried again when it appeared that it was taking a considerable bit more time to boot (especially the colorful loading screen were windows loads before u click the logon account). But it booted, so I was relieved, checked a heap of files and mp3s that had been playing/acting funnily before but were now playing and opening fine. At this point I stopped worrying (stupidly...lol) and left it.

The next day I came back to the laptop which was now in hibernation, and woke it out of hibernation, and it was behaving slowly again, but files opened fine and mp3s were playing fine still. After a bit of web browsing, something crashed, i think firefox and the computer locked up for ages and couldn't seem to get control without restarting. So I restarted: it returned to the colorful loading screen and loaded for like 7 minutes with nothign happening before I decided to restart again. At this point I was given those options to how you want to boot. Select the one "use last good configuration" or however it goes, this went to colorful loading screen, again took a considerable more time than usual, but got in and windows loaded. Once windows loaded up I got some diagnostic web site pop up about a possible harddisk error, but said if this was the first time i got the message there was probably nothing wrong.

This is the point where i really starting panicking and started trying to back up really important things, (i have backed up 2.5 weeks before this, so luckily I haven't lost too much, but i know there is about a CD's worth of things I would really like to try to get back), but in doing so, again something crashed and I couldn't regain control by trying to kill processes and had no vision of what was happening, so restarted again.

Now i'm in the nasty position of being unable to boot into any of the options given
e.g Safe mode
Safe mode w networking
s m w/ commnd prompt
start xp normally
last good config

the 3 safemode's all stop when loading something in i'm pretty sure Drivers/Mup.sys and hang there.

start xp normally --> gets to that colorful xp loading screen, loads for 2 or so minutes, cuts to blue screen for about half a second (haven't been able to read it properly yet it comes up so quickly) then reboots itself and continues cycle to chose how u want to load windows.

last good config --> does the same but a little quicker to get to blue screen and reboot.

-------------------

So yeah, i'm in a bit of a nasty spot and not really sure how I can go forward with this. All i've done so far is go into BIOS, and do that disk self check thing you can select, which fails in 40-50 seconds each time i ran it (3 or 4 times)

Is there any conceivable chance I have of getting my files back?? or any files at all?? If I could only get small sized files that would still be helpful as there are a number of uni word documents that wouldn't be big that'd be really nice to get back.

Just bought one of those external hd thingies, is there any chance I could maybe hook the drive up to that to try to get in from my desktop comp and get/save what I can on that comp? Or perhaps the laptop hd won't fit...

And just lastly, ignoring the data, how can i be sure or more confident that if i reformat the drive and clean install windows and everything on the laptop, that the drive won't do it again (or will have a tendency/more likeliness to do so?)
I guess the question is, is there any way I can trust that it won't happen over and over? As in: happen because there is a flaw in the hardware, rather than happen because of some crazy internal problem? (if that makes sense)
---------


**posted by devil_himself:**
---
Boot into recovery console . At the prompt type :

attrib -r -s -h c:\boot.ini
del c:\boot.ini
bootcfg /rebuild
-at the first prompt press "y" enter
-at the second prompt type what you want to name your windows installation (anything you want)
-at the third prompt type /fastdetect
chkdsk /r
fixboot
-at the prompt press y
fixmbr
-at the prompt press y
---------



**posted by me:**
----
just thought i better post my laptop stats in case

Compaq Presario V2000

AMD Turion 64 1.8 ghz
1 gig ram
80 gig hd
ATI radeon xpress 200m g card

also I realized I didn't mention, the reality of the situation is that the most essential files to get back would be the uni word documents etc that would mostly be under 1 mb, and I estimate i probably made about maybe 10-15 doc's since the last back up, so the things i most want to save are actually the smallest.
-------

**posted by me:**
----
and boot into recovery console with the XP install disk (or whatever the one that came with the laptop was) yeah?
--------


**posted by devil himself:**
---
Try it MIght solve your problem
-------


**posted by simon cleaver:**
---
SimonCleaver  SimonCleaver is offline
Junior Member
		
Posts: 1
Join Date: Jul 2007
Experience: Intermediate
Hi there,
amazing, yesterday i was asked to look at a packard bell laptop with exactly the same problem.

_**To get the important data off first, I used a livecd of Knoppix to get the laptop working, then copied all data and photos to a usb flashdrive.**_ Hope that helps the original poster.

As for the fix above, I cant get to a prompt. When the laptop starts, the cd spins but never loads, it always reverts back to the "choose an option, safe, last good, etc"
I know that it will start from cd, because I can run Knoppix livecd.
Any ideas why the machine is not running xp cd.
-----------

---

### Post by bdtgp on 2007-07-19
you can use the ubuntu live cd if you have one.  if youre going to install ubuntu you may as well.  it should automount your hard drive and let you access the files.  if you dont have an ubuntu live cd you can go get a copy of the july Linux Magazine and there is one in there.

---

### Post by intransit on 2007-07-19
Doesn't the version I have work like a Live CD?

It let me start ubuntu before I actually installed in Virtual PC... and access things like firefox

---

### Post by intransit on 2007-07-20
???

---

### Post by hessiess on 2007-07-20
yes thats the live cd if you can boot it, then run off the disk.

---

